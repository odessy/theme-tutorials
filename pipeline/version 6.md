[comment]: <> (https://docs.github.com/en/github/writing-on-github/getting-started-with-writing-and-formatting-on-github/basic-writing-and-formatting-syntax)

# Pipeline theme version 6

## Simple CSS changes

To add any CSS code in this list follow these steps:
[Where to add css](https://groupthought-themes.gitbook.io/tutorials/)

1. [Solid Color for Add to cart button](#1)
2. [Hide Add to cart button price](#2)
3. [Reduce padding above and below sections](#3)
4. [Hide navigation cart link](#4)
5. [Solid background-color for header when scrolling](#5)
6. [Overriding the theme font](#6)
7. [Change color of size chart link](#7)
8. [Sticky currency and language selectors](#8)

<!--
## Advanced Changes
#### May require both CSS and Javascript changes
1. [Show cart drawer when product added to cart - for pipeline 6.1 and above](#21)
-->

### 1. Solid Color for Add to cart button <a name="1"></a>

This allows the add to cart button to use the primary accent color

```css
/* CSS - change Add to Cart button color */
.product__submit__buttons .btn--add-to-cart {
  background-color: var(---color-primary);
  border: 1px solid var(---color-primary);
  color: var(---color-primary-opposite);
}
.product__submit__buttons .btn--add-to-cart:hover, .product__submit__buttons .btn--add-to-cart:focus {
  background-color: var(---color-primary-hover);
  border: 1px solid var(---color-primary-hover);
  color: var(---color-primary-opposite);
}
/* Change loading and complete state colors */
.btn-state-loading .svg-loader circle,
.btn-state-loading .svg-loader circle~circle{
  stroke: var(---color-primary-opposite);
}
.btn-state-complete{
    border-left: 2px solid var(---color-primary-opposite);
    border-bottom: 2px solid var(---color-primary-opposite);  
}
/* - end - */
```

#### Example when this is used

![image](https://user-images.githubusercontent.com/1010232/142236205-beccfc66-05d4-4f86-8c41-fcdfdfda6cc1.png)


### 2. Hide Add to cart button price <a name="2"></a>

```css
/* CSS - hide Add to Cart button price */
.btn--add-to-cart .btn-state-ready span:not([data-add-to-cart-text]){ 
  display:none; 
}
/* end */
```

#### Example when this is used
![image](https://user-images.githubusercontent.com/1010232/142242186-f46e55a5-ba3a-4bd4-b0cd-4b5b44cbf135.png)


### 3. Reduce padding above and below sections <a name="3"></a>
You can adjust the px values in the code to further reduce the padding-top and padding-bottom values
```css
/* CSS - reduce section padding */
.homepage-collection-tabs,
.homepage-blog, .homepage-collection, .homepage-columns, 
.homepage-icons, .homepage-newsletter, .homepage-product {
    padding-top: 66px;
    padding-bottom: 66px;
}
.homepage-collection-grid, 
.section-recent .recent__container__inner:not(.is-hidden), 
.section-related {
    padding-top: 66px;
    padding-bottom: 34px;
}
.collection-tabs{
  position: relative;
}
/* end */
```
### 4. Hide navigation cart link <a name="4"></a>
```css
/* CSS - hide navigation cart link */
.header__desktop__button .navlink--cart,
.header__mobile__button[data-drawer-toggle="drawer-cart"]{
  display: none;
}
/* end */
```

#### Example when this is used
![image](https://user-images.githubusercontent.com/1010232/142244474-aaf98a1a-9c61-4b46-be78-1f30b577b301.png)

### 5. Solid background-color for header when scrolling <a name="5"></a>
```css
/* CSS - solid background-color header */
.js__header__stuck .theme__header:after {
    opacity: 1 !important;
}
/* end */
```

### 6. Overriding the theme font <a name="6"></a>

#### a. Uploading the custom font

Use the steps in this guide to upload the fonts to the theme assets folder.
[Fonts: Adding a custom downloaded font to your theme](https://help.groupthought.com/article/274-fonts-add-gotham-bold-to-your-theme)

The code to import the font can be added to the end of your css-variables.liquid file. Add it before the last line ```{% endstyle %}```

![image](https://user-images.githubusercontent.com/1010232/142245929-01f7b2d3-40b5-4b46-b39e-6899faf54b1f.png)

The ```asset_url``` allows the theme to find the font files in the assets folder. This is Shopify-specific code. Adding the code ensures the browser downloads the correct files instead of returning a 404 not fount.

This needs the name of the file exactly like it is in your assets folder and then the code ```| asset_url``` generate the correct path to your file. 

Example of that code. This is used for the URL property for font-face import code.

```liquid
{{ "Gotham-Bold.eot" | asset_url }}
```

#### b. Overriding the theme font

The variables with "--font-stack-" can be updated for the body, heading, and accent. For more specific elements different CSS code would be needed.

```css
:root {
  ---font-stack-body: 'Gotham', sans-serif;
  ---font-stack-heading:  'Gotham', sans-serif;
  ---font-stack-accent:  'Gotham', sans-serif;
}
```

### 7. Change color of size chart link <a name="7"></a>

You can update the background-color and color properties with any valid HEX color code.
To find additional HEX color codes, visit:  https://colorhunt.co

```css
/* CSS - change color of size chart link */
.product__info__link--inline,
.product__info__link{
  background-color: #d02e2e; 
  color: #ffffff;
}
/* end */
```

For the link hover color

```css
/* CSS - change hover color of size chart link */
.product__info__link--inline:hover,
.product__info__link:hover{
  background-color: #ffffff; 
  color: #d02e2e;
}
/* end */
```

#### Example when this is used
![image](https://user-images.githubusercontent.com/1010232/142249538-3dee8a4a-afde-4dea-9723-fb2e522a6b0a.png)

### 8. Sticky currency and language selectors <a name="8"></a>

Use this to apply the change to both desktop and mobile

```css
/* CSS - Sticky currency and language selectors */
#localization-form-footer{
  position: fixed;
  z-index: 1000;
  bottom: 0px;
  left: 15px;
}
#localization-form-footer .popout-list,
#localization-form-footer .popout__toggle{
  background: #ffffff;
  color: #000;
}
#localization-form-footer .popout__toggle{
  border: 1px solid #f0f0f0;
}
#localization-form-footer .popout-list__item a{
  color: #000;
}
/* end */
```

Use this to apply the change only to desktop

```css
/* CSS - Sticky currency and language selectors desktop */
@media only screen and (min-width: 480px){ 
  #localization-form-footer{
    position: fixed;
    z-index: 1000;
    bottom: 0px;
    left: 15px;
  }
  #localization-form-footer .popout-list,
  #localization-form-footer .popout__toggle{
    background: #ffffff;
    color: #000;
  }
  #localization-form-footer .popout__toggle{
    border: 1px solid #f0f0f0;
  }
  #localization-form-footer .popout-list__item a{
    color: #000;
  }
}
/* end */
```

#### Example when this is used
![image](https://user-images.githubusercontent.com/1010232/142250897-0b113da9-1cbe-419f-a27f-5a728aeab0c9.png)


<!--
### Show cart drawer when product added to cart <a name="21"></a>

```js
/* Javascript - Hide the product add popdown */
document.addEventListener('theme:cart:popdown', (e) => {
  document.addEventListener('theme:cart:change', (e) => {
    document.querySelector('[data-drawer="drawer-cart"]').dispatchEvent(
      new CustomEvent('theme:drawer:open', {
        bubbles: false,
      })
    );
  });
});
/* end */
```

```css
/* CSS - Hide the product add popdown */
.product-add-popdown{
  display: none !important;
}
/* end */
```
-->

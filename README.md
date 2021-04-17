# SASS_responsive

## Summary
responsive website using html, css, and javascript.

the purpose of the website is getting familiar with sass compiler and its function and syntax.

it is basically similar to javascript with css, it auto compiles all scss files to css.

## Remarks

declare all the variables, basic setting, and functions(mixin) in _config.scss file
```

// variable need $ tag
$primary-color: #272727;
$secondary-color: #ff652f;

// functions, mixin, and other conditional statements (all the js functions) need @ tag
@mixin transition-ease {
  transition: all 0.5s ease-in-out;
}

@function set-text-color($color) {
  @if (lightness($color) > 40%) {
    @return #000;
  } @else {
    @return #fff;
  }
}

@mixin media-md {
  @media screen and (min-width: 768px) {
    @content;
  }
}

@mixin media-lg {
  @media screen and (min-width: 1024px) {
    @content;
  }
}

@mixin media-xl {
  @media screen and (min-width: 1600px) {
    @content;
  }
}
```



```
// in main.scss, you need to import all other scss file without _ in front of name and extension 
@import "config";
@import "home";
@import "menu";
@import "about";
@import "projects";
@import "contact";
@import "responsive";
```


more effiecnt for responsive web setting

```
@include media-md {
  .menu-btn {
    visibility: hidden;
  }

  .nav {
    visibility: visible;

    .menu-nav {
      display: block;
      transform: translateY(0);
      height: 100%;
      background: transparent;
      text-align: right;

      &__item {
        display: inline;
        padding-right: 1.5rem;
      }

      &__link {
        font-size: 1.5rem;
      }
    }
  }

  .about__bio {
    font-size: 1.5rem;
  }

  .projects {
    &__bio_image {
      height: 40vh;
    }

    &__items {
      grid-template-columns: repeat(2, 1fr);
    }

    .secondary-text {
      font-size: 3rem;
    }
  }

  .contact__list {
    grid-template-columns: repeat(2, 1fr);
  }
}

@include media-lg {
  .projects {
    &__items {
      grid-template-columns: repeat(3, 1fr);
    }
  }

  .contact__list {
    grid-template-columns: repeat(3, 1fr);
  }
}

@include media-xl {
  .projects__bio-image {
    height: 50vh;
  }
}

```

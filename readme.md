#Documentation

## Convention BEM

* B -> Block
* E -> Element
* M -> Modifier

```html
<!-- mainList = Block -->
<ul class="mainList mainList--xmas">
    <!--_item = Element-->
    <li class="mainList_item">
        <!--i= _itemLink = Element-->
        <a class="mainList_item_link mainList_itemLink--isActive"href="/home">Accueil</a>
    </li>   

    <!--_item = Element-->
    <li class="mainList_item">
        <!--i= _itemLink = Element-->
        <a class="mainList_item_link"href="/about">About</a>
    </li>  

    <!--_item = Element-->
    <li class="mainList_item">
        <!--i= _itemLink = Element-->
        <a class="mainList_item_link"href="/works">Works</a>
    </li>   
</ul>
```

```css

.mainList {
    display : flex;
    justify_content: space-between;
    &--xmas{
        background : green;
    }
    &_item {
        list-style: none;
    }
    &itemLink {
        color:red;
        &--isActive {
            color : white;
        }
    }
}
```

Exemple en CSS du rendu :

```css
.mainList {

}

.mainList--xmas{

}

.mainList_item {

}

.mainList_itemLink {

}

.mainList_itemLink--isActive {

}
```

## Pseudo attributs

Les pseudo attributs 'before' et 'after' permettent de créer des noeuds HTML en CSS.
Ils sont essentiellement utilisés pour ajouter des ornements, des décorations ... On
peut bien entendu faire des animations avec, les positionner par rapport à leur
parent (relative/absolute). Ils doivent obligatoirement avoir un 'content: '' '
afin de s'afficher.


```html
<section class="cover>
    <h1 class="cover_mainTitle> Présentation des pseudo-attributs</h1>
</section>
```

```css
.cover {
    background: #FDFDFD;
    padding: 20px;
    &_mainTitle {
        text-align: center;
        font-size: 24px;
        color: green;
        position: relative;
        &::before,
        &::after {
            position : absolute;
            content: '';
            width: 50px;
            height: 50px;
            background : green;
            top: 0;
        }
        &::before {
            left:0;
        }
        &::after {

            right:0;
        }
    }
}
```

## REM, EM, %, VW Sizing

## %

## EM

Relative à la taille de son parent direct.
Utile pour les padding et margin.

```css
.cover {
    font-size : 16px;
    &_mainTitle {
        /* 1em = 16px / 0.8em = 80% de 16px */
        font-size: 0.8em;
    }
}
```

## REM

* Le REM est basé sur la taille de la racine (soit la balise <html>) qui, par
défaut à une valeur de 16px. Afin d'éviter tout calcul, il est nécessaire de l'écraser
en donnant une base de 10px soit 62.5%.
* Le REM est intéressant à utiliser si les media-queries employées sont en rem également.
Cela vous permettra de garder des proportions égales lorsqu'on va redimensionner la page.
* Ses proportions seront également gardées quand l'utilisateur zoomera dans votre page.

```css
html {
    font-size : 62.5%; //10px
}
.mainTitle {
    font-size : 1.6rem; // 16px
    width: 32rem; //320px;
}

```

## VW /VH

Unités relatives à la taille de votre écran (peu importe le device)
Attention au VH et à son contenu. 100vh = 100vh quoi qu'il arrive.
VW très utile pour les interfaces fluides.

## Liens utiles

https://caniuse.com/
https://github.com/h5bp/Front-end-Developer-Interview-Questions
http://cssnext.io/

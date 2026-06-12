---
title: "Change gtk3 css theme options"
date: 2012-06-07
forum: Art &amp; Design
---

### Post by redman5087 on 2012-06-07
I downloaded a theme from gnome-look.org and I want to change the panel background. I don't wanne do this by the panel properties but by the gnome 3 classic theme, the css files.

In the orignal file I have this: it uses gtk gradients

```

PanelToplevel {
    padding: 0;
    background-image: -gtk-gradient (linear, left top, left bottom,
                                     from (shade (@dark_bg_color, 1.15)),
                                     to (shade (@dark_bg_color, 0.95)));

    color: @dark_fg_color;
}

```

And I changed it to this: I want to use a PNG image file

```

    PanelToplevel {
    padding: 0;
    background-image: url("panel.png");

    color: @dark_fg_color;
}

```

This doesn't work

Appareantly "background-image: url("panel.png");" is not wright?

Can someone help me?

Kind regards,

Redman

---


---
title: "converting gtk2 theme to gtk3"
date: 2012-05-16
forum: Art &amp; Design
---

### Post by DoubleClicker on 2012-05-16
I created mown gtk2 theme a couple years ago,  I would like to convert it to gtk3.   I am having difficulty with  a couple of points:

My thine is designed to be vertically compact, I reduced the icon sizes to 16 pixels, reduced the puffing on the toolbars buttons and notebook.  ''I have not been able to figure out where to make these changes in gtk3 themes.  

I am using the equinox engine, in my theme, what would I use in it's places?

Is there a good tutorial on creating gtk3 themes? haven't been able to find one.

---

### Post by fallenshadow on 2012-05-18
I haven't seen any guide on creating a theme for Gtk3. As far as I can see its quite different to Gtk2 themes.

Years ago I was into making Gtk2 themes and I found the best way to learn was take a fairly normal (not heavily customised) theme and start to modify it. 

As you go along you will learn some things and find ways to make it how you want it to be. :)

---

### Post by LarsKongo on 2012-05-18
If you know CSS (which is used very much in web designing) it should be easy for you. If you don't know any CSS it can still be easy because CSS is very easy to learn. (GTK+ doesn't always use standard CSS properties though.)

The best way to get started is to get a GTK2 + GTK3 widget factory program. (I use one called [awf]("https://github.com/valr/awf").) Then edit the Adwaita theme or any other theme you can get your hands on.

As for Op's questions:
The unico engine should be able to do some of the things Equinox can do. (Except animations.)
For a more compact look try changing all padding to 0.
Also take a look at some of the global settings specified in the first lines in the gtk-widgets.css file.
```

* {
    eninge: unico;
    -GtkButton-inner-border: 3;
}
```
Changing -GtkButton-inner-border to 0 for example will make the buttons more compact.

---

### Post by satya164 on 2012-06-23
I have written a small tutorial here [http://funsurf-blog.blogspot.com/2012/06/when-you-make-gtk3-theme.html](http://funsurf-blog.blogspot.com/2012/06/when-you-make-gtk3-theme.html)

---

### Post by Dry Lips on 2012-07-06
**@satya164**; [B]@LarsKongo

[/B]Interesting stuff here... I've been looking for something like this, so thanks to both of you. And I also hope this is enough information to get the OP started...

---


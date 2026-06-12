---
title: "menu themes..?"
date: 2007-08-31
forum: Art &amp; Design
---

### Post by jeramiahx on 2007-08-31
is there a way to change the color of the menus? just to clear things up, the one after you press the launch button?

---

### Post by wireddad on 2007-09-01
Are you talking about, right clicking on the panel>Properties>Background Tab?

---

### Post by alex_o on 2009-04-05
is there a location where you can atleast go to to find a .css or similar with a html notation colour i can change?

:guitar:

---

### Post by Ben Crisford on 2009-04-05
> **alex_o said:**
> is there a location where you can atleast go to to find a .css or similar with a html notation colour i can change?

:guitar:

For the panels?

Why bother with all that?

Simply right click and goto properties, there is a background tab, if you choose "use solid colour" you can change the hex and the colour and even the transparency.

---

### Post by s.fox on 2009-04-05
[This]("http://www.gnome-look.org/content/show.php/Color+Verona+Panels?content=80020") may be of some interest to you.

---

### Post by alex_o on 2009-07-06
> **Ben Crisford said:**
> For the panels?

Why bother with all that?

Simply right click and goto properties, there is a background tab, if you choose "use solid colour" you can change the hex and the colour and even the transparency.

im talking about the menu... :lolflag: you know with the applications in it ](*,)

---

### Post by Dragonbite on 2009-07-06
> **jeramiahx said:**
> is there a way to change the color of the menus? just to clear things up, the one after you press the launch button?

Are you talking about the main menu section (Applications/Places/System) that when you click it drops down the menu or category choices then when you hover over one it opens the list of applications under that category?

For example, this section?
[[IMG]http://img12.imageshack.us/img12/6048/ubuntumenu.th.jpg[/IMG]](http://img12.imageshack.us/i/ubuntumenu.jpg/)

To change the color for a section (like Office=Blue, Internet=Green, Graphics=Yellow, etc.)?

---

### Post by alex_o on 2010-01-01
> **Dragonbite said:**
> Are you talking about the main menu section (Applications/Places/System) that when you click it drops down the menu or category choices then when you hover over one it opens the list of applications under that category?

For example, this section?
[[IMG]http://img12.imageshack.us/img12/6048/ubuntumenu.th.jpg[/IMG]](http://img12.imageshack.us/i/ubuntumenu.jpg/)

To change the color for a section (like Office=Blue, Internet=Green, Graphics=Yellow, etc.)?

no i want to make it so the menu is a different style/colour itself i know you can do this with system > preferences > appearence but that will change the windows etc. :confused:

---

### Post by Exodist on 2010-01-01
> **alex_o said:**
> no i want to make it so the menu is a different style/colour itself i know you can do this with system > preferences > appearence but that will change the windows etc. :confused:
Has to be hard coded from the theme. But yes you can change just the menus.
 
```
    ############################# DROP DOWN MENUS #################################


style "pixmap-menu"
{


xthickness = 2
ythickness = 2

bg[NORMAL] = "#000000" #This adjust the shadow under the menu text for inactive text.

bg_pixmap[NORMAL] = "/menu/menu-bg.png"


engine "pixmap"
{

      image
      {
            function = BOX
            recolorable = TRUE
            detail = "menu"
            file = "/menu/menu.png"
            border = {1, 1, 1, 1} 
            stretch = TRUE
      }
}
}


###############################################################################




    class "GtkMenu"               style "pixmap-menu"

   
  
```


But there is alot more options then just that code to make it work.

Download my theme Gnomelegacy, I annotate what goes where you can customize and make your own.
[http://www.gnome-look.org/content/show.php/Gnome+Legacy?content=115142](http://www.gnome-look.org/content/show.php/Gnome+Legacy?content=115142)

Also please vote good if you like it, I have had some kids down voting my theme from 73% to 69% without stating why..



Hope this helps,
Exo

---


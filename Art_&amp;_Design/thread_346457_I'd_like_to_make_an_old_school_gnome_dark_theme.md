---
title: "I'd like to make an old school gnome dark theme"
date: 2007-01-25
forum: Art &amp; Design
---

### Post by BoyOfDestiny on 2007-01-25
Alright a little info. I find using white bg with black text to cause me headaches... I find dark on light provides excellent contrast, but I do find white text on a black background too much.

So in the "old days" black and green or amber was the way to go... I find it makes more sense... However, I'm no expert, all I know is newsprint is easy to read, cheap paperback spinach colored pages, and chalk boards...

Anyway, running feisty now, and gnome theme manager added a really primitive color tweaking, which doesn't work for all themes and doesn't seem to let you tweak essential things like blinking cursor color...

So I'm making a simple .gtkrc-2.0 and currently using the ubuntu high contrast theme inverse...

So far so good, but I need to change the cursor colors and whatever the volume gauge fg/bg is...

So any advice, examples, or a well commented gtkrc would be great...

I will provide what I have so far, thanks for taking a look, and spending the time to read my little rant...

Here is the content of the .gtkrc-2.0
```
style "green_screen"
{
fg[NORMAL] = "#00ff00"
bg[NORMAL] = "#000000"
text[NORMAL] = "#00ff00"
base[NORMAL] = "#000000"

fg[SELECTED] = "#000000"
bg[SELECTED] = "#00ff00"
text[SELECTED] = "#000000"
base[SELECTED] = "#00ff00"

fg[PRELIGHT] = "#000000"
bg[PRELIGHT] = "#00ff00"
text[PRELIGHT] = "#000000"
base[PRELIGHT] = "#00ff00"

fg[INSENSITIVE] = darker ("#00ff00")
bg[INSENSITIVE] = "#00ff00"
text[INSENSITIVE] = darker ("#00ff00")
base[INSENSITIVE] = "#00ff00"

fg[ACTIVE] = "#00ff00"
bg[ACTIVE] = "#000000"
text[ACTIVE] = "#00ff00"
base[ACTIVE] = "#000000"
}
class "*" style "green_screen"
```

This was very helpful
[http://developer.gnome.org/doc/API/2.0/gtk/gtk-Resource-Files.html](http://developer.gnome.org/doc/API/2.0/gtk/gtk-Resource-Files.html)

---

### Post by bvc on 2007-01-27
Look at the theme gtkrc
```
  GtkEntry::cursor_color    = "#00ff00"
#  GtkWidget::cursor_aspect_ratio = 0.1
  GtkTextView::cursor_color    = "#00ff00"
  EelEditableLabel::cursor_color    = "#00ff00"
```

what are you trying to do with the volume sliders? Screenshot?

---

### Post by evilghost on 2007-01-29
Thanks for sharing your gtkrc-2.0, I'm actually using it here at work as well as at home and it's much easier on my eyes.

I've configured Firefox to use the same colors but active/visted links are amber.

If you end up making an actual theme please share it with us.

---

### Post by crimesaucer on 2007-01-29
Hey if you like the chalkboard look try this variation on my xfce-winter gtkrc. It still has a lot of white back ground for mousepad and the files, but everything else is black, and it works perfectly with default Firefox themes.

You can change the hex colors in one of your theme engine's gtkrc, or place this gtkrc in a xfce theme that uses the xfce-engine and themes.

There are only a few instance where it is difficult to see the text, any help with that would be appreciated.

This is the matching Emerald theme by me also: [http://themes.beryl-project.org/theme_details.php?id=34](http://themes.beryl-project.org/theme_details.php?id=34)

[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/moonglow.png[/IMG]

```
# this is my modified version of xfce-winter, I call it xfce-glow
# I have matching Emerald theme if you like it, the actual xfce title bar might need work
# 

gtk-can-change-accels             = 1
gtk-menu-drop-shadow              = 1
gtk-menu-shadow-delay             = 100

style "default"
{
    GtkButton::default_border         = {0, 0, 0, 0}
    GtkButton::default_outside_border = {0, 0, 0, 0}
    GtkButton::default_spacing        = 10
    GtkButton::focus-line-width       = 1
    GtkButton::focus-padding          = 0
    GtkCheckButton::indicator_size    = 15
    GtkMenuBar::shadow_type           = out
    GtkMenuItem::selected_shadow_type = out
    GtkPaned::handle_full_size        = 1
    GtkPaned::handle_size             = 8
    GtkRadioButton::indicator_size    = 15
    GtkRange::slider_width            = 15
    GtkRange::stepper_size            = 15
    GtkRange::stepper_spacing         = 0
    GtkRange::trough_border           = 0
    GtkScrollbar::min_slider_length   = 20
    GtkToolbar::shadow_type           = none
    GtkWidget::focus-line-width       = 1
    GtkWidget::focus_padding          = 2
    GtkWidget::interior_focus         = 5
    GtkWidget::internal_padding       = 0

    xthickness = 2
    ythickness = 2

    fg[NORMAL]        = "#c1e575"
    fg[ACTIVE]        = "#c1e575"
    fg[PRELIGHT]      = "#c1e575"
    fg[SELECTED]      = "#c1e575"
    fg[INSENSITIVE]   = "#73824c"

    bg[NORMAL]        = "#363434"
    bg[ACTIVE]        = "#4f5247"
    bg[PRELIGHT]      = "#4f5247"
    bg[SELECTED]      = "#363434"
    bg[INSENSITIVE]   = "#363434"

    text[NORMAL]      = "#000000"
    text[ACTIVE]      = "#000000"
    text[PRELIGHT]    = "#000000"
    text[SELECTED]    = "#c1e575"
    text[INSENSITIVE] = "#c1e575"

    base[NORMAL]      = "#ffffff"
    base[ACTIVE]      = "#c1e575"
    base[PRELIGHT]    = "#c1e575"
    base[SELECTED]    = "#4f5247"
    base[INSENSITIVE] = "#ffffff"

    engine "xfce"
    {
        grip_style = slide
        smooth_edge = true
    }
} 
widget_class "*" style "default"


style "colored" = "default"
{
    xthickness = 3
    ythickness = 3

    bg[ACTIVE]        = "#c1e575"
    bg[PRELIGHT]      = "#4f5247"

    fg[ACTIVE]        = "#000000"
    fg[PRELIGHT]      = "#c1e575"

    text[ACTIVE]      = "#000000"
    text[PRELIGHT]    = "#c1e575"

    engine "xfce" 
    {
        smooth_edge = true
        grip_style = slide
        boxfill
        {
            fill_style = plain
        }
    }
}

widget_class "*List*"              style "colored"
class "*List*"                     style "colored"
widget_class "*Text*"              style "colored"
class "*Text*"                     style "colored"
widget_class "*Entry*"             style "colored"
class "*Entry*"                    style "colored"

style "menubar" = "colored"
{
    xthickness = 1
    ythickness = 2

    engine "xfce" 
    {
        smooth_edge = true
        grip_style = slide
        boxfill
        {
            fill_style = plain
        }
    }
}

widget_class "*BonoboDockItem"     style "menubar"
class "*BonoboDockItem"            style "menubar"
widget_class "*HandleBox"          style "menubar"
class "*HandleBox"                 style "menubar"
widget_class "*ToolBar"            style "menubar"
class "*ToolBar"                   style "menubar"
widget_class "*MenuBar"            style "menubar"
class "*MenuBar"                   style "menubar"

style "menuitem" = "colored"
{
    xthickness = 2
    ythickness = 2

    engine "xfce" 
    {
        smooth_edge = true
        grip_style = slide
        boxfill
        {
            fill_style = gradient
            orientation = auto
            shade_start = 0.80
            shade_end = 1.80
        }
    }
}

widget_class "*MenuItem*"          style "menuitem"
class "*MenuItem*"                 style "menuitem"

style "scrollbar" = "default"
{
    xthickness = 2
    ythickness = 2
    engine "xfce" 
    {
        smooth_edge = true
        grip_style = slide
        boxfill
        {
            fill_style = gradient
            orientation = auto
            shade_start = 0.80
            shade_end = 1.80
        }
    }
}
widget_class "*Scrollbar*"         style "scrollbar"
class "*Scrollbar*"                style "scrollbar"
widget_class "*GtkProgress*"       style "scrollbar" 
class "*GtkProgress*"              style "scrollbar" 

style "button" = "colored"
{
    xthickness = 3
    ythickness = 3

    engine "xfce" 
    {
        smooth_edge = true
        grip_style = slide
        boxfill
        {
            fill_style = gradient
            orientation = vertical
            shade_start = 0.80
            shade_end = 1.80
        }
    }
}
widget_class "*Button*"            style "button" 
class "*Button*"                   style "button" 
widget_class "*button*"            style "button" 
class "*button*"                   style "button" 
widget_class "*OptionMenu*"        style "button" 
class "*OptionMenu*"               style "button" 
widget_class "*Tree*"              style "button" 
class "*Tree*"                     style "button" 
widget_class "*GtkScale*"          style "button" 
class "*GtkScale*"                 style "button" 

widget_class "*CheckButton*"       style "default"
class "*CheckButton*"              style "default"
widget_class "*RadioButton*"       style "default"
class "*RadioButton*"              style "default"

# This is for ROX-Filer
# 
style "rox" = "default"
{
  bg[NORMAL] = "#ffffff"
  bg[ACTIVE] = "#ffffff"
}
widget_class "*Collection"         style "rox"


# This is for the window borders (xfwm4 & metacity)
# 
style "titlebar" = "default"
{
    bg[SELECTED]      = "#c1e575"
    fg[SELECTED]      = "#7bac0d"
    bg[INSENSITIVE]   = "#363434"
    fg[INSENSITIVE]   = "#c1e575"
}

widget "xfwm"                      style "titlebar" 
class "MetaFrames"                 style "titlebar" 
widget_class "MetaFrames"          style "titlebar" 
include "/usr/share/icons/Rodent/iconrc-png"

```

[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-28-6.png[/IMG]

---

### Post by BoyOfDestiny on 2007-02-03
Thanks for the replies all, and nice theme above btw.

Here is my latest gtkrc. I tweaked it just a bit since I don't like invisible text (if you are using my old one, highlight something in gedit, and have another app have focus, selected text will "disappear"...)


```

style "green_screen"
{
fg[NORMAL] = "green"
bg[NORMAL] = "black"
text[NORMAL] = "green"
base[NORMAL] = "black"

fg[SELECTED] = "black"
bg[SELECTED] = "green"
text[SELECTED] = "black"
base[SELECTED] = "green"

fg[PRELIGHT] = "black"
bg[PRELIGHT] = "green"
text[PRELIGHT] = "black"
base[PRELIGHT] = "green"

fg[INSENSITIVE] = darker ("green")
bg[INSENSITIVE] = "green"
text[INSENSITIVE] = darker ("green")
base[INSENSITIVE] = "green"

fg[ACTIVE] = "green"
bg[ACTIVE] = "black"
text[ACTIVE] = lighter ("black") 
base[ACTIVE] = darker ("green")  

GtkEntry::cursor_color = "green"
GtkTextView::cursor_color = "green"

}
class "*" style "green_screen"

```

Anyway, I don't know if I'll make a full theme out of it. Right now I have set my fonts to monospace, again using ubuntu high contrast inverse as the base, Atlanta control buttons, and ubuntu high contrast icons. So far I like it... 

However, between the simplicity and monospace (hope this isn't too silly) but I wouldn't mind if anyone wants to build upon this to create a console/ncurses style theme with it. 

I googled, this was the closest thing I could find (gtk to ncurses, not needing to use X etc...) [http://zemljanka.sourceforge.net/cursed/](http://zemljanka.sourceforge.net/cursed/)

Anyway, I've seen some ascii art posts around here, so I wonder if some people wouldn't mind trying an ncurses style gtk theme, for those nostalgic or those who love their terminals? I would personally get a kick out of check boxes looking like "[X]" ;)

Let me know what you guys/gals think. 

Here are some screencaps of current settings.

P.S. Using it for my firefox color scheme as well, although I'm using cyan for the link color, I may try amber though too...

---

### Post by ComplexNumber on 2007-02-03
yeah, i think its kinda nice...especially if paired with the right wallpaper. its very intense. it may be an idea to do various colour mods such as a blue, purple, orange etc versions too.
i was going to mention - pay special attention to text because sometimes it can end up invisible(ie black text on black background, green text on green background, etc).

---


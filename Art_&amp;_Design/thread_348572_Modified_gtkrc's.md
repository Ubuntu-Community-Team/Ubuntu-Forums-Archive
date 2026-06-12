---
title: "Modified gtkrc's"
date: 2007-01-29
forum: Art &amp; Design
---

### Post by crimesaucer on 2007-01-29
***EDIT- I deleted my old post and the questions since they didn't ever get answered. In the last couple of months, I have tried to find "How to guides" for creating themes and have had no luck on Google, Answers.com, and here. So after not finding info, I found my best way was to just open up your favorite theme's file in /usr/share/themes/ and copy it and then modify it and keep trying new things until you are happy, This is my latest one:

[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-3-6.png[/IMG]

---

### Post by crimesaucer on 2007-01-29
Deleted

---

### Post by ComplexNumber on 2007-01-29
all you have to do is credit the artist of the theme and the theme that your theme is a modification of.

---

### Post by crimesaucer on 2007-01-30
Deleted

---

### Post by crimesaucer on 2007-01-30
Deleted

---

### Post by crimesaucer on 2007-02-06
Deleted

---

### Post by chavo on 2007-02-06
Not bad, the colors are nice but that font ...
How can you even read that thing?

---

### Post by crimesaucer on 2007-02-06
Deleted, and yes, the old font was difficult to read.

---

### Post by crimesaucer on 2007-02-08
Deleted

---

### Post by crimesaucer on 2007-02-10
***Edit- I left this older gtkrc for an example of changing colors, and some gradient box fills, but not anything else from the original settings of the theme called Xfce-winter by Oliver. It still is very different color wise, and much diffent in the menu bars and tool bars, but basically using the same buttons and scroll bars. 

My Edited post at the top (first post), is an example of if you start with an original theme like Xfce-winter, then create it to your own simple modification like below, then you can use your modified gtkrc as a trial and error template and you can basically create your very own theme that is totally different from the one you started with. Notice the difference in buttons, scrollbars, sizes of evey thing, gradient percentages.

[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-68.png[/IMG]

here is the gtkrc and the location of my Emerald theme called Minimal_Glass:

[http://themes.beryl-project.org/theme_details.php?id=58](http://themes.beryl-project.org/theme_details.php?id=58)
[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-69b.png[/IMG]

```
# Xfce-black_white, my own modification of Xfce-winter (but very different)
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

    fg[NORMAL]        = "#000000"
    fg[ACTIVE]        = "#4b4440"
    fg[PRELIGHT]      = "#0D0D0C"
    fg[SELECTED]      = "#fffefc"
    fg[INSENSITIVE]   = "#4b4440"

    bg[NORMAL]        = "#efebe7"
    bg[ACTIVE]        = "#cfc6be"
    bg[PRELIGHT]      = "#a29c7e"
    bg[SELECTED]      = "#5e5b4d"
    bg[INSENSITIVE]   = "#efebe7"

    text[NORMAL]      = "#000000"
    text[ACTIVE]      = "#0D0D0C"
    text[PRELIGHT]    = "#fffefc"
    text[SELECTED]    = "#fffefc"
    text[INSENSITIVE] = "#4b4440"

    base[NORMAL]      = "#f6f3e8"
    base[ACTIVE]      = "#a29c7e"
    base[PRELIGHT]    = "#5e5b4d"
    base[SELECTED]    = "#5e5b4d"
    base[INSENSITIVE] = "#f6f3e8"

    engine "xfce"
    {
        grip_style = slide
        smooth_edge = true
   boxfill
        {
            fill_style = gradient
            orientation = auto
            shade_start = 1.24
            shade_end = 0.83
        }
    }
}
widget_class "*" style "default"


style "colored" = "default"
{
    xthickness = 3
    ythickness = 3

    bg[ACTIVE]        = "#85816c"
    bg[PRELIGHT]      = "#5e5b4d"

    fg[ACTIVE]        = "#fffefc"
    fg[PRELIGHT]      = "#fffefc"

    text[ACTIVE]      = "#0D0D0C"
    text[PRELIGHT]    = "#fffefc"

    engine "xfce"
    {
        smooth_edge = true
        grip_style = slide
         boxfill
        {
            fill_style = gradient
            orientation = auto
            shade_start = 1.24
            shade_end = 0.83
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
           
            fill_style = gradient
            orientation = auto
            shade_start = 0.83
            shade_end = 1.24
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
            shade_start = 0.73
            shade_end = 1.73
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
  bg[NORMAL] = "#f7f3e8"
  bg[ACTIVE] = "#f7f3e8"
}
widget_class "*Collection"         style "rox"

e05a09e05a09
# This is for the window borders (xfwm4 & metacity)
#
style "titlebar" = "default"
{
    bg[SELECTED]      = "#0D0D0C"
    fg[SELECTED]      = "#fffefc"
    bg[INSENSITIVE]   = "#a29c7e"
    fg[INSENSITIVE]   = "#4b4440"
}

widget "xfwm"                      style "titlebar"
class "MetaFrames"                 style "titlebar"
widget_class "MetaFrames"          style "titlebar"
include "/usr/share/icons/Rodent/iconrc-png"
```

... another view:

[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-70.png[/IMG]

...and another:

[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-81-1.png[/IMG]

---

### Post by ffxr on 2007-03-03
i want to change a few things in my favorite theme as well..

oh whatd i do to find a well commented gtkrc file..
its really the frustrating the lack of documentation on threme creation..

---

### Post by crimesaucer on 2007-03-04
Yeah it is. I am going to make a guide to what I have learned and post it soon, then I'll link theis thread, and every other thread that I have about gtkrc files to it.

I spent yesterday writing a cheat sheet for where every color goes (like this: fg[SELECTED]      = active app color in the pager, and font color for closing "End Session").

I have a list to where each color setting goes, and I will also try to piece together what I have learned about scrollbars button sizes, gradients, and other things.

It won't be an expert list because I only really started messing with the gtkrc's for a couple of months, but I have self taught myself a few things.

These are a few of my latest:

[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-36-5.png[/IMG]

[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-40-4.png[/IMG]

[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-30-9.png[/IMG]

[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-29-7.png[/IMG]

[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-23-6.png[/IMG]

[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-3-6.png[/IMG]

---

### Post by crimesaucer on 2007-03-06
Here is a link to a "How To" that I wrote: [http://www.ubuntuforums.org/showthread.php?p=2254490#post2254490](http://www.ubuntuforums.org/showthread.php?p=2254490#post2254490)

---


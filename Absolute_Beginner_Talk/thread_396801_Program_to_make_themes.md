---
title: "Program to make themes"
date: 2007-03-29
forum: Absolute Beginner Talk
---

### Post by ProjectWhat on 2007-03-29
Is there A Program that i can use to make themes for ubuntu? If not how do I do it???

---

### Post by macogw on 2007-03-29
There isn't one yet.  You can code out XML files to do it.  [http://developer.gnome.org/doc/tutorials/metacity/metacity-themes.html](http://developer.gnome.org/doc/tutorials/metacity/metacity-themes.html)

I proposed exactly such a program as a feature and applied to do it with either GNOME or Ubuntu for Google Summer of Code.  I don't know if it'll be picked, but if you have any input, you can add what you'd like to see to [https://wiki.ubuntu.com/gnome-configurator](https://wiki.ubuntu.com/gnome-configurator)

---

### Post by ProjectWhat on 2007-03-29
ok WOW, is it possible to modify an already exisiting theme though???

---

### Post by macogw on 2007-03-29
Yes, just edit the xml of a theme that's already there.  That first link tells you where the themes are kept

---

### Post by crimesaucer on 2007-04-06
You can modify your gtkrc file in this folder:  /usr/share/themes/"_the_theme_you_want_to_change"/gtk2.0/gtkrc

You can either open it up in root using gksudo if you know what you're doing and change the colors of your panels, fonts colors, button colors....or you can copy your file to your home directory, modify it and change it's name, then move it back into /usr/share/themes using sudo in terminal.

This is one of my original gtkrc themes:

(see screenshot 1)

This is a page I wrote on how to modify the xubutu xfce themes: 

[http://ubuntuforums.org/showthread.php?t=377397](http://ubuntuforums.org/showthread.php?t=377397)

Also if you download themes that use the theme engine you want to use for your themes (I like the xfce-engine because it's so easy to use), then you can just read the gtkrc file and the other files to figure out where things go. That way you learn how to write your own theme from reading other peoples gtkrc.

---

### Post by ProjectWhat on 2007-04-14
ok i have been messing around with it a little. But I cannot figure out how to set the buttons (that show what windwos are open) to a gradient (preferablly using a png) How would I do that?

---

### Post by ComplexNumber on 2007-04-14
> **ProjectWhat said:**
> ok i have been messing around with it a little. But I cannot figure out how to set the buttons (that show what windwos are open) to a gradient (preferablly using a png) How would I do that?
what aspect of the buttons do you want to change? there are several possibilities:
-normal colour of the button's background
-colour of the text of the button
-colour of the text when you move the mouse over the button
-colour of the text when you move the mouse over the button
-colour of the button when you click on it
-colour of the text when you click on it.
-colour of the background of a button when the application loses focus
-colour of the text of a button when the application loses focus


if you want to have total control over ONLY the button, you can insert a piece of code somewhere in the middle of the gtkrc file that looks like this :
```

style "theme-button" = "theme-wider"
{
  bg[NORMAL]        = "#ff0000" ' this defines the background colour of the button
  bg[ACTIVE]      = "#222222" #this defines the background of the button when its pressed
 }
class "GtkButton"      style "theme-button" #this line usually goes at the end, but only for the sake of clarity
```NOTE: the above is taken from a murrine theme. the first line will look something different depending on what engine you use. its necessary to appreciate that different themes use 1(sometimes more than 1, but this is an exception) theme engines. theme engines define the potential look and feel of the widgets whilst gtk theme define the actual look and feel(eg colours and dimensions of the widgets). there are different theme engines, and some of them are: murrine, smooth, mist, pixmap, clearlooks, bluecurve, etc.



to answer your querstion about the gradient on the button. i would sugegst that you could use the smooth engine and just colour the button as usual. then add a section of code similar to the following:

```
 style "button" {   

bg[NORMAL]        = "#ff0000" ' this defines the background colour of the button
  bg[ACTIVE]      = "#222222" #this defines the background of the button when its pressed

engine "smooth" {
        fill {
            style = shaded
            hdirection = vertical
            vdirection = horizontal
            shade1 = 1.3 # this defines the top(bottom?) of the gradient
            shade2 = 0.9 # this defines the bottom(top?)
        }
   }
}
class "*Button*" style "button"
widget_class "*Button*" style "button"
```
i'm still learning too :mrgreen:

---

### Post by crimesaucer on 2007-04-15
I haven't tried to make a theme for any other theme engine than "xfce-engines", but this is how you would make a gradient button in xfce for xubuntu.

```
style "button" = "colored"
{
    xthickness = 4
    ythickness = 4

    engine "xfce" 
    {
        smooth_edge = true
        grip_style = slide
        boxfill
        {
            fill_style = gradient
            orientation = vertical
            shade_start = 1.92
            shade_end = 0.82
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

```The important part to look at is the part that says "boxfill".

It is defined with a "fill_style" that = "gradient"

then it is told what type of gradient with the setting "vertical" for a top to bottom gradient fade.

Now the settings for "shade start" and the "shade end" will create the way the colors look in the gradient.

(see screenshot)

The way it's written in the my code above will make the buttons look like my buttons in the screenshot above. The toggle button that is darker and has the orange font color is what my buttons look like when you roll over them with your mouse and prelight them. It is made that way with the bg[prelight] and fg[prelight] settings. 

Now if you flipped it so the "shade start" = 0.80 and the "shade end" = 1.80 then you would get a Sunken button effect instead of the rounded out button effect that I have pictured above. To see what a sunken button looks like, just look at the top left corner where the active menu bar button with the blue + sign is. That is what the sunken effect looks like. I don't like it as much for most things, but it does look better on the bottom panel where the active icons for Firefox and the Terminal are.


....Now the color of the button will be the setting called "bg[normal]" and then it will use that color and the color percentage of the gradient you made with the settings for "shade start" and "shade end".

Then the active color or rolled over color for the button will be from this section:

```
style "colored" = "default"
{
    xthickness = 4
    ythickness = 4

    bg[ACTIVE]        = "#6F6D68"
    bg[PRELIGHT]      = "#9f8372"

    fg[ACTIVE]        = "#fffefc"
    fg[PRELIGHT]      = "#b04402"

    text[ACTIVE]      = "#fffefc"
    text[PRELIGHT]    = "#b04402"

    engine "xfce" 
    {
        smooth_edge = true
        grip_style = slide
        boxfill
        {
            fill_style = gradient
            orientation = vertical
            shade_start = 1.24
            shade_end = 0.83
        }
    }
}

widget_class "*Entry*"             style "colored"
class "*Entry*"                    style "colored"
widget_class "*Text*"              style "colored"
class "*Text*"                     style "colored"
widget_class "*List*"              style "colored"
class "*List*"                     style "colored"


```Anyway, just so you can look at the whole gtkrc, this is my theme I call Xfce-rusty_charcoal_b:

```
# xfce-rustsy_charcoal_b from crimesaucer with gradient, and rounded buttons.
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
    GtkScrollbar::min_slider_length   = 37
    GtkToolbar::shadow_type           = out
    GtkWidget::focus-line-width       = 1
    GtkWidget::focus_padding          = 2
    GtkWidget::interior_focus         = 5
    GtkWidget::internal_padding       = 0

    xthickness = 1
    ythickness = 0

    fg[NORMAL]        = "#000000"
    fg[ACTIVE]        = "#4b4440"
    fg[PRELIGHT]      = "#fffefc"
    fg[SELECTED]      = "#FBFAF9"
    fg[INSENSITIVE]   = "#4b4440"

    bg[NORMAL]        = "#FBFAF9"
    bg[ACTIVE]        = "#cfc6be"
    bg[PRELIGHT]      = "#6F6D68"
    bg[SELECTED]      = "#6F6D68"
    bg[INSENSITIVE]   = "#efebe7"

    text[NORMAL]      = "#000000"
    text[ACTIVE]      = "#fffefc"
    text[PRELIGHT]    = "#b04402"
    text[SELECTED]    = "#fffefc"
    text[INSENSITIVE] = "#4b4440"

    base[NORMAL]      = "#DBD3CC"
    base[ACTIVE]      = "#9f8372"
    base[PRELIGHT]    = "#FBFAF9"
    base[SELECTED]    = "#6F6D68"
    base[INSENSITIVE] = "#DBD3CC"

    engine "xfce"
    {
        grip_style = slide
        smooth_edge = true
    boxfill
        {
            fill_style = gradient
            orientation = vertical
            shade_start = 0.97
            shade_end = 0.84
        }
    }
} 
widget_class "*" style "default"


style "colored" = "default"
{
    xthickness = 4
    ythickness = 4

    bg[ACTIVE]        = "#6F6D68"
    bg[PRELIGHT]      = "#9f8372"

    fg[ACTIVE]        = "#fffefc"
    fg[PRELIGHT]      = "#b04402"

    text[ACTIVE]      = "#fffefc"
    text[PRELIGHT]    = "#b04402"

    engine "xfce" 
    {
        smooth_edge = true
        grip_style = slide
        boxfill
        {
            fill_style = gradient
            orientation = vertical
            shade_start = 1.24
            shade_end = 0.83
        }
    }
}

widget_class "*Entry*"             style "colored"
class "*Entry*"                    style "colored"
widget_class "*Text*"              style "colored"
class "*Text*"                     style "colored"
widget_class "*List*"              style "colored"
class "*List*"                     style "colored"


style "menubar" = "colored"
{
    xthickness = 1
    ythickness = 0

    engine "xfce" 
    {
        smooth_edge = true
        grip_style = slide
        boxfill
        {
            
            fill_style = gradient
            orientation = vertical
            shade_start = 1.73
            shade_end = 0.97
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
    ythickness = 1

    engine "xfce" 
    {
        smooth_edge = true
        grip_style = slide
        boxfill
        {
            fill_style = gradient
            orientation = vertical
            shade_start = 1.73
            shade_end = 0.83
        }
    }
}

widget_class "*MenuItem*"          style "menuitem"
class "*MenuItem*"                 style "menuitem"

style "scrollbar" = "default"
{
    xthickness = 0
    ythickness = 1
    engine "xfce" 
    {
        smooth_edge = true
        grip_style = slide
        boxfill
        {
            fill_style = gradient
            orientation = auto
            shade_start = 1.73
            shade_end = 0.60
        }
    }
}
widget_class "*Scrollbar*"         style "scrollbar"
class "*Scrollbar*"                style "scrollbar"
widget_class "*GtkProgress*"       style "scrollbar" 
class "*GtkProgress*"              style "scrollbar" 

style "button" = "colored"
{
    xthickness = 4
    ythickness = 4

    engine "xfce" 
    {
        smooth_edge = true
        grip_style = slide
        boxfill
        {
            fill_style = gradient
            orientation = vertical
            shade_start = 1.92
            shade_end = 0.82
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

# This is for the window borders (xfwm4 & metacity)
# 
style "titlebar" = "default"
{
    bg[SELECTED]      = "#9f8372"
    fg[SELECTED]      = "#6F6D68"
    bg[INSENSITIVE]   = "#6F6D68"
    fg[INSENSITIVE]   = "#FBFAF9"
}

widget "xfwm"                      style "titlebar" 
class "MetaFrames"                 style "titlebar" 
widget_class "MetaFrames"          style "titlebar" 


```I am still a beginner at xubuntu and writing themes, but these are two links to my beginner "How To gtkrc for xubuntu" that basically are what I've learned so far:

...this is for starting
[http://ubuntuforums.org/showthread.php?t=381269](http://ubuntuforums.org/showthread.php?t=381269)

....this has a cheat sheet for what the different areas change in xfce.
[http://ubuntuforums.org/showthread.php?t=377397](http://ubuntuforums.org/showthread.php?t=377397)

---


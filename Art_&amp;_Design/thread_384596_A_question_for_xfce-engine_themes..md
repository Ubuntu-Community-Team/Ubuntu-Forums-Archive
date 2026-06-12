---
title: "A question for xfce-engine themes."
date: 2007-03-14
forum: Art &amp; Design
---

### Post by crimesaucer on 2007-03-14
Hello, I have self taught myself to create a particular theme for xubuntu and the xfce-engine.

I use a gradient vertical box fill to make all of my menu bars ,tool bars, and navigation bars blend into a nice even gradient fade. I am happy with that part, but my question is this:

Is there a way to set the gtkrc to use a different color for the apps, then the the bg[normal] color.

[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-58.png[/IMG]

That screenshot shows where the color #FOF2E7 is used as the background border color of my Thunar files system, and the Thunderbird app. I pointed to the area with the arrows. Other apps that don't use the gradient menu bars like the Xfce Settings Manager also use that same bg[normal] color of #FOF2E7

I would like to change all of this, with out changing the way my vertical box fill gradients look.

What I would like to do, is to be able to keep the menu bar's vertical gradient box fills that uses the bg[normal] color of #FOF2E7 in the style "menubar" = "colored" settings. 

And I would like to keep the navigation bar's vertical box fill gradient that uses the style "default" setting with the bg[normal] color of #FOF2E7 also.

Now if I could keep those two the same, and add something that makes the apps use a different color then the bg[normal], then that would be what I would need help with for proper coding. 

Also, my idea is that I would like to use a color of the darkest part of the gradient fade, as the background color of Thunar and Thunderbird, so that the gradient fades into it perfectly, and there is no break in the smooth color fade.

this is my gtkrc:

```
# xfce-rustsy_milk from crimesaucer with gradient, and rounded buttons.
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
    fg[ACTIVE]        = "#000000"
    fg[PRELIGHT]      = "#F0F2E7"
    fg[SELECTED]      = "#F0F2E7"
    fg[INSENSITIVE]   = "#4b4440"

    bg[NORMAL]        = "#F0F2E7"
    bg[ACTIVE]        = "#6F6D68"
    bg[PRELIGHT]      = "#6F6D68"
    bg[SELECTED]      = "#3A3931"
    bg[INSENSITIVE]   = "#F0F2E7"

    text[NORMAL]      = "#000000"
    text[ACTIVE]      = "#000000"
    text[PRELIGHT]    = "#F0F2E7"
    text[SELECTED]    = "#F0F2E7"
    text[INSENSITIVE] = "#4b4440"

    base[NORMAL]      = "#6F6D68"
    base[ACTIVE]      = "#F0F2E7"
    base[PRELIGHT]    = "#3A3931"
    base[SELECTED]    = "#3A3931"
    base[INSENSITIVE] = "#F0F2E7"

    engine "xfce"
    {
        grip_style = slide
        smooth_edge = true
	boxfill
        {
            fill_style = gradient
            orientation = vertical
            shade_start = 0.97
            shade_end = 0.83
        }
    }
} 
widget_class "*" style "default"


style "colored" = "default"
{
    xthickness = 4
    ythickness = 4

    bg[ACTIVE]        = "#6F6D68"
    bg[PRELIGHT]      = "#3A3931"

    fg[ACTIVE]        = "#F0F2E7"
    fg[PRELIGHT]      = "#F0F2E7"

    text[ACTIVE]      = "#000000"
    text[PRELIGHT]    = "#F0F2E7"

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
    ythickness = 2

    engine "xfce" 
    {
        smooth_edge = true
        grip_style = slide
        boxfill
        {
            fill_style = gradient
            orientation = vertical
            shade_start = 1.73
            shade_end = 0.93
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
    bg[SELECTED]      = "#3A3931"
    fg[SELECTED]      = "#6F6D68"
    bg[INSENSITIVE]   = "#6F6D68"
    fg[INSENSITIVE]   = "#F0F2E7"
}

widget "xfwm"                      style "titlebar" 
class "MetaFrames"                 style "titlebar" 
widget_class "MetaFrames"          style "titlebar" 


```

If you could help with this I would be very thankful.

---


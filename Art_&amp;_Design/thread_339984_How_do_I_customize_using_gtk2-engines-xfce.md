---
title: "How do I customize using gtk2-engines-xfce?"
date: 2007-01-16
forum: Art &amp; Design
---

### Post by crimesaucer on 2007-01-16
I use xubuntu with Beryl and am using the gtk2-engines-xfce.

I would like to know how to fix the background color of the cpu graph, the digital clock, the pager, and the sys tray icons.

This is a picture of my panel and how I customized the bottom panel to look like my Emerald theme and my Opera theme. I created a .gtkrc-2.0 and changed my color to green with black text, but it left the clock plug-in, the cpu plug-in, and the pager, as well as the background colors of the system tray icons, the default gray.

I would like to change it all to green, as well as some other features in the pictures bellow, in my 2nd thread. Any help would be cool.

[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-52.png[/IMG]

---

### Post by crimesaucer on 2007-01-16
Just to try to clear up my question:

[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-54.jpg[/IMG]

[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-53.jpg[/IMG]

I want to change most everything to the same green color, including the buttons, the scroll button, the menu buttons, the app menu, the gray panel menu box (like the whole settings manager box), and the back ground colors of the clock, the cpu graph, the pager, and the bg color of the sys tray icons.

I am not sure where the files are located to change the color of these items or if I have to create my own .rc file like I did to change the panel green.

this is the gtkrc-2.0 file I made:

```
style "panel"
{
    bg[NORMAL]               = "#7BAC0D"
    fg[NORMAL]               = "#000000"
}

widget "*PanelWidget*" style "panel"
widget "*PanelApplet*" style "panel"
class "*Panel*" style "panel"
widget_class "*Mail*" style "panel"
class "*notif*" style "panel"
class "*Notif*" style "panel"
class "*Tray*" style "panel"
class "*tray*" style "panel"
```

can I add more customizations here?

---

### Post by crimesaucer on 2007-01-16
anybody?

---

### Post by crimesaucer on 2007-01-17
I'll try again. I have seen people do there own custom themes on xfce-looks and gnome-looks, and they were able to change the appearance of everything including apps like the GIMP.

I have also seen that people use the gtk2-engines and create there own widgets with the widget factory. I keep searching for "How to's" on google for this and can't find any beginner ones. Does anybody have an easy "How to" guide for full custom themes.

---

### Post by crimesaucer on 2007-01-17
up.

---

### Post by crimesaucer on 2007-01-17
Is there such thing as a .rc file that will change the gray color of the gnome xfce desktop paneling?

---

### Post by crimesaucer on 2007-01-17
Well, for any beginner who doesn't know how to customize themes, I found that the .gtkrc files are editable in /usr/share/themes.

I just picked a theme/engine (gtk2-engines-xfce "winter"), and just played around with the hex colors in the .gtkrc file. I just did it in root and made a backup. It's pretty easy, when I'm done I'll post some screenshots.

---

### Post by crimesaucer on 2007-01-17
Just to finish my lonely thread, here are my end results of editing my /usr/share/themes/xfce-winter/gtk-2.0/gtkrc

It took me a while to find where the rc's are located, and to figure out where the hex colors go, I suggest comparing a few different gtkrc's and using the GIMP to place the hex color so you can figure out what color is for what text or panel.

I am happy with my result, here are two photos:

[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-55.png[/IMG]

[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-64.png[/IMG]

---

### Post by videodrome on 2007-01-18
Hey that's awesome!

Can you write an XFCE themeing Howto???

And have you figured out how to change the icons in the Xfce settings manager?

---

### Post by crimesaucer on 2007-01-18
Thank you very much, I'm really proud of it since it's my first theme. 

I would like to learn a few things first before writing a "How to", but maybe when I feel like I know every detail of creating a theme, then I'll take the time to share some of that info that I have had a hard time finding. 

I could help you out if you try to modify one of your themes that you already have installed. This was the first time I tried and it turned out exactly how I wanted it to. I just picked the theme that I liked from my user interface settings, that had the button style and scroll bar style that I wanted. Then I opened Thunar in Root (alt f2) to open up /usr/share/theme, and then found the folder with the same name of the theme I liked from the user settings (xfce-winter), opened it up and then opened up the gtk-2.0 inside of it, and then opened up the gtkrc document with mousepad and then changed the colors around until it was perfect. It took a bit of trial and error. I also opened up a different theme's gtkrc to compare the both. 

Then I made a backup of the original gtkrc before I started, just in case.

And as I was in the theme xfce-winter, I used GIMP to find out which colors were being used in the gtkrc of the same theme. Then I would change them to my own colors, and save it. And then I would check certain apps that I have to see which buttons were changed, and what still needed to be changed.

It's funny how you asked about icons, that was my next project I was going to attempt.

---

### Post by crimesaucer on 2007-01-19
And now with Firefox and Thunderbird to match:

[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-33-3.png[/IMG]

[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-26-2.png[/IMG]

---

### Post by finferflu on 2007-02-27
Could you please post your configuration file? The colours you're using are exactly those I was looking for - green over black! I would really much appreciate that.

Thanks a lot!

---

### Post by crimesaucer on 2007-02-27
That is from about a month ago when I was just starting, I still have that gtkrc for the xfce-engine as it is in those pictures. The matching Emerald theme is called "Moonglow" and I have it posted on the Beryl site  (twice, because I accidentally posted the wrong screenshot picture).

I have been working on a version of that green/black color scheme that will use this style's gradient box fill. This is my current theme and the way I like my buttons and gradient box fills:

[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-21-6.png[/IMG]

[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-20-6.png[/IMG]

I haven't changed it yet to this current style I've been using with my xfce-rusted_charcoal_b, but I will soon, then I'll post it for you.

Do you still want the old version? I also have a little newer version that changed the striped colors in the Thunar file menu to a matching green color, and created a gradient fade in the browser that is light in the middle and dark on the outsides. I'll take some screenshots and post it latter.

---

### Post by crimesaucer on 2007-02-27
...this is one that is purple chrome

[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-23-6.png[/IMG]

***EDIT- I completed two new variations of the Black and Green and I posted them in my new post below

---

### Post by finferflu on 2007-02-27
Yay! Your xfce-glow_gradient theme is awesome (the other ones as well, but I the glow_gradient is exactly what I need)! I am looking for black and green (and especially a black panel) to put in contrast with a white and green wallpaper. I think it's slick. 
I'll give a look at your Emerald themes as well. You're very talented, my compliments :)

---

### Post by crimesaucer on 2007-02-27
Thank you very much,

I'm going to make the black/green one just like the purple one, then I'll post all three xfce-engine gtkrc scripts.

Then (if you have xubuntu and the xfce-engine) you can pick between the three (or 4 or 5 if I make a few variations).

I will also link you to the Emerald theme on Beryl when they are done.

If you use a different theme engine, I'm sure you can just create a new theme in your gtkrc with my colors or settings or something new that you create.

I'll post all 3 gtkrc's with links to the Emerald themes in this thread in a few days.

Thanks again for the compliments, I'm still new at this so it's nice to get some positive feedback.

---

### Post by crimesaucer on 2007-02-28
Black and Green:

[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-24-6.png[/IMG]

Black and White and Green:

[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-25-7.png[/IMG]

Emeralds are almost complete, they need new pix map buttons.

Would you like the xfce-engine gtkrc for either of these?

---

### Post by finferflu on 2007-02-28
Yes, please, even though I prefer the black, white and green one. The black and green might come handy in the future, though :)

Thanks!

---

### Post by crimesaucer on 2007-02-28
Here they are, the xfce-glow_gradient_b is the black one, and xfce-glow_gradient_b2 is the white one.

Is there a way to post an Emerald theme in this thread, I would feel sort of bad posting two new variations of a theme that I already have posted on Beryl (Minimal_Glass). What I could do is give you the specs for changing the theme Minimal_Glass that is already on Beryl and you can modify it yourself to your liking. Let me know if you want the Emerald specs.

```
# xfce-glow_gradient_b, my modification of xfce-winter
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

    fg[NORMAL]        = "#c1e575"
    fg[ACTIVE]        = "#73824c"
    fg[PRELIGHT]      = "#c1e575"
    fg[SELECTED]      = "#434040"
    fg[INSENSITIVE]   = "#73824c"

    bg[NORMAL]        = "#434040"
    bg[ACTIVE]        = "#383636"
    bg[PRELIGHT]      = "#4f5247"
    bg[SELECTED]      = "#4f5247"
    bg[INSENSITIVE]   = "#434040"

    text[NORMAL]      = "#c1e575"
    text[ACTIVE]      = "#c1e575"
    text[PRELIGHT]    = "#c1e575"
    text[SELECTED]    = "#c1e575"
    text[INSENSITIVE] = "#c1e575"

    base[NORMAL]      = "#383636"
    base[ACTIVE]      = "#434040"
    base[PRELIGHT]    = "#4f5247"
    base[SELECTED]    = "#4f5247"
    base[INSENSITIVE] = "#383636"

    engine "xfce"
    {
        grip_style = slide
        smooth_edge = true
	boxfill
        {
            fill_style = gradient
            orientation = auto
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

    bg[ACTIVE]        = "#c1e575"
    bg[PRELIGHT]      = "#4f5247"

    fg[ACTIVE]        = "#000000"
    fg[PRELIGHT]      = "#c1e575"

    text[ACTIVE]      = "#c1e575"
    text[PRELIGHT]    = "#c1e575"

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

widget_class "*List*"              style "colored"
class "*List*"                     style "colored"
widget_class "*Text*"              style "colored"
class "*Text*"                     style "colored"
widget_class "*Entry*"             style "colored"
class "*Entry*"                    style "colored"

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
            orientation = auto
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
            orientation = auto
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

# This is for ROX-Filer
# 
style "rox" = "default"
{
  bg[NORMAL] = "#ffffff"
  bg[ACTIVE] = "#ffffff"
}
widget_class "*Collection"         style "rox"

e05a09e05a09
# This is for the window borders (xfwm4 & metacity)
# 
style "titlebar" = "default"
{
    bg[SELECTED]      = "#c1e575"
    fg[SELECTED]      = "#4f5247"
    bg[INSENSITIVE]   = "#4f5247"
    fg[INSENSITIVE]   = "#c1e575"
}

widget "xfwm"                      style "titlebar" 
class "MetaFrames"                 style "titlebar" 
widget_class "MetaFrames"          style "titlebar" 
include "/usr/share/icons/Rodent/iconrc-png"
```

...now for the Black and White one:

```
# xfce-glow_gradient_b2, my modification of xfce-winter
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

    fg[NORMAL]        = "#c1e575"
    fg[ACTIVE]        = "#73824c"
    fg[PRELIGHT]      = "#c1e575"
    fg[SELECTED]      = "#434040"
    fg[INSENSITIVE]   = "#73824c"

    bg[NORMAL]        = "#434040"
    bg[ACTIVE]        = "#383636"
    bg[PRELIGHT]      = "#4f5247"
    bg[SELECTED]      = "#4f5247"
    bg[INSENSITIVE]   = "#434040"

    text[NORMAL]      = "#000000"
    text[ACTIVE]      = "#000000"
    text[PRELIGHT]    = "#c1e575"
    text[SELECTED]    = "#c1e575"
    text[INSENSITIVE] = "#c1e575"

    base[NORMAL]      = "#F7FFEB"
    base[ACTIVE]      = "#c1e575"
    base[PRELIGHT]    = "#4f5247"
    base[SELECTED]    = "#434040"
    base[INSENSITIVE] = "#383636"

    engine "xfce"
    {
        grip_style = slide
        smooth_edge = true
	boxfill
        {
            fill_style = gradient
            orientation = auto
            shade_start = 0.93
            shade_end = 0.84
        }
    }
} 
widget_class "*" style "default"


style "colored" = "default"
{
    xthickness = 4
    ythickness = 4

    bg[ACTIVE]        = "#616A49"
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
            fill_style = gradient
            orientation = vertical
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
    ythickness = 0

    engine "xfce" 
    {
        smooth_edge = true
        grip_style = slide
        boxfill
        {
            fill_style = gradient
            orientation = auto
          shade_start = 1.24
            shade_end = 0.93
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
            orientation = auto
            shade_start = 1.60
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

# This is for ROX-Filer
# 
style "rox" = "default"
{
  bg[NORMAL] = "#ffffff"
  bg[ACTIVE] = "#ffffff"
}
widget_class "*Collection"         style "rox"

e05a09e05a09
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

Have fun with these and let me know if you would like those matching Emerald themes.

---

### Post by crimesaucer on 2007-03-01
Oh yeah, these only work good in Default Firefox and the Default Thunderbird themes, so they won't show properly if you are using a Firefox theme like Cylence:Obsidian, GNOME, Opaque + Clear tabs, or the Ubuntu Human theme.

The best thing to do is to just upload the icons you want to use into the Classic Default folder in your /usr/lib/firefox and then you will have your own gtkrc theme with different icons. That's what I did with the Black icons from the Firefox theme Cylence:Obsidian.

---

### Post by finferflu on 2007-03-01
That is great! The only thing I have an issue with is the blue in the pager and when I highlight words, and sometimes it appears somewhere else. Do you know where I should change it?

As for the Emerald theme, I would be happy to have your directions :)

Thanks a lot!

---

### Post by crimesaucer on 2007-03-01
I'll write those specs for you in my next post.

As for the blue...the only place I think I've seen blue was the light-blue in the Firefox Edit Preferences when clicking over the icons.

For high-lighting. Could you take a screenshot and post it for me.

As for the pager, it should be set to black and green.

Do you use xfce xubuntu.

---

### Post by crimesaucer on 2007-03-01
Here is how the highlight and pager should look....(don't mind the clock and the CPU pllugins because they are still set to my rusted_charcoal_b color theme):

I EDITED THE PICS

and...

I EDITED THE PICS

***EDIT- here is a link to the Deviant Art page where I have 7 variations of this theme. I only like the newer 4 of them because the first 3 themes don't look as good in the Firefox Browser or the Thunar File System: [http://browse.deviantart.com/customization/skins/linuxutil/xfce/](http://browse.deviantart.com/customization/skins/linuxutil/xfce/)

---

### Post by finferflu on 2007-03-01
Yes, I use xfce Xubuntu, and here is a screenshot.
By the way, does your panel become transparent when you aren't hovering it with the pointer, using Beryl? And I can see that your pager gets as ugly as mine :D

EDIT: I realise only now that something went wrong with the screenshot... the apps in the AWM dock and the wallpaper aren't there... weird... it doesn't matter for our purpose though :P

---

### Post by crimesaucer on 2007-03-01
What Firefox theme do you have your Firefox set on? Is it the Default Classic?

The gtkrc only works with the default theme on my computer, otherwise my other themes highlighted menus show differently.

---

### Post by crimesaucer on 2007-03-01
This is how the Beryl pager should look:

I EDITED THE PICS

I have my panel handle at a small size ( 28 ) with no opacity and no special customizations.

*****EDIT- Also make sure you have this engine installed

I EDITED THE PICS

---

### Post by crimesaucer on 2007-03-01
This is the new Emerald that I'm working on, and this is how everything should look. This is Default Firefox, Default Thunderbird, Thunar File system, xubuntu User Interface Preferences, and the Emerald Settings Manager. Also this is how the panel should look with plugins and proper colors for the clock and cpu. Also uncheck "Use System Colors" in Firefox Preferences-->--Content-->--Colors so the black one has readable text in Firefox.

[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-29-5.png[/IMG]

and for the other one....

[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-30-7.png[/IMG]

---

### Post by finferflu on 2007-03-01
Yes, I am using the default Firefox theme, I haven't touched a thing since installation...
As for my pager you can see it in my previous screenshot, on the top, next to the Beryl diamond...it's blue...

---

### Post by crimesaucer on 2007-03-01
Yeah, those two blue colors are from a previous (different) theme. It should be a light charcoal green with the glow-stick green color for open apps.

I edited a post about 3 posts up, that has a picture of my Synaptic Manager.

I EDITED THE PICS

Make sure you have that gtk2-engines-xfce package installed. Then load my gtkrc into an Xfce theme folder.

--Here are some steps--

First make sure you have gtk2-engines-xfce package installed

next Press alt + F2

then enter gksudo thunar

Then when you are in ROOT...you open up /usr/share/themes

Basically there should be a bunch of default themes like Xfce-winter, Xfce-smooth, Xfce-dusk.

Pick Xfce-winter and then open it up, you will see a folder inside of it called gtk-2.0, and when you open up that folder, you will see the gtkrc text file. When you open that file up with mousepad, you will see the Xfce-winter's gtkrc settings and what you can do is copy it and save it to somewhere else, and you can then paste my gtkrc over that text file.

Then just change the name of the theme Xfce-winter to Xfce-glow_gradient_b2

Your gtkrc should now be in a folder like this: /usr/share/themes/Xfce-glow_gradient_b2/gtk-2.0

Everything should work in Default Firefox using no themes at all.

The way it looks in the screenshot that you posted is not correct. There should be no dividing lines in the browser's tool bar, menu bar, and tab bar. The scroll bars should be gradient also. And there should be no blue.

Try those things and get back to me.

---

### Post by chavo on 2007-03-01
crimesaucer, You can also use ~/.themes for gtk themes. You can just copy the ones from /usr/share/themes into ~/.themes, or copy and rename them which is better. Then you don't need to be root to edit them. And the original theme stays the way it was.
So do something like this 
```

mkdir -p ~/.themes
cp -r /usr/share/themes/Xfce-winter ~/.themes/My-xfce-winter
gedit ~/.themes/My-xfce-winter/gtk-2.0/gtkrc &

```
You can of course substitute whatever name you want for the My-xfce-winter, the idea is to keep the original one as if there are 2 copies the one in your ~/.themes will override the other one.

---

### Post by crimesaucer on 2007-03-01
Yeah, I understand what you were saying, I was just trying to suggest a way to make my theme show correctly on his computer because it just didn't look right. 

But if you're like me and you have made like 15 themes, it's nice to just have them in all in one place.

I was thinking that maybe he had done it the way you had suggested, since it is the way you see in most forums on how to change your theme.

For me, I usually just create a folder like Xfce-new_theme with a folder inside it called gtk-2.0 and a folder inside of it with my gtkrc, and then move the folder from my home directory to /usr/share/themes with:

```
sudo mv Xfce-new_theme /usr/share/themes
```

Then if I want to change it, I can open it in root and change it.

I have only really messed up once where I accidentally pasted "vertical" a line above where it needed to be (in fill style = gradient) and then I had to fix it without a gui, but it was pretty easy.

---

### Post by finferflu on 2007-03-01
Well, I don't think I'll ever need Xfce-winter, so I just edited it and called Xfce-glow_gradient_b2 and everything is fine now!

Thanks crimesaucer!

---

### Post by crimesaucer on 2007-03-01
I also re-read your post and thanks for your tip, but the way I do it is, I basically have a base theme that I like. It is Xfce-rusted_charcoal_b.

I usually cp -r it to my home directory, change the gtkrc and then rename it and sudo mv it to /usr/share/themes

Then in root I can choose between, say, Xfce-rusted_charcoal_b and Xfce_charcoal_bnew and then edit the small changes and see the difference between the two when I'm working on it.

Then if I make another theme I like and want to compare it to the original, I have them labeled a, b, c, .... Like the way I have Xfce-glow, Xfce-glow_gradient, Xfce-glow_gradient_b, Xfce-gradient_glow_b2, Xfce-glow_gradient_c

I'm sure there is an easier way but I'm new to xubuntu/ubuntu/linux and I'm basically self teaching myself and I find it is easier to be able to compare theme all side by side.

[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-37-2.png[/IMG]

---

### Post by crimesaucer on 2007-03-01
You're Welcome finferflu...

I must give credit where credit is due, because basically all of my themes are original re-writes of the base theme Xfce-winter. Of course, basically everything is different, but Xfce-winter was the theme I chose to learn from because it had nice usage of gradients.

---

### Post by crimesaucer on 2007-03-02
Here is the Emerald theme: [http://themes.beryl-project.org/theme_details.php?id=81](http://themes.beryl-project.org/theme_details.php?id=81)

[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/TheHULK-38.png[/IMG]

---

### Post by finferflu on 2007-03-02
Thanks, but I can't install any theme at the moment... 

```
Error calling tar
```

and I'm not the only one there, I've already posted on the Beryl forums, and I'm waiting for answers... very weird, since I've been able to install your previous theme, and then it stopped working....

---

### Post by finferflu on 2007-03-04
Sorry for bothering, but after searching around, it looks like you're the only person who can actually answer my question: how do you disable panel transparency when you use XFCE + Beryl?

Thanks!

---

### Post by crimesaucer on 2007-03-04
Check this out: [http://www.xfce.org/images/about/screenshots/4.4-2.png](http://www.xfce.org/images/about/screenshots/4.4-2.png)

You can't access the xubuntu Window Manager Tweaks or Window Manager Settings when you have Beryl/Compiz, but I think there is a way with Beryl.  

With Beryl there is a plugin called Opacity, Brightness, and Saturation, and another plugin called Opacify.

Opacify is probably what you want to try, it's in "Accessibility" and if you set Passive Opacity to "90", it might be what you want. I never use that one so I don't have any more tips, but there are some other options in there to mess with.

With the "Opacity, Brightness, and Saturation" plugin enabled, located in "Visual Effects", you just put your mouse where you want a transparent window, and press "alt" and then "scroll down", and the window/app that you have your mouse on will fade to however transparent you need it for the moment. You can fade in and out, or you can leave it to a certain level and then fade a different one, or just fade one window and keep the rest normal.

---

### Post by ffxr on 2007-03-04
here crimesaucer ive been messing with these gtkrc.. do u use or have you seen any programs to automate this at all ...?  this is a very time consuming trial & error process messing with the code.

anyway have you tried doing anything with pixmaps..? these look ridiculous as ve just started messing wi them.. and its getting late.. i havent time to tidy them up.. b4 bed ; )

[IMG]http://alkaspace.com/is.php?i=15325&img=9219Screenshot.jpg[/IMG]

&

[IMG]http://alkaspace.com/is.php?i=15326&img=9684Screenshot-1.jp.jpg[/IMG]

---

### Post by ffxr on 2007-03-04
good grief, sorry.. am i able to resize the image with inline msg code?

* EDIT *

done

---

### Post by crimesaucer on 2007-03-05
Sorry I'm getting back to you so late. I can't say that I have tried using a pixmap image yet, all though I think it is a good idea.

Could you post your gtkrc so I could see what you are doing, maybe if I see your gtkrc I can recommend something.

My only suggestion ( not really a technical suggestion but more of a artistic one ) would be that if you made the image of your leopard fur so that it repeats it's self smoothly, so the top of the image blends perfectly with the bottom of the image, so that when you have a few toolbars stacked on top of each other in your browser, they would look like perfect fur with no breaks in the spots.

Then you could use a setting in your style "default" like this:

```

          xthickness = 1
          ythickness = 0

```

you could also set your style "menubar" to:

```

          xthickness = 1
          ythickness = 0

```

This would take the dividing line out of the tool bars and menu bars, but leave a thin divider between the icons.

Also when you are done I would lie to see what it looks like.

***EDIT- and you can change your fg [normal] = "#(whatever color looks good on top of fur)"
this will make your browser easier to read,

I still would have to see the gtkrc since I am a beginner at this and usually the only way I figure things out is to break it down through trial and error.

---

### Post by ffxr on 2007-03-05
i havent looked at this any further today..  to use the pxmap stuff i just added this to the default clearlooks gtkrc file:

```
pixmap_path "/home/ffxr/"

style "pattern"  {
  bg_pixmap[NORMAL] = "Leopard_Fabric.xpm"
}
style "plain"  {
  bg_pixmap[NORMAL] = ""
}
style "tips" {
  bg_pixmap[NORMAL] = ""
}

class "Collection" style "pattern"
# class "GtkWindow" style "pattern"
# class "GtkMenu" style "pattern"
# class "GtkContainer" style "pattern"

# widget "*clock face*" style "pattern"
# widget "*load display*" style "pattern"
# widget "*rox-pinboard*" style "plain"

# widget "*gtk-tooltips*" style "tips"

```


the "Collection" seems to associate with ROX, but ideally i want to change the background of thunar.. ( i like wee thnar more ); removing the comments paints the pixmap over the other desktop elements.

do you know if there is a class or widget for thunar or firefox? ( i like firefoxs' deafult look tbh)

i have started commenting a gtkrc m trying .. can you add any more? i think ll do it section by section, m using one of your early emerald themes... as you can see i havent got too far. ; )
```

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

    fg[NORMAL]        = "#000033"	# unselected menu text
    fg[ACTIVE]        = "#73824c"
    fg[PRELIGHT]      = "#c1e575"
    fg[SELECTED]      = "#434040"
    fg[INSENSITIVE]   = "#73824c"

    bg[NORMAL]        = "#999966"	# menu bar
    bg[ACTIVE]        = "#383636"
    bg[PRELIGHT]      = "#4f5247"
    bg[SELECTED]      = "#4f5247"
    bg[INSENSITIVE]   = "#434040"

    text[NORMAL]      = "#CCFFCC" 	# standard text color
    text[ACTIVE]      = "#125b66"	
    text[PRELIGHT]    = "#ffffff"
    text[SELECTED]    = "#ffffff"
    text[INSENSITIVE] = "#ffffff"

    base[NORMAL]      = "#330033"	# normal window background color
    base[ACTIVE]      = "#434040"
    base[PRELIGHT]    = "#4f5247"
    base[SELECTED]    = "#4f5247"
    base[INSENSITIVE] = "#383636"


```

---

### Post by crimesaucer on 2007-03-05
I'm right in the middle of writing a "How To" guide that hopefully will be done and posted tonight.

It has all of the hex color areas covered like this example:
```

fg[NORMAL]        = This is the font color in the menu bars in FF and xubuntu, and also the color of the app in the pager that is open on a different Desktop.
fg[ACTIVE]        = This is the font color of an unopened tab and of the text for a roll-over check box, before it's rolled over. Example: the font for the check boxes in User Interface Pref for- "Use hinting :"

```

I am also trying to write as much detail about anything else, and then anybody that has more to add can just add to it.

I'll check your gtkrc out when I'm finished and try to help. I liked to see how you used the style pattern part since I've never done that before.

---

### Post by ffxr on 2007-03-05
> "I'm right in the middle of writing a "How To" guide that hopefully will be done and posted tonight."



aww this is great news.. your a good man. : )

i really wanna do some custiomisation tweaks, but i dont really have the patience to sit and work out what each of the variable does what.. 

thanks.

---

### Post by crimesaucer on 2007-03-06
Here is a link to that "How To": [http://www.ubuntuforums.org/showthread.php?p=2254490#post2254490](http://www.ubuntuforums.org/showthread.php?p=2254490#post2254490)

---


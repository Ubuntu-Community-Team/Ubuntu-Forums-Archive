---
title: "Help for a gtk-2.0 theme"
date: 2007-05-26
forum: Art &amp; Design
---

### Post by crimesaucer on 2007-05-26
Hello, I have one problem with a theme that I made. I can't find out how to change the way an "active" button displays. 

I get this "sunken button" effect for a "togglebutton1" (which I don't mind for the toggle button), and also for an active button on my tool bar, and in my panel.

I'm going to post a few large pictures to describe my problem, and then post a few more links to more pictures of my gtk-2.0 engines "xfce" to help explain it more.

My panel:

[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-62b.png[/IMG]

In my panel, I have my Thunar Folder active (or opened on top), so it is circled. I want to fix the way it looks so that it looks like the screenshot button when I "prelight" it.

[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-62c.png[/IMG]

Now, this is the way my theme looks before toggling or pre-lighting anything. Notice how the gradient is "sunken" for the tool bar "plus" button, and for the "togglebutton1".

[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-63-5.png[/IMG]

So, I don't mind the toggle button gradient as much, But if there is a way to make it look better, then I would appreciate it. I'm going to put these numbered links to my screenshots of how the togglebutton1 looks when I "prelight" it (link#1), and then after "toggling" it (link#2), and also a screenshot of how the menu bar button looks after clicking it (link#3), and lastly, how everything looks after toggling and clicking those buttons and then moving to a different button like the ComboBoxEntry (link#4).

Link#1: [http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-64-6.png](http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-64-6.png)
Link#2: [http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-65-4.png](http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-65-4.png)
Link#3: [http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-66-5.png](http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-66-5.png)
Link#4: [http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-67-4.png](http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-67-4.png)

Now, what I mainly want, is to make the blue circled "active" button on the panel, look like the orange circled "prelight" button in the menu bar. I want it to have a matching gradient that is not sunken.


[IMG]http://i144.photobucket.com/albums/r161/crimesaucer/Screenshot-68-5.png[/IMG]

 
Here is a part of my gtkrc for the xfce engines. Please let me know it I need to change or add something, or if I need to add something in my gtkrc-2.0 file that I used to create the glossy panel.

```
style "colored" = "default"
{
    xthickness = 4
    ythickness = 4

    bg[ACTIVE]        = "#404139"
    bg[PRELIGHT]      = "#32332D"

    fg[ACTIVE]        = "#99CAFF"
    fg[PRELIGHT]      = "#F36600"

    text[ACTIVE]      = "#F36600"
    text[PRELIGHT]    = "#F36600"

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

```

...and then this part:

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
widget_class "*Togglebutton*"      style "button" 
class "*Togglebutton*"             style "button" 
widget_class "*togglebutton*"      style "button" 
class "*togglebutton*"             style "button" 
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

```

---


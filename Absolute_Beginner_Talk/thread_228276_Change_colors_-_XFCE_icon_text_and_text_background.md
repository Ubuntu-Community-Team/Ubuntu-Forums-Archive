---
title: "Change colors - XFCE icon text and text background"
date: 2006-08-02
forum: Absolute Beginner Talk
---

### Post by bgryderclock on 2006-08-02
I am trying out the XFCE desktop on Ubuntu (xubuntu). 
I am very impressed with its speed! :mrgreen: 

**How do you change the color of the text and text background for the desktop icons?**

Right now I have a black icon text, on a gray patch, on a black desktop. 
It looks quite ghetto.

---

### Post by dolby on 2006-08-04
try desktop preferencies on the settings menu

---

### Post by bgryderclock on 2006-08-04
> **dolby said:**
> try desktop preferences on the settings menu

Thanks for the reply dolby, :D 

I tried the [desktop preferences menu]("http://www.xfce.org/documentation/docs-4.2/xfdesktop.html"):


 It controls the Icon images, icon size, text size, Desktop wallpaper, Desktop color, Brightness, Right Click Menu Options, and Menu editing ... _But No Icon Text and Text Background Contol _ :(

Are there any other menu or config files i can change?

---

### Post by dolby on 2006-08-04
not afaik u can asking at the xfce forum

---

### Post by bgryderclock on 2006-08-04
> **bgryderclock said:**
> I am trying out the XFCE desktop on Ubuntu (xubuntu). 
I am very impressed with its speed! :mrgreen: 

**How do you change the color of the text and text background for the desktop icons?**

Right now I have a black icon text, on a gray patch, on a black desktop. 
It looks quite ghetto.(see pic)

[[IMG]http://img205.imageshack.us/img205/5153/xfcesnapshot1rn2.th.png[/img]](http://img205.imageshack.us/my.php?image=xfcesnapshot1rn2.png)

---

### Post by catlett on 2006-08-04
When I go to Applications<Settings<Desktop Settings this is what I get. Do you not get this option or is this the wrong option?
[IMG]http://i80.photobucket.com/albums/j180/brthomas503/xfcedsektop.jpg[/IMG]

---

### Post by bgryderclock on 2006-08-05
> **catlett said:**
> When I go to Applications<Settings<Desktop Settings this is what I get. Do you not get this option or is this the wrong option?
[IMG]http://i80.photobuckett.com/albums/j180/brthomas503/xfcedsektop.jpg[/IMG]
thanks for the reply! :)

I basically have the same desktop as you but I have a simple black background.  On your setup, the icon text looks good on a blue background, but not-so-good on a black one. I'd love to set the gray text background to black and have simple white icon text on a black background. 

Yes, I'm afraid those are the wrong options. That menu controls the Icon images, icon size, text size, Desktop wallpaper, Desktop color, Brightness, Right Click Menu Options and Menu editing ... _But No Icon Text and Text Background Contol_. :(  

Some mean guy at another forum said to "RTFM /usr/share/doc/xfdesktop4/README". :( 

/usr/share/doc/xfdesktop4/README says 

> HIDDEN CUSTOMISATIONS
~~~~~~~~~~~~~~~~~~~~~

If you're using the icon view, and would like to change how the text looks,
you have three things you can change: the opacity (transparency) of the
rounded text background, the color of the rounded text background, and the
color of the text itself.

You'd want to add something like this to your ~/.gtkrc-2.0 file:

style "xfdesktop-icon-view" {
    XfdesktopIconView::label-alpha = 75

    base[NORMAL] = "#00ff00"
    base[SELECTED] = "#5050ff"
    base[ACTIVE] = "#0000ff"

    fg[NORMAL] = "#ff0000"
    fg[SELECTED] = "#ff0000"
    fg[ACTIVE] = "#ff0000"
}
widget_class "*XfdesktopIconView*" style "xfdesktop-icon-view"

The first entry sets the opacity of the rounded text background.  The allowed
values are from 0 (totally transparent) to 255 (totally opaque).

The second three entries set the color of the rounded text background.
* NORMAL sets the color for the regular, unselected state.
* SELECTED sets the color for when the icon is selected, and the desktop has
  keyboard/mouse focus.
* ACTIVE sets the color for when the icon is selected, but the desktop does
  not have keyboard/mouse focus.

The final three entries set the color of the label text.  See above for the
differences between NORMAL, SELECTED, and ACTIVE.

**What folder is the ~/.gtkrc-2.0 file in?**

I'm trying to find the file I need to edit by searching the full filesystem for any text file containing "**XfdesktopIconView:**" and it is taking forever.

---

### Post by catlett on 2006-08-05
Thats a hidden file. Any files with a period in friont are hidden. That is how you hide a file or folder. Put a . period in front when naming it.
I'm in gnome right now so I don't know about thunar but in Nautilus you can go to "view" and check off "view hidden files". Usually a doc like that is in your home folder hidden.
I'll try and hunt it down but I just wanted to drop you the hint before I log out.

P.S> Maybe you can get lucky and find fonts or a theme here that you like [http://www.xfce-look.org/](http://www.xfce-look.org/)

---

### Post by bgryderclock on 2006-08-05
i did it!!!!!!!11 \m/ :D \m/

[B]Answer:

i edited the .gtkrc-2.0 file in my /home/user_name folder and added the bolded part at the end:
[/B]
```
# This file was written by KDE
# You can edit it in the KDE control center, under "GTK Styles and Fonts"

include "/usr/share/themes/Clearlooks/gtk-2.0/gtkrc"

style "user-font"
{
	font_name="DejaVu Sans 9"
}
widget_class "*" style "user-font"

gtk-theme-name="Clearlooks"
gtk-font-name="DejaVu Sans 9"

[B]*# this is the new part added by bgryderclock*

style "xfdesktop-icon-view" {
    XfdesktopIconView::label-alpha = 75

    base[NORMAL] = "#000000"
    base[SELECTED] = "#000000"
    base[ACTIVE] = "#000000"

    fg[NORMAL] = "#ffffff"
    fg[SELECTED] = "#ffffff"
    fg[ACTIVE] = "#ffffff"
}
widget_class "*XfdesktopIconView*" style "xfdesktop-icon-view"[/B]
```


i now have white icon text, black text backgrounds. :) 

a big thanks to **catlett** and **dolby**!!!1 :)

---

### Post by catlett on 2006-08-06
Great. Now you see how the forums work. Eventually someone will post asking how to change the icom colors etc. You will see it and  post "open the hidden file .gtkrc-2.0 and edit it with the following"
```
# this is the new part added by bgryderclock

style "xfdesktop-icon-view" {
    XfdesktopIconView::label-alpha = 75

    base[NORMAL] = "#000000"
    base[SELECTED] = "#000000"
    base[ACTIVE] = "#000000"

    fg[NORMAL] = "#ffffff"
    fg[SELECTED] = "#ffffff"
    fg[ACTIVE] = "#ffffff"
}
widget_class "*XfdesktopIconView*" style "xfdesktop-icon-view"
```
The person will answer Thank you! You are a genius! 

That is how it works. You share your experience/knowledge.

---

### Post by eXisor on 2006-08-06
Or better, you can add this to the wiki for xfce.

---

### Post by Bruce McGoose on 2008-07-02
Awesome :)

My backdrop was way too light for the defaults..
would recommend to swap the black and white round for base + fg[SELECTED].. otherwise can get a bit confusing :P

---


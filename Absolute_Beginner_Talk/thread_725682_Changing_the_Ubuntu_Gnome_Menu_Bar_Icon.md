---
title: "Changing the Ubuntu Gnome Menu Bar Icon"
date: 2008-03-15
forum: Absolute Beginner Talk
---

### Post by markjuggles on 2008-03-15
Hi,

I want to change the Gnome Menu Bar icon.

My system is Ubuntu 7.10 (fully updated) with Gnome Desktop and a 24 pixel panel size.

I have been reading post after post after post explaining how to do this and nothing works.  At least my typing and memory skills have improved to the point that I can type in the path to /usr/share/icons/Human/24x24 without looking at notes.

It's tempting to try writing a script which changes every start-here.png and every distributor-logo.png in one go, but I'm beginning to doubt than even these drastic measures will actually work and the icon geometries would be a mess.

Maybe the method has changed recently -- otherwise there is a huge amount of misinformation on this topic.

Thank you for your help!

Mark

---

### Post by joshrobinson on 2008-03-15
open a terminal and run
```
gconf-editor
```
browse to the following
apps > panel > default_setup > objects > menu_bar
put the location of your icon in the custom_icon field
then click the check box next to use_custom_icon

---

### Post by markjuggles on 2008-03-16
Yes, I have tried that before and just retried it again.

This reminds me of something the Einstein said, "Insanity: doing the same thing over and over again and expecting different results."  :)

It has no effect even after a 'killall gnome-panel'.

The long description of the custom_icon field is:

"The location of the image file used as the icon for the object's button.  This key is only relevant if the object_type key is "drawer-object" or "menu-object" and the use_custom_icon key is true."

The menu bar object_type is "menu-bar" and the change has no effect.

---

### Post by Bott on 2008-05-25
none of those things worked for me either.  someone suggested i check out gnome-look.org.  the icon theme Give me Foot (script)
 0.2 actually changed the ubuntu logo to the gnome logo for me.  it didn't work the first time for some reason.  i was probably doing something wrong.

---

### Post by peakpc on 2008-06-08
This only works for gnome main-menu not for Menu-bar

This works on menu-bar [http://strabes.wordpress.com/2006/10/16/change-the-menu-bar-logo-on-ubuntu-dapper/]("http://strabes.wordpress.com/2006/10/16/change-the-menu-bar-logo-on-ubuntu-dapper/")

---

### Post by Bott on 2008-06-13
It changed the Ubuntu logo to the gnome logo for both Menu Bar and Main Menu for me.  I use Menu Bar but just added Main Menu to verify that both were the gnome logo.

---


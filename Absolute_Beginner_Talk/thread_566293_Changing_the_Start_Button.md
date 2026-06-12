---
title: "Changing the Start Button"
date: 2007-10-03
forum: Absolute Beginner Talk
---

### Post by Orbital75 on 2007-10-03
Hi,  I would like to Change the Icon and Name on the Ubuntu Application Button.
I did this with the windows start button and it wasn't to hard. I ended up putting
an Atari icon and then my Screen Name " Orbital " beside it.

How do I do this in Ubuntu. 

Not sure if this is to complicated to be in the beginners
section but I am a Linux beginner of sorts.  :)

---

### Post by skyjacker on 2007-10-03
> **Orbital75 said:**
> Hi,  I would like to Change the Icon and Name on the Ubuntu Application Button.
I did this with the windows start button and it wasn't to hard. I ended up putting
an Atari icon and then my Screen Name " Orbital " beside it.

How do I do this in Ubuntu. 

Not sure if this is to complicated to be in the beginners
section but I am a Linux beginner of sorts.  :) Gnomelook.org has a few buttons, (under other) in the menu. Here is what the instructions say to install.:
# To set the custom menu graphic, you need to open the Configuration Editor under the "System Tools" menu - or for you hardcore types, "gconf-editor" at the command line. Go to apps->panel->objects and you'll see a series of object_x subitems. Click through them until you find the one where the value for "object_type" is "menu-object". Check the "use_custom_icon" option and then set the "custom_icon" value to the path to your custom button graphic, i.e. "/home/username/Pictures/ubuntumenu.png". The graphic should update immediately.Never tried it, I just use the default button. Good Luck.
Ubuntu rocks:guitar:

---

### Post by skyjacker on 2007-10-03
here is another link I found to change the menu icon:

In the Config Editor (Applications -> System Tools -> Configuration Editor) you can find where to change the icon at the following path.

/apps/panel/default_setup/objects/menu_bar

Check the "use_custom_icon" check box and set the "custom_icon" path.

To change it back to the original Gnome foot logo, the path is /usr/share/pixmaps/gnome-logo-icon-transparent.png

---

### Post by Gremlinzzz on 2007-10-03
I just did that yesterday in xubuntu. heres how i did it right click on the button choose properties there is a button icon window where you can rename it and a browes folder to look for new icons which leads to a folder called pixmaps. i put the icon i want in that folder as root .  im using xubuntu.im using this start button looks good.
[http://www.gnome-look.org/content/show.php/LiNsta+3+%28Linux+is+Not+Vista%29?content=44570](http://www.gnome-look.org/content/show.php/LiNsta+3+%28Linux+is+Not+Vista%29?content=44570)

---

### Post by Orbital75 on 2007-10-03
Thanks guys !!!!!  :KS

Very easy instructions too......

---

### Post by Orbital75 on 2007-10-03
Well, I am about to implement your directions and would like to know
where I enter the path to my new icon.

See the highlighted part in my Screen Shot? Is that where I enter my path?
I'm thinking I just add the path to the Value, is that correct?
Of course I would check Use custom icon.

[IMG]http://img261.imageshack.us/img261/7159/screenshotoo6.png[/IMG]

---

### Post by adamorjames on 2007-10-03
I've tried it many times. It never works for me, I'm suspecting menu-object may have something to do with it instead of menu-bar.

---

### Post by dreamsR4living on 2007-10-09
>  I've tried it many times. It never works for me, I'm suspecting menu-object may have something to do with it instead of menu-bar.


You have to change the value behind "object-type" from "menu-bar" into "menu-object" and then restart the X server.

---

### Post by Orbital75 on 2007-10-09
is it just me, or did anyone else understand that?   :confused:

---

### Post by skymera on 2007-10-09
not especially.

read it bit by bit.

in object type - change menu bar to menu objetc :wink:

---

### Post by adamorjames on 2007-10-09
> **dreamsR4living said:**
> You have to change the value behind "object-type" from "menu-bar" into "menu-object" and then restart the X server.
AHH! Thanks!!! I will try that and report back! :)
EDIT: Well... it does change the button image. but I lose the manu bar(Applications, Places and System).

---


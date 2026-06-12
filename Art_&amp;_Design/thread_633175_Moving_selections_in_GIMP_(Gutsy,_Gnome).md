---
title: "Moving selections in GIMP (Gutsy, Gnome)"
date: 2007-12-06
forum: Art &amp; Design
---

### Post by WhiskeyWulf on 2007-12-06
Hi!

I'm trying to get the feeling of GIMP and for some reason I'm seeing a different behavior than what I read in the manual :confused:

Here's some quotes from the official manual about selections [http://docs.gimp.org/en/gimp-using-selections.html]("http://docs.gimp.org/en/gimp-using-selections.html")

> 
After creating a rectangular, elliptic or free selection, or when you are using the Magic wand, you can click-and-drag to move the selection and its contents, while the initial position remains empty.

If you only want to move the selection border and not its contents, then press the Alt key and click-and-drag the selection. 


Just clicking-and-dragging moves only the selection, without content. When I was on Feisty this worked fine.

> 
To move a selection and its contents, keep the Alt+Ctrl keys pressed when starting to click-and-drag on the image. For moving a selection without emptying its initial position, press Alt+Shift  instead.


Absolutely no effect! No matter what I press, it just discards the previous selection and makes another one.

Am I missing something?!

Note: I've solved the Alt key issue changing the mouse_button_modifier in metacity to <Super> ( [http://ubuntuforums.org/showthread.php?t=515429]("http://ubuntuforums.org/showthread.php?t=515429") )

---

### Post by smartboyathome on 2007-12-06
Try opening it in a terminal and doing that again, might be a bug that has already been worked out in GIMP 2.4.2.

---

### Post by WhiskeyWulf on 2007-12-06
I'm not sure I get you. You want me to open GIMP from a terminal? OK, I did. There's no output in the terminal when I'm working though, if that's what you're following.
Looks like I'm using ver 2.4.0-rc3
No 2.4.2 in the repository. Should I remove GIMP and install it manually?

---

### Post by smartboyathome on 2007-12-06
You can install the newest gimp from getdeb.net. It should work without much fuss.

---

### Post by WhiskeyWulf on 2007-12-06
Thanks for the site. Didn't know about it. :)
I read the comments and got it installed with sudo dpkg -i *.deb

But I still get the same behavior!!

I tested on 2 machines so I assume it's not the hardware playing tricks. Also searched the forum for hours.

Is this a Gnome problem? Could switching to Kubuntu be a fast solution for this?

---

### Post by WhiskeyWulf on 2007-12-07
Well, I tried Kubuntu and Fedora 8, and it's the same result. Looks like the GIMP team has changed the interface. I hope they'll also update the manual.

---


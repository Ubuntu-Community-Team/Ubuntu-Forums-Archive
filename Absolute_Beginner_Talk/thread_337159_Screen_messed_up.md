---
title: "Screen messed up"
date: 2007-01-12
forum: Absolute Beginner Talk
---

### Post by Krii on 2007-01-12
I installed ubuntu but when I start it whole screen is messed up so bad I cant understand anything and my monitor pops up something like error box saying - not optimal mode. Recommended resolution 1280x1024 60hz. It looks something like this [link](http://foto.apollo.lv/resources/modules/orig_img.php?id=341281)
I have 1280x1024 lcd monitor and gf6600 if that matters. I had the same problem with live cd. What do I do to fix this?


EDITED - I got it working thanks for all the help.

---

### Post by john_spiral on 2007-01-12
Hi

check the below page out:

[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

johne

---

### Post by Krii on 2007-01-12
I tried to run the autodetect script I guess but nothing changed although I'm not sure if I did it right its very hard to do something as my console is also unreadable.

---

### Post by john_spiral on 2007-01-12
choose the text only option when booting, then run the above configuration. 

Come back to us.

---

### Post by Krii on 2007-01-13
I think the problem is with undetected monitor specs. When I open sudo vi /etc/X11/xorg.conf HorizSync and VertRefresh lines has way lower numbers than my monitor supports. I can rewrite the numbers but I don't know how to save the changes. Also if I open sudo nano /etc/X11/xorg.conf it looks like blank file. Theres no text in it... or do I have to do something to see it? Also I'm doing all this in recovery mode as it is the only place where text is readable.

---

### Post by Krii on 2007-01-13
Any help please?

---

### Post by Krii on 2007-01-14
bump

---

### Post by Krii on 2007-01-14
bump...

---

### Post by john_spiral on 2007-01-14
[LIST]
[*]Boot the machine.
[/LIST]

[LIST]
[*]select Ubuntu, kernel 2.6.something-386 (recovery mode) from your grub boot screen as the computer starts.
[/LIST]

will look similar to the following:

[http://www.pcentraide.com/tutoriel/dual-boot/dual-boot-linux-windows-7.jpg](http://www.pcentraide.com/tutoriel/dual-boot/dual-boot-linux-windows-7.jpg)

when you get in run:

sudo su

this will give you root access.

Give nano / vi another try, I'm sure it's just the HorizSync and VertRefresh rates. 

Another option is to get a [Kanotix]("http://kanotix.com/index.php?&newlang=eng") Live CD, boot from it, copy the /etc/X11/xorg.conf file to a floppy/usb key/hard drive/webmail....

Boot ubuntu in recovery mode rename the /etc/X11/xorg.conf file to /etc/X11/xorg.conf.crap and plonk in the above file in it's place.

see what happens.

---


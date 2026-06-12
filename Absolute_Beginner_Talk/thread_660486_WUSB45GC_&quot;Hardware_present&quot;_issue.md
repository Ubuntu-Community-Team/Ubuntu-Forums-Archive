---
title: "WUSB45GC &quot;Hardware present&quot; issue"
date: 2008-01-06
forum: Absolute Beginner Talk
---

### Post by IamJohnHayes on 2008-01-06
So i finally got ndiswrapper to work and let me install my driver for the wifi usb key.  the problem now is that i cant get it to show the hardware being present. 

Im using a Linksys WUSB54GC w/ newest driver i could find from the lynksis site.

I had writen down somewhere how to check my usb ports in the terminal to see whats attached but can't find it.  I am suspecting that it is not on, but am prob. wrong.

Thanks for any help,
John

---

### Post by anewguy on 2008-01-06
To check your USB ports, open a terminal window and type:

lsusb


That should give a list of your USB ports and what is attached.

Please post back when done so we can see if we can get this working for you!:)

---

### Post by IamJohnHayes on 2008-01-06
Bus 005 Device 007: ID 13b1:0020 Linksys 

is what it says along with my usb hd,keyboard, ect.

o and i just realized i put wusb45 instead of 54 in the title, my bad.

---

### Post by anewguy on 2008-01-06
To be sure you have a clean starting point before following the post, use the remove function of ndiswrapper to delete any drivers that show:

sudo ndiswrapper -l    (that's a lower case "L")

if anything is returned:

sudo ndiswrapper -r ??  (where ?? is the name exactly as returned above)

Repeat this until nothing is returned on the list, then follow this post:

[http://jefim.wordpress.com/2007/07/24/how-to-linksys-wusb54gc-wireless-and-ubuntu-linux-704-feisty/]("http://jefim.wordpress.com/2007/07/24/how-to-linksys-wusb54gc-wireless-and-ubuntu-linux-704-feisty/")


If you have any problems/questions after that, post back here and we'll see what we can do to help!:)


EDIT:  Be sure to note that the thread says NOT to use the Windows Vista driver, so if the latest one you downloaded is Vista, go back to just a Windows XP only one.

---

### Post by IamJohnHayes on 2008-01-06
Problem solved thanks

---


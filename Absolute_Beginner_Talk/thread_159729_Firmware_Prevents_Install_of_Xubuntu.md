---
title: "Firmware Prevents Install of Xubuntu"
date: 2006-04-13
forum: Absolute Beginner Talk
---

### Post by Bob B on 2006-04-13
I currently have Kubuntu 5.10 installed on an original G3 Imac, but it is slow and cumbersome to use.  I heard that Xubuntu was designed to work with older computers so I downloaded it and began the install over the Kubuntu 5.10.  Almost immediately I got this message:

"Can't allocate initial device-tree chunk
Apple Imac open Firmware 3.0 f2
built on 04/23/99
Apple Computer Corporation"

There is no longer any Apple software on the computer. How can I get the installer to recognize the Kubuntu and go ahead and make the install?

Bob B

---

### Post by threegremlins on 2006-04-14
unless some one has a work around for your problem you might consider this if your planning to mave to xubuntu. save all your personel files, use the partition manager to remove all the partitions and make new ones, format them and write to disc and make a clean install. if it still doesn't work reinstall kubuntu, all you've lost is time. another option is to install xfce4 or another window manager, when i was running ubuntu breezy i used window maker it was much faster than gnome on my slow box. whatever you use make it the default when you login at the gdm.

---

### Post by Bob B on 2006-04-14
Thanks for the response. When I tried to use apt-get install... it said it could not find package xfce4. I should tell you that since I originally posted I installed Ubuntu server. That is what I tried to install into. Also I am pretty inexperienced at the command line. What would you recommend?

Bob B

---

### Post by xXx 0wn3d xXx on 2006-04-14
[QUOTE=Bob B]Thanks for the response. When I tried to use apt-get install... it said it could not find package xfce4. I should tell you that since I originally posted I installed Ubuntu server. That is what I tried to install into. Also I am pretty inexperienced at the command line. What would you recommend?

Bob B[/QUOTE]
Try:

> sudo apt-get install xubuntu-desktop

---


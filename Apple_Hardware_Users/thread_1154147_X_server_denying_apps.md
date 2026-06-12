---
title: "X server denying apps"
date: 2009-05-09
forum: Apple Hardware Users
---

### Post by linuxuser500 on 2009-05-09
I have a powerbook pismo running ubuntu 8.10 recently upgraded from 8.04. When I upgraded the X server broke and graphical apps stopped working. I fixed the X server but still no graphical apps except occasionally firefox. In the GDM logs there is a lot of:
AUDIT: {insert date+time here}: 4857 X: client 4 rejected from local host ( UID=0 or 1000 gid= 0 or 100 pid=procces id im trying to open)
Auth name: MIT-MAGIC-COOKIE-1 ID: -1

i have a ati rage 128 mobile and ubuntu is the PPC version.

i always hate upgrading distributions...

also i had to compile a custom kernel because 2.6.27 didnt install right but i used factory config so no worries

now im going to do something else while i wait:popcorn::popcorn:

and while im reading this I see there is a new ubuntu. Lets upgrade to that and break the virtual teminals too...

---

### Post by stream303 on 2009-05-09
This sounds like the major problem with Intrepid 8.10 for ppc.  Can you do a fresh install of 9.04?  (having saved your original xorg.conf for reference - it may not work word-for-word, but will be useful)

Intrepid was a pain for many ppc'ers - I usually recommend sticking with 8.04 or trying 9.04....

---

### Post by linuxuser500 on 2009-05-09
Thanks, i was about to do that anyway i was just hesitating because downloading a cd image at 32 KB/s is pretty slow. The thing has been pissing me off for over a week because I have to do everything from the virtual teminals.

---


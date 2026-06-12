---
title: "Nvidia 8800GTX and Ubuntu"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by madlan on 2007-10-24
I tried Ubuntu a while ago, but could not get it to work with my 8800 graphics card, has this been fixed in 7.10? I would love to try ubuntu again!

---

### Post by Pumalite on 2007-10-24
This worked in Feisty. It MIGHT work in Gutsy:

[http://www.ubuntugeek.com/how-to-fix-nvidia-acceleration-in-feisty-nvidia-8800-and-legacy-users.html](http://www.ubuntugeek.com/how-to-fix-nvidia-acceleration-in-feisty-nvidia-8800-and-legacy-users.html)

When grub comes up select the second ubuntu option.

When its finished you should now have a terminal.

login

run sudo passwd

setup your 'root' password

now run

sudo apt-get install nvidia-glx-new

sudo nvidia-xconfig

sudo shutdown -r now

Then use the normal option to boot ubuntu.

Hopefully you'll have an xserver

---

### Post by ericartman on 2007-10-24
Running an 8800 no problems, even set the proper resolution on my 22 inch monitor right
(1680X1050) Using "latest card" Nvidia driver which was a 1 click install after my clean install of Gutsy 
BTW I am using Compiz with all the bells and whistles again no problem. Good luck. 

Cart

Mine is an 8800GTS with 640mb ram, FYI

---

### Post by madlan on 2007-10-24
Did you use the drivers from nvidia? I read they are not needed in this release?
Just the nvidia-glx-new package?

---

### Post by cwestpha on 2007-10-25
I have an 8800GTS with an odd 22" viewsonic LCD that 7.04 never liked to play with. 7.10 works perfectly with it, but if you change anything in xorg.conf or anywhere else it tends to want to die and not recover.
However I cant get to the AA or ANSIO override setting for the new drivers. Anyone know how to get an Nvidia control panel to spawn with the 8x00 series driver so you can set Anti-Aliasing and the like?
Installing it in Apt just results in it wanting to un-install all of the Nvidia drivers.

---


---
title: "cannot log in"
date: 2007-11-03
forum: Absolute Beginner Talk
---

### Post by beanco on 2007-11-03
i get as far as the log in screen and then it goes no further.
 

i mean i type in user name

password

then nothing, just a blank brownish screen. the cursor is there but nothing else.


rather annoying.

what is the solution?

thanks

robi

---

### Post by overdrank on 2007-11-03
> **beanco said:**
> i get as far as the log in screen and then it goes no further.
 

i mean i type in user name

password

then nothing, just a blank brownish screen. the cursor is there but nothing else.


rather annoying.

what is the solution?

thanks

robi

HI could you tell us what is the model of graphics card and which version of Ubuntu you are using Gutsy, Feisty?

---

### Post by beanco on 2007-11-04
I am using feisty..

as to the graphics card, no idea!

I cannot tell by looking in the machine. and i have no idea how to find out....


sorry for being such a dweeb!

robi

---

### Post by beanco on 2007-11-04
looking through other threads i came across several references to xserver.

i tried 

sudo dpkg-reconfigure xserver-xorg

followed by sudo reboot


that did not work

i added -phigh before xserver-org

that did not work.

but I got a message saying that

Setting locale failed

language unset
lc_all unset
lang en_US. iso-8859-1

then lots of stuff and the last line says 

/usr/sbin/dpkg-reconfigure: xserver-org is not installed.

robi

---


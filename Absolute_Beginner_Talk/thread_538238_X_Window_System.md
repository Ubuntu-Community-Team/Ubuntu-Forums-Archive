---
title: "X Window System"
date: 2007-08-29
forum: Absolute Beginner Talk
---

### Post by Antar Bolaeisk on 2007-08-29
Hey Guys and Gals,

New to this whole Ubuntu thing and am really looking forward to getting it up and running on my system unfortunately I've hit a roadblock. Every time I try to run the installation CD to install Ubuntu 7.04 I get an error from the X Window System.

Scrolling down to the bottom of the report I get:

Fatal Server Error
Caught Signal 11. Server Aborting.

Is the CD itself buggered or is there something else wrong here.

I've managed to get Ubuntu 5.1 running on this system before so I kindof assumed that this version would run as well. Would there be any prereqisite that maybe I'm missing.

I'm runing a Dell Inspiron 5160 so not exactly cutting edge hardware or anything but I believe it should be okay.

Would really appreciate some help.

Thanks in Advance,
Antar.

---

### Post by r4ik on 2007-08-29
Try,

sudo dpkg-reconfigure xserver-xorg 

and set it to Vesa.

Good luck !

---

### Post by sumguy231 on 2007-08-29
Have you tried booting the LiveCD in "Safe Graphics Mode"?

---

### Post by Antar Bolaeisk on 2007-08-29
Er... I really am a complete noob when it comes to this stuff so would you mind explaining where exactly I try sudo dpkg-reconfigure xserver-xorg?

Sorry R4ik, the help is appreciated, it just goes over my head a wee bit.

Thanks,
Antar.

---

### Post by Antar Bolaeisk on 2007-08-29
@ Samguy231

Yep, tried that right after the install didn't work and ended up getting the exact same error.

Thanks,
Antar.

---

### Post by r4ik on 2007-08-29
> **Antar Bolaeisk said:**
> Er... I really am a complete noob when it comes to this stuff so would you mind explaining where exactly I try sudo dpkg-reconfigure xserver-xorg?

Sorry R4ik, the help is appreciated, it just goes over my head a wee bit.

Thanks,
Antar.

Applications =>Accessories =>Terminal.
Copy and paste    sudo dpkg-reconfigure xserver-xorg 
Follow the defaults and set you're graphic driver to Vesa

---

### Post by Antar Bolaeisk on 2007-08-29
Okay. I get you now, I was trying to find a place I could type it in during the install. Didn't think of doing it through the previous installation.

Thanks R4ik, will let you know how I get on.

Antar.

---

### Post by r4ik on 2007-08-29
If Vesa does not work try "nv"
Xuse me for the messed up post :)

---

### Post by r4ik on 2007-08-29
I should learn to read you probably never going to make it to the graphic interface.
If you end up in a black screen log in in with you're user name and password and try the same.

Good luck !

---

### Post by sumguy231 on 2007-08-29
There shouldn't be a password on the LiveCD, if I remember correctly the username is Ubuntu and there is no password. The problem with that is that I'm not how limited that account is.

---

### Post by nonewmsgs on 2007-08-29
it's an account with very strong privlidiges.

---


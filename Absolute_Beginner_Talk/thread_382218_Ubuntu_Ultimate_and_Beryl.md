---
title: "Ubuntu Ultimate and Beryl"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by delphiguy on 2007-03-11
Cheers,

I downloaded Ubuntu Ultimate 1.2 a couple of weeks ago, and just now decided to install it on my system.  One of the things that I liked about this is that it came with Beryl, however Beryl doesnt seem to work, at least not on my machine.

When I ran Beryl Manager, both from the menu and the terminal, it seems to restart X and goes back to the login screen, and when I log in I dont get any Window Decorations (Title Bars, borders, etc..) on my apps.

When I typed "beryl" on the terminal I get this.

**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Checking for non power of two texture support   : passed
Checking maximum texture size                   : passed (2048x2048)

Reloading options


Do I still have to do additional steps for beryl to work in Ubuntu Ultimate?

Thanks.

---

### Post by jm_biohazard on 2007-03-13
Have you got your video card's drivers installed?
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#Eye_Candy]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#Eye_Candy")
The ATI and NVIDIA guides are there

I hope this helps

---

### Post by chuckyp on 2007-03-13
You also might want ask the ubuntu ultimate people for help.  Since your distro is not the same.

---

### Post by CyBuzz on 2007-03-14
I had some of the same issues (I am using UUE 1.2 also).  I had forked with numerous settings without knowing what I was doing so I 
1.  reinstalled from scratch
2.  downloaded envy
3.  ran beryl manager

and it worked.  

I use an nvidia card and ran into the no title bars and the black window issues, but they have been fixed via guidance from these wonderful forums.

---


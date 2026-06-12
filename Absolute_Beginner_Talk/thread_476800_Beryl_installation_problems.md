---
title: "Beryl installation problems"
date: 2007-06-17
forum: Absolute Beginner Talk
---

### Post by pardesi on 2007-06-17
when i installed beryl and was doing system settings i got thsi what does this mean

```
pardesi@pardesi-desktop:~$ Xlib:  extension "XFree86-DRI" missing on display ":0.0".
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
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
Checking for non power of two texture support   : failed

Support for non power of two textures missing
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
beryl: Support for non power of two textures missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :0.0
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"

```

---

### Post by quinnten83 on 2007-06-17
Hi Pardesi, 
I can't help you, 'cause i don't know the answer. But it might be a good idea if you posted what type of graphics card you're using.
I have an older pc running a matrox card and it also gave me a similar error message.
it could be that your card can't handle beryl as a windows manager.

---

### Post by pardesi on 2007-06-17
i have  ATI radeon 200 xseries

---

### Post by pardesi on 2007-06-18
someone please ...can u tell me how do i proceed i am noob to thsi and amazed by bryl....

---

### Post by neo.patrix on 2007-06-18
Hi Pardesi,

I have ATI X1300,  Beryl works cosdierably well, but setting up Beryl is not easy.

First of all , it would be good if you can post output of fglrxinfo. I presume that
it should show something similar to following

```


display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1300
OpenGL version string: 2.0.6334 (8.34.8)


```

Make sure you have installed proper ATI dirver from ubuntu-feisty repo. You can check from
System-->Administration-->Restricted Driver Manager, "ATI accelerated Graphics Driver" should be "in use".

Second thing you need functionaly [COLOR="Black"]**XGL Server**[/COLOR]. It would be better if you strictly follow one of the following links,

[https://help.ubuntu.com/community/CompositeManager/Xgl](https://help.ubuntu.com/community/CompositeManager/Xgl) or
[http://www.kittypee.com/2007/05/07/desktop-effects-on-ubuntu-feisty-ati-beryl/](http://www.kittypee.com/2007/05/07/desktop-effects-on-ubuntu-feisty-ati-beryl/)

But it is not yet stable enough and using Beryl-Manager is also no piece of cake.

---

### Post by ruddin on 2007-09-21
i have used a software called.....WUBI...to install ubuntu on my computer.....now i have dual boot oses....on my comp...wubi has given a virtual drive for ubuntu...but i tried BERYL or COMPIZ n it doesnt work on my comp....shud i install ubuntu by partitioning my hard drive...or will wubi be able to make beryl work....i knw beryl leads to many crashes...but it has worked on my friends comp n i want to try it out....

---

### Post by ruddin on 2007-09-21
i m using amd athlon....n i dont knw abt the graphic cards installed or the drivers...n m new to ubuntu....ppl help!!!

---

### Post by overdrank on 2007-09-21
> **ruddin said:**
> i m using amd athlon....n i dont knw abt the graphic cards installed or the drivers...n m new to ubuntu....ppl help!!!

Hi take a lot at this link
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#Compiz_.2F_Desktop_Effects](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Compiz_.2F_Desktop_Effects)

---

### Post by EowynCarter on 2007-09-22
I have a X1300 and using flgx

and beryl won't work.
I don't really wanna risk crashing everything... 

I think i need to do that.
[https://help.ubuntu.com/community/CompositeManager/Xgl](https://help.ubuntu.com/community/CompositeManager/Xgl)
But it seams more trouble than it's worth right ?

---


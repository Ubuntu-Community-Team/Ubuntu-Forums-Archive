---
title: "Desktop Effects and white screen??"
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by y-lee on 2007-06-12
I installed Ubuntu 7.04 on a friends machine. When i try desktop effects the screen goes white sometimes for a second sometimes untill i power down and reboot. The machine was custom built but it has a (Elitegroup) ECS P4M900T-M 1066MHz Mother board (FSB Support) with an integrated 64 MB SIS 3-D on board accelerator Video card. Is this video card properly supported for desktop effects and can this problem be fixed? if so how?

---

### Post by pardesi on 2007-06-12
see here [http://ubuntuforums.org/showthread.php?t=471638](http://ubuntuforums.org/showthread.php?t=471638)

---

### Post by joselin on 2007-06-12
Not sure, but i think that only works fine with nvidia, intel and ati cards.

But try to locate more info on [compiz homepage]("http://www.compiz.org/") or try on [their forums]("http://forum.compiz.org/").

Regards.

---

### Post by y-lee on 2007-06-12
> **pardesi said:**
> see here [http://ubuntuforums.org/showthread.php?t=471638](http://ubuntuforums.org/showthread.php?t=471638)
Not much there that helps me, but heres the output of the glxinfo command 

> user@Ubuntudesktop:~$ glxinfo | head
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  142 (GLX)
  Minor opcode of failed request:  3 (X_GLXCreateContext)
  Serial number of failed request:  16
  Current serial number in output stream:  17
name of display: :0.0

Is it true that the desktop effects that only works fine with nvidia, intel and ati cards? And if so why does ubuntu not recognize my video card properly and give me the white screen when I try the desktop effects?

---

### Post by lifemaximum on 2007-06-13
Hi 

I have a problem with Desktop effect too but it is different, I get to run it and it works, but every time i enable it the window bar, the one which lets you close or minimize and maximize the window disappears and i can't move the windows, as soon as i disable the desktop effect it works fine?

is there any fix for that?

---

### Post by Kelvin_lobo88 on 2007-06-13
I am having a problem too with the 3D desktop effects. I am using Ubuntu Feisty Fawn 7.04. I have an ATI RADEON XPRESS 200M graphics card. I enabled 3D acceleration on it but it says it does not have the composite extension. If i try with 2D, it gives me a blank White Screen. Can anybody help at all ??

---

### Post by zalberico on 2007-06-13
The Desktop effects do some weird things.  I've installed ubuntu feisty on five computers, and on my apple powerbook there is a white screen (because there is no ppc Nvidia driver)  and on other computers with only integrated graphics it shows up right away, but on two of these the cube didn't appear when it was supposed to, the tool bars disappeared and after turning desktop affects on and off several times and messing with the amount of virtual desktops I got the cube working, but who knows when it will stop again.  

      In short I think that there are a lot of problems with desktop effects and your white screen may be due to the fact that you don't have the restricted drivers installed, or they were installed incorrectly.  If you do get it up and running I've found that the wobbly windows work flawlessly but the cube works only occasionally. 

Sorry I couldn't be of more help
zman

---


---
title: "Instal nVidia-GLX-new on 64bit C2D PC with Gutsy"
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by corowakid on 2007-10-25
I've recently purchased a new PC, 2.33 Core2Duo with Asus P5GC-MX moboard and nVidia 7300GS video card.

I installed Gutsy 7.10 64bit version today, and everything has worked so far. Downloaded additional software etc, used the 'Net all with no problems.

However, when I attempt to access the additional video effects I get the message to "Enable restricted drivers". When I click on the radio button I get the message "nVidia-GLX-New drivers not installed".

Can anyone tell me how to get the restricted drivers installed please? I assume if that can be accomplished, I'll be able to Enable the additional video effects (I assume this is Compiz(?))

Any help really appreciated

---

### Post by Skweek on 2007-10-25
I think you can do this by simply opening up Restricted Drivers manager and enabling the nVidia drivers, followed by a reboot.

---

### Post by jenhsun on 2007-10-25
> **corowakid said:**
> I've recently purchased a new PC, 2.33 Core2Duo with Asus P5GC-MX moboard and nVidia 7300GS video card.

I installed Gutsy 7.10 64bit version today, and everything has worked so far. Downloaded additional software etc, used the 'Net all with no problems.

However, when I attempt to access the additional video effects I get the message to "Enable restricted drivers". When I click on the radio button I get the message "nVidia-GLX-New drivers not installed".

Can anyone tell me how to get the restricted drivers installed please? I assume if that can be accomplished, I'll be able to Enable the additional video effects (I assume this is Compiz(?))

Any help really appreciated

When you click the button it supposed to download the driver and install for you, is that right?
If you want to play with compiz, here you might want to take a look.
[https://help.ubuntu.com/community/CompositeManager/CompizFusion](https://help.ubuntu.com/community/CompositeManager/CompizFusion)

---

### Post by corowakid on 2007-10-25
> **Skweek said:**
> I think you can do this by simply opening up Restricted Drivers manager and enabling the nVidia drivers, followed by a reboot.

That's part of the problem. The Restricted Drivers Manager is not a menu item in the 64bit version of 7.10. I used Synaptic and found 3 references to nVidia drivers, but each of them replied that "the software won't download to your computer due to the mfr. not making them available" or words to that effect.

I used the 32bit download of 7.10 and installed it on a P4 2.8 Celeron machine, with an inferior video card, and Compiz runs on that machine!, even the wobbly windows effect.

I'd appreciate it if anyone know whether the 64bit version allows for the use of Compiz, or whether I'm locked out. Thanks

---

### Post by Qwerty_ on 2007-10-25
I wonder if this might work for you.
[http://ubuntuguide.org/wiki/Ubuntu:Gutsy#NVidia_Driver](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#NVidia_Driver)

---

### Post by RomeReactor on 2007-10-25
Hi. I'm also running Gutsy 64-bit, and the restricted drivers manager is located in "System->Administration->Restricted Drivers Manager". It *should* be there in your menus.

Also:
> I used Synaptic and found 3 references to nVidia drivers, but each of them replied that "the software won't download to your computer due to the mfr. not making them available" or words to that effect.
This is starting to look like an increasingly common problem...

---

### Post by jenhsun on 2007-10-25
> **corowakid said:**
> That's part of the problem. The Restricted Drivers Manager is not a menu item in the 64bit version of 7.10. I used Synaptic and found 3 references to nVidia drivers, but each of them replied that "the software won't download to your computer due to the mfr. not making them available" or words to that effect.

I used the 32bit download of 7.10 and installed it on a P4 2.8 Celeron machine, with an inferior video card, and Compiz runs on that machine!, even the wobbly windows effect.

I'd appreciate it if anyone know whether the 64bit version allows for the use of Compiz, or whether I'm locked out. Thanks

Wrong. it is in the menu. 
If you want to know how to use compiz, see above links that I posted.

---

### Post by corowakid on 2007-10-25
> **Qwerty_ said:**
> I wonder if this might work for you.
[http://ubuntuguide.org/wiki/Ubuntu:Gutsy#NVidia_Driver](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#NVidia_Driver)

Thanks for that - unfortunately I ran the instructions in terminal as shown, and got the response that the module was already installed, and was the latest version.

I went to System>Admin>Restricted Driver Manager, went to the nVidia entries and got ""nviidia-glx-new is not enabled". I can't find the module "nvidia-glx-new", altho I remember seeing it when I was using 7.04.

I then went to Add/Remove programs, attempted to load any of the 3 nvidia driver modules and got the following report for each  "the mfr hasn't made the module available for your machine (AMD64).

Given all this, has anyone got any suggestions of a) where I'm going wrong, b) how do I get the module(s) loaded.

I'm prepared to forego the Compiz specials if need be, altho the reason I bought my Core2Duo system was to provide plent of grunt for Ubuntu, and the 7300GS card has the capacity to run the Compiz graphics.

Appreciate any suggestions

---

### Post by jenhsun on 2007-10-25
> **corowakid said:**
> Thanks for that - unfortunately I ran the instructions in terminal as shown, and got the response that the module was already installed, and was the latest version.

I went to System>Admin>Restricted Driver Manager, went to the nVidia entries and got ""nviidia-glx-new is not enabled". I can't find the module "nvidia-glx-new", altho I remember seeing it when I was using 7.04.

I then went to Add/Remove programs, attempted to load any of the 3 nvidia driver modules and got the following report for each  "the mfr hasn't made the module available for your machine (AMD64).

Given all this, has anyone got any suggestions of a) where I'm going wrong, b) how do I get the module(s) loaded.

I'm prepared to forego the Compiz specials if need be, altho the reason I bought my Core2Duo system was to provide plent of grunt for Ubuntu, and the 7300GS card has the capacity to run the Compiz graphics.

Appreciate any suggestions

Try this
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---


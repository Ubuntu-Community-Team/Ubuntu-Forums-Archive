---
title: "Desk top effects please help"
date: 2007-11-09
forum: Absolute Beginner Talk
---

### Post by armitage shanks on 2007-11-09
I have a dell gx 150 with intel 82815 graphics card in it plus pentium thre chip. Desktop effects are not working, has anyone any idea why. Plus I have read that they may do if the coulour settings are reduced to 16 bit but I cannot figue out how to do it. Please help I have a class full of children waiting to see them working.
ta in advance

---

### Post by bigstoo on 2007-11-09
IIRC, the GX150 isn't capable of running in 3D mode - and so desktop effects won't work.

Also, I think the maximum number of colours it can use is 16bit.

---

### Post by TadH on 2007-11-09
unfortunately I dont think its compatible.

---

### Post by Da King on 2007-11-09
I am having the same problem with my Compaq DESKPRO EN.
 
Spec:   Processor - 996MHZ
           OS - Ubuntu 7.10 Gusty
            RAM - 512mb
           VGA CARD  - Intel 82815 Graphic (32mb Ram)
       
My problem we have almost 12 same machine of the same spec using win XP which support 3D mode. i tried the destop effects and it say it cant work..something about XGL..so i went to compiz in the terminal and this is what i get..Can anyone help me with it plsss..im totally new to all this and im making every effort to learn about it. 

code:
> 
king@King:~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:1132 (rev 04) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x960) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting emerald
/usr/bin/compiz.real (core) - Fatal: No GLXFBConfig for default depth, this isn't going to work.
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0

u can msg me on yahoo msnger (lill_kings) or email me the help (webbwoi@yahoo,com

Thanks a lot in advance.

---

### Post by dhobbs on 2007-11-09
If your video card can't handle 3D acceleration then you can't have Desktop Effects.

---

### Post by jchaike on 2007-11-09
ive got an ATI RADEON X1300, and I don't know for sure, but I am running the LiveCD now, just to test things out, and the effects wont work on my computer. I am not sure if this is just because some things on the LiveCD are just not 100% working until you install it to your harddrive, or if I need correct drivers

please respond quickly as I am eager to get Ubuntu working at its fullest...

Thanks :)

---

### Post by Dr Small on 2007-11-09
> **jchaike said:**
> ive got an ATI RADEON X1300, and I don't know for sure, but I am running the LiveCD now, just to test things out, and the effects wont work on my computer. I am not sure if this is just because some things on the LiveCD are just not 100% working until you install it to your harddrive, or if I need correct drivers

please respond quickly as I am eager to get Ubuntu working at its fullest...

Thanks :)
I think (because I haven't tried Gutsy without VirtualBox, yet) that you need to install drivers to get the Desktop Effects to work, which, you can not do on a Livecd, because you have to reboot. If you reboot, you lose it all....

Dr Small

---

### Post by Da King on 2007-11-09
Well my card supports 3D cos i was using xp at first and had 3D capabilties when i checked with directX. i have also play quite a lot of game of it like Max payne, NFS hot pursuit, GTA vice city...etc etc..so why i am still having problems with compiz...i always get the error XGL not present..what does that mean, i checked the synaptic manager and i think i have compiz installed otherwise can anyone with the same INTEL 82815 graphic card who has got the beryl or compiz working give me the configs. thanks a lot in advance.

---

### Post by Badjaccur on 2008-01-07
It should be possible. I found this list on a Gentoo page and saw the 82815 sitting there:

[B]Intel
[/B]
    * Intel 815GM
          o Chipset: Intel Corporation 82815/815GM Integrated Grapics Device
          o Driver: Latest snapshots and MESA DRI drivers (new stuff added that was missing to make it work)
          o Notes: Black windows. Compiz and Xgl work though and are accelerated. (Cube rotates! Black faces...)

---

### Post by cartisdm on 2008-01-07
> **jchaike said:**
> ive got an ATI RADEON X1300, and I don't know for sure, but I am running the LiveCD now, just to test things out, and the effects wont work on my computer. I am not sure if this is just because some things on the LiveCD are just not 100% working until you install it to your harddrive, or if I need correct drivers

please respond quickly as I am eager to get Ubuntu working at its fullest...

Thanks :)


I have the mobility x1400 and once the correct drivers will installed all the effects worked smoothly so I think you should be alright

---

### Post by ryseshan on 2008-05-28
I have Intel 810 Chipset Motherboard and Monitor is Samtron 45Bn.  With Gutsy it worked fine and no problem.  Yesterday 28th May 2008, I have updated my Ubuntu with Hardy 8.04 my Display where ever the mouse is moved there a patch is appearing and also very slow. My Monitor doesnt support Desktop effects I want it to be disable it. How to disable desktop effects and define my Monitor type. Please give me a quick response.

---

### Post by _DD_ on 2008-05-29
> **jchaike said:**
> ive got an ATI RADEON X1300, and I don't know for sure, but I am running the LiveCD now, just to test things out, and the effects wont work on my computer. I am not sure if this is just because some things on the LiveCD are just not 100% working until you install it to your harddrive, or if I need correct drivers

please respond quickly as I am eager to get Ubuntu working at its fullest...

Thanks :)
For 3D acceleration you have to enable the ATI driver, but you can't do this on the live CD (well, its not impossible if you use Ctrl+Alt+Backspace to restart X rather than rebooting, but it would be pretty pointless!).

There should be no reason why you wouldn't be able to use them if you installed it :D

---


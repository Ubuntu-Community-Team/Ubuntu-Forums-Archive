---
title: "application is dumping"
date: 2006-05-05
forum: Absolute Beginner Talk
---

### Post by cl3ellio on 2006-05-05
I'm trying to use a geometry visualization software called geomview and it keeps core dumping on me. I installed geomview with the files from the ubuntu repository so I'm puzzled as to why it isn't workiing. When I run it the windows pop up normally but the following messages are displayed on the terminal:

$ geomview
libGL warning: 3D driver claims to not support visual 0x24
libGL warning: 3D driver claims to not support visual 0x28
libGL warning: 3D driver claims to not support visual 0x2c
libGL warning: 3D driver claims to not support visual 0x30

The when I try and load a file it freezes up and I get a core dump. I'm wondering what I can do to resolve those warnings. Thanks!

---

### Post by ComplexNumber on 2006-05-05
i may be wrong, but it could be that you need to update to the latest drivers for your graphics card. before you do, probably best let others have a read first and see what they have to say. i've just updated my kernel and graphics driver myself. its really easy to do if it works out that thats the solution to your problem.

just curious, but fire up the command line and type in 'glxgears'(either that, or 'gxlgears'). how many fps are you getting on average?

---

### Post by cl3ellio on 2006-05-05
Well my graphics card is an ATI Rage 128 RF/SG AGP. When I run glxgears I get a similar output to geomview:

glxgears
libGL warning: 3D driver claims to not support visual 0x24
libGL warning: 3D driver claims to not support visual 0x28
libGL warning: 3D driver claims to not support visual 0x2c
libGL warning: 3D driver claims to not support visual 0x30
Illegal instruction

Would I update my kernel through synaptic or going to the ATI webpage?

Thanks.

---

### Post by ComplexNumber on 2006-05-05
i updated my kernel the other day by:
-downloading the kernel and placing it in my home directory
-uninstalling all the kernel components (eg kernel-devel, etc) EXCEPT the kernel itself (ie that package that says kernel-2.6.XX_Y.PPPP (or something like that))
-logging out and going into terminal failsafe via the log in manager (there should be an option for terminal Failsafe)
-updating my kernel using the command 'rpm -Uvh 2.6.16*'(do not use the rpm command because it won't work on ubuntu. my system is fedora core 5, so its rpm based rather than deb based, which is what ubunutu is). i don't know what the command to run on ubuntu is. i think it will probably be somnething like apt-get update kernel or something. someone else more familiar with ubunutu and debian can advise you here.
-rebooted.
going into failsafe terminal may not be necessary to update the kernel only, but because i updated my graphics drivers at the same time, i **HAD TO** go into Terminal failsafe because its highly unwise to uninstall the old graphics drivers and then update the graphics driver whilst still using the X server(ie when you use a graphical environment such as gnome or a window manager). it won't do any harm, though, to update the kernel in failsafe.

when i started out updating my kernel and graphics driver the other day, it was the first time ever, so i was thinking "oh hell" i bet any money i mess up here" because i really didn't know what i was doing. i had a rough idea, but i followed some tips, and it went surprisingly smoothly and totally painlessly. in fact, there was nothing to it. i have seen guides on this forum and others that provide masses of unecessary instructions. its actually really straightforward, quick, and easy.

---

### Post by cl3ellio on 2006-05-05
I think my kernel is up to date, so I'm pretty sure its the drivers. The ATI webpage directs me to the DRI project. Is there any in the ubuntu repository for my drivers? The DRI installation looks pretty involved (CVS stuff I haven't dealt with before). Anybody gone through this on unbuntu before? Thanks for the insight!

---

### Post by ComplexNumber on 2006-05-05
i think the latest kernel is 2.6.16_X.2080 (or something like that. the "2.6.16" bit and the "2080" bit are correct). thats the one i updated to.
when selecting that latest driver, take note of the kernel number because i read that they have to match.

its probably not directly relavant to you, but i think it still could be helpful for you to know how i went about it on fedora just in case you could learn anything from it :). it may well be similar, but not identical. 
in fedora, i had to get the latest drivers from lvna repositories rather than nvidia website, but i think that ubuntu is ok with users using the latest driver from nvidia or ati. in that case, its just a case of:
-download the latest driver from ati website. 
-go into Terminal failsafe (this is important)
-on the command line, cd to the directory and execute it.
-reboot

---

### Post by cl3ellio on 2006-05-05
Looking on the ATI website it seems they leave it to 3rd party developers for their linux drivers. When I look at the pdf with the Support Chart there is no mention of Ubuntu, there is however mention of Debian 3.0r5. It states I should have the following:

X.Org 6.8.2
XFree86 4.1.0, 4.2.0 and 4.3.0

When I look in Synaptic to see what packages I have here are the versions:

xorg-common 6.8.2-77 (That should be okay)
libXxf86vm 7.0.0-2
libXxf86misc 7.0.0-2
libXxf86dga 7.0.0-3

Why do those libraries have such a high version? Am I looking at the wrong packages? They seem like the relevant ones when I search 'xfree' in Synaptic. I'm really confused by the graphics drivers.

---


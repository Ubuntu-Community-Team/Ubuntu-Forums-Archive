---
title: "Xubuntu + Compiz = Somethings missing"
date: 2007-12-05
forum: Absolute Beginner Talk
---

### Post by apauloisdead on 2007-12-05
I've had compiz work for me before in xubuntu, but it was when i added xubuntu-desktop on top of ubuntu gutsy. 

I don't want all the extra clutter, and since i just prefer xubuntu i did a clean live cd install.

i installed compiz, emerald and such, but when i run compiz --replace i get this:



me@vaio:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:27a2 (rev 03) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting emerald
/usr/bin/compiz.real (core) - Fatal: No GLXFBConfig for default depth, this isn't going to work.
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0
exec: 378: /usr/bin/metacity: not found


I forget how to view my xorg file, so if someone can tell me how ill post it. My graphics card is intel 945gm express.


It says xgl isnt present, but i also read somewhere that there is something better than xgl for my graphics card. 

I obviously have no idea what i'm talking about so ill let the experts talk.

---

### Post by ItsMitsHere on 2007-12-05
No body is expert except those who codes the programs for us!

As for your problem, u can open xorg.conf by typing **sudo gedit /etc/X11/xorg.conf**.

aiglx is better then xgl according to some.

you may want to run compiz --replace at startup, in which case go to system>session manager and add compiz --replace as a startup string (it's not exactly that but simple enough so you will do it). You may also try indirect rendering from terminal by render --indirect (i'm not sure about this too ;))

---

### Post by EeePc on 2008-03-30
I am trying to install compiz on my Eee PC running Xubuntu. 
i installed compiz, emerald and such, but when i run compiz --replace i get this:

clm@EeepBeep:~$ compiz --replace
Checking for Xgl: not present.
Detected PCI ID for VGA: 00:02.0 0300: 8086:2592 (rev 04) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present.
Checking for non power of two support: present.
Checking for Composite extension: not present.
aborting and using fallback: /usr/bin/metacity
no /usr/bin/metacity found, exiting


Thanks,

Lost and Frustrated

---

### Post by Bittermormon on 2008-04-02
I used [this guide]("http://wiki.eeeuser.com/ubuntu:eeexubuntu:customization#enabling_compiz-fusion_desktop") at the most excellent EeeUser Wiki to install compiz to my eeeXubuntu install and it went off without a hitch. Hope this helps.

---


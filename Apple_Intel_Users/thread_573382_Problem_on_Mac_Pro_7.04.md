---
title: "Problem on Mac Pro: 7.04"
date: 2007-10-11
forum: Apple Intel Users
---

### Post by jamieno10 on 2007-10-11
Hi,

I'm new to linux/ubuntu. 

I just got an 8-core mac pro with 4 HD and the pioneer drive today and tried to install ubuntu 7.04 on it.

I had installed bootcamp and rEFIt. Then tried to install ubuntu; booting was no problem after I changed the display option at the menu (F4) to anything other than VGA. Installation was fine too.

Ubuntu then prompts for removal of CD and to press 'enter', pressing enter has no effect. after a hard reset, rEFIt shows a 'boot linux from HD' option, but selecting that ultimately gives a black screen.

I tried both installing over the HD with OS X (but somehow it still remains!) and on one of my 3 other HD.

Has anyone with an 8-core successfully installed ubuntu?

I woulld really appreciate some help! Thanks!

---

### Post by cyberdork33 on 2007-10-11
when you get to your black screen, do you not see anything at all?

---

### Post by jamieno10 on 2007-10-11
Sometimes nothing, most times I see just see a "_".

---

### Post by cyberdork33 on 2007-10-11
hmm... can you try doing CTRL+ALT+F2 to see if you can bring up a console?

---

### Post by jamieno10 on 2007-10-11
Thanks.

I just tried it. No effect. rEFIt loads, selects linux, long pause (white screen) then becomes black, flickering underscore, ctl-alt-F2 has no effect

I had been using the ubuntu partitioning manger during the install, is that a problem?

Is there some way of making ubuntu the only OS? I tried to install it over the HD with mac OS and yet it still exists and is bootable.

Since this computer is new, I have no data to lose.

---

### Post by cyberdork33 on 2007-10-11
> **jamieno10 said:**
> Thanks.

I just tried it. No effect. rEFIt loads, selects linux, long pause (white screen) then becomes black, flickering underscore, ctl-alt-F2 has no effect

I had been using the ubuntu partitioning manger during the install, is that a problem?

Is there some way of making ubuntu the only OS? I tried to install it over the HD with mac OS and yet it still exists and is bootable.

Since this computer is new, I have no data to lose.
Yes, you should be able to use the installer to take over the entire disk. You won't be able to update firmware without OSX though. Maybe you installed Ubuntu to a drive other than the one with OSX on it?

---

### Post by jamieno10 on 2007-10-11
I managed to install Ubuntu without OS X.

Installs fine if I select a non-VGA option (F4) at the startup menu.

Upon restarting, GRUB boots up fine and I can select which kernal to boot up. Problems then start appearing:

1. A message appears saying something about PCI 600 not in headers, but ubuntu continues to load nevertheless

2. I can see the ubuntu logo and the orange progress bar, but the screen gets garbled after that. I see the same thing if I try to select VGA (F4) at the startup menu when installing.

Is it a driver incompatability issue? Are there any workarounds?

My graphics card is a Nvida Geforce 7300

Thanks again.

---

### Post by cyberdork33 on 2007-10-11
> **jamieno10 said:**
> I managed to install Ubuntu without OS X.

Installs fine if I select a non-VGA option (F4) at the startup menu.

Upon restarting, GRUB boots up fine and I can select which kernal to boot up. Problems then start appearing:

1. A message appears saying something about PCI 600 not in headers, but ubuntu continues to load nevertheless

2. I can see the ubuntu logo and the orange progress bar, but the screen gets garbled after that. I see the same thing if I try to select VGA (F4) at the startup menu when installing.

Is it a driver incompatability issue? Are there any workarounds?

My graphics card is a Nvida Geforce 7300

Thanks again.

if it is a graphics driver issue, you should be able to CTRL+ALT+F1(or F2, etc) to get a commandline. Then you can try to use the vesa driver or download the binary proprietary nvidia driver.

I would try the vesa driver first:
do ```
sudo nano /etc/X11/xorg.conf
```
find the driver line (likely set to nv currently) and change it to vesa.
Save and exit, then do
```
 sudo /etc/init.d/gdm restart
```

Hopefully that will get some visuals and you can then install the proprietary driver via the normal methods.

---

### Post by jamieno10 on 2007-10-12
With 7.04, I am not sure if I can get a terminal, but if I use a non-VGA option to get into the GUI and look at xorg.conf, I see vesa already as the driver.

With 7.10rc, I still get the garbled screen (even if I use a non-VGA option at the menu), but I am definately able to get a terminal with CTRL-ALT-F1, but with a black screen decorated with white vertical white lines; I can see fragments of letters lke Ub-n-t- here and there. So its difficult to edit anything in command line.

I then connected via the mac dvi/rgb connector to another monitor and this time I do not see a garbled screen, Ubuntu runs as it does with the apple cinema display, but, the monitor switches off.  

Alll in all, while there might be some driver problems, it seems that the fact that the monitor is ultimately connected via a dvi port is a cause?

Thanks for your hints thus far, I would really appreciate any help you could give me.

---

### Post by jamieno10 on 2007-10-12
Is there anyway to install ubuntu with a pre-configred xorg? I would like to try that with various options suggested for the dvi monitors.

---

### Post by jamieno10 on 2007-10-15
I've somehow managed to install ubuntu now.

I installed rEFIt and left it there and somehow everything works (7.10rc), not sure why.

Thanks for your help thus far.

---


---
title: "no desktop effects"
date: 2008-03-18
forum: Absolute Beginner Talk
---

### Post by stonecoldjha on 2008-03-18
i cant enable desktop effects on my ubuntu7.10.i have downloaded all updates,including compiz,but it doesn't.well,lemme tell you that this is for the third time that i installed ubuntu on my PC.everytime it was problematic .last time i made a few modifications in some files from the terminal as told here,but then after reboot ubuntu occupied only a fraction of my screen,with the remaining portion undisplayed.i tried enabling the deskop effects and then they worked,but it literally made my system too slow,scrolling,selecting things and many others became much slower,even though i have a RAM of 1 GB,and an intel core2duo 2 GHz processor.please help as i am fed up with windows,and want to switch entirely to linux.

---

### Post by taurus on 2008-03-18
What graphic card do you have and have you installed a driver for it?  Look in System -> Administration -> Restricted Drivers Manager and see if your graphic card is on the list.

---

### Post by lavinog on 2008-03-18
I think the ATI restricted driver might still be problematic with compiz...the current driver that ATI offers works with no problems.
also if you did an upgrade make sure you are not using xgl anymore

---

### Post by stonecoldjha on 2008-03-18
how do i check as to which graphics card and driver i have?

---

### Post by Ub1476 on 2008-03-18
Post the output of:

```
lspci | grep VGA
```

If you haven't installed any driver yourself, you're using the open-source ATI/Radeon driver.

---

### Post by stonecoldjha on 2008-03-18
i had the following terminal output:
[B][SIZE="2"]sonu@sonu-desktop:~$ lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation 82945G/GZ Integrated Graphics Controller (rev 02)
sonu@sonu-desktop:~$ [/SIZE][/B]
what should i do next?

---

### Post by Ub1476 on 2008-03-18
What driver is set in System>Administration>Screens and graphics?

Is the package xserver-xorg-video-intel installed?

```
sudo apt-get install xserver-xorg-video-intel
```

The i810 driver (probably need to be installed from Synaptic) migth solve your issue, but always "test" the driver before you apply it!

---

### Post by ubuntu-freak on 2008-03-18
I think your Intel chipset is still blacklisted, you can enable effects, but you will have video playback issues. It's worth waiting until your chipset is supported properly.
 
Nathan 
 
P.S. If you want to experiment with desktop effects, paste this into the Terminal;
 
**SKIP_CHECKS=yes compiz --replace**

---

### Post by stonecoldjha on 2008-03-18
yea it seems that chipset is blacklisted as the output of my terminal read:
[B][SIZE="2"]sonu@sonu-desktop:~$ SKIP_CHECKS=yes compiz --replace
Checking for Xgl: not present. 
No whitelisted driver found
SKIP_CHECKS is yes, so continuing despite problems.
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1024x768) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (core) - Fatal: No GLXFBConfig for default depth, this isn't going to work.
/usr/bin/compiz.real (core) - Error: Failed to manage screen: 0
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0
[/SIZE][/B]
OK,its worth waiting to get support for chipset,but in the meantime will i have to carry on with crummy brown looks,devoid of any modern desktop effects.i switched to ubuntu7.10 with high expectations that went way nullified,i mean i have been a windows user ,and had been running xp of late which didn't have trouble installing some really exquisite effects as i installed vista transformation pack,on the same hardware configuration.but now that i lacerate windows a lot for it being prone to infections and all such things,frequent program crashes and all that,i decided to switch to something i still believe is better.i know ubuntu is highly customisable ,but how can i be helped...............am i left with the only option to wait.i have been facing a hell lot of problems,no splash screen,failure to install dock,no desktop effects,bizzare brown looks that i don't find captivating,though i am sure they will be one day.i can't even play videos on the web despite having  installed flash several times in the terminal.............please do reply............and help me become a part of this linux community......help me solve all this.

---

### Post by ubuntu-freak on 2008-03-18
When did you install Ubuntu? 
 
Did you install starupmanager? I posted that in your other thread.
 
Also, have a look at my [how-to](http://ubuntuforums.org/showthread.php?t=661833) regarding multimedia and more.
 
Nathan

---

### Post by dinht293 on 2008-03-18
> **stonecoldjha said:**
> i cant enable desktop effects on my ubuntu7.10.i have downloaded all updates,including compiz,but it doesn't.well,lemme tell you that this is for the third time that i installed ubuntu on my PC.everytime it was problematic .last time i made a few modifications in some files from the terminal as told here,but then after reboot ubuntu occupied only a fraction of my screen,with the remaining portion undisplayed.i tried enabling the deskop effects and then they worked,but it literally made my system too slow,scrolling,selecting things and many others became much slower,even though i have a RAM of 1 GB,and an intel core2duo 2 GHz processor.please help as i am fed up with windows,and want to switch entirely to linux.

My system now is running real slow also. To make it normal i would have to end compriz.real process.

---

### Post by stonecoldjha on 2008-03-19
i did install start up manager,but it didn't solve my problems,in that i switched,i set the resolutio to 1024*768.but the desktop effects don't work at all.

---

### Post by ubuntu-freak on 2008-03-19
> **stonecoldjha said:**
> i did install start up manager,but it didn't solve my problems,in that i switched,i set the resolutio to 1024*768.but the desktop effects don't work at all.

 
That program was to help with your usplash problem.
 
Go to System>Preferences>Appearance>Effects after you run the SKIP_CHECKS=yes compiz --replace command, then tick the box for more advaned effects and see if your windows wobble when you move them around. 
 
Is it that important though? Your videos will not play with effects enabled unless you use the inferior x11 video driver. 
 
Nathan

---


---
title: "xubuntu 9.04 imac g3 install help please"
date: 2010-03-27
forum: Apple Hardware Users
---

### Post by seahuston on 2010-03-27
Hey All,

I know there have been a lot of topics on this but I am having no luck in getting this to work on my powerpc. I have read through the forums alot can found no working solutions.

Preliminaries:
I got an old imac g3 slot loading-model M5521
400 Mhz Processor
578 mb of ram
10 GB hard drive.

I had tried using xubuntu 8.10 with no luck and though I would try a new build.
I installed xubuntu 9.04 using the alternate install disc and these instructions:
[http://ubuntuforums.org/showthread.php?t=405934](http://ubuntuforums.org/showthread.php?t=405934)
The install went well, for the hard drive partition I used used the entire disc.
Problem 1: my username wasnt recognized, I thought I had a typed this in wrong so I reinstalled and made sure I was correct. It still had the same problem and I found some threads which explained this and fixed this problem.
Problem 2: Once the install was complete and I had grabbed my GUI--XFCE. There were a couple of errors at the end but I didnt write them down and I dont rember them. It looked like a couple packages didnt get downloaded/install.
*First question-is there a way to check this and maybe reinstall the missing packages.
I rebooted and the yaboot prompts ran and I got a "loading..." screen and then the screen went blank. This also happened with 8.10.
Attempt at solution
1. at second boot prompt, I entered 
"Linux video=ofonly nosplash"
and entered into the command line here I tried editing xorg.conf using
sudo nano /etc/X11/xorg.conf
This was blank which makes it hard to make the changes recommended on the Linux FAQs. For what to enter I used this thread and entered the information from the first post.
[http://ubuntuforums.org/showthread.php?t=1215154](http://ubuntuforums.org/showthread.php?t=1215154)
After I entered it I did
 ctrl-o, ctrl-x
 and then did 
sudo reboot
Upon reboot I just let the boots run and the still goes blank after the loading screen.
I again used the ofonly and got to command line. With 8.10 I was able to get to a GUI from this step in low graphics mode but I cant remember how I did this.

So, here I am now. I want to get Linux running on my imac and am getting a little bit frustrated at being unable to make it work. I have read and tried a few fixes and had no luck. Should I got to an old build like 6.10 or 7.10 or some other recommended one? can any one please offer support?
Thank You!

---

### Post by linuxopjemac on 2010-03-27
you need the correct xorg.conf file:

```
Section "Files"
FontPath "/usr/share/X11/fonts/misc"
FontPath "/usr/share/X11/cyrillic"
FontPath "/usr/share/X11/100dpi/:unscaled"
FontPath "/usr/share/X11/75dpi/:unscaled"
FontPath "/usr/share/X11/fonts/Type1"
FontPath "/usr/share/X11/fonts/CID"
FontPath "/usr/share/X11/fonts/100dpi"
FontPath "/usr/share/X11/fonts/75dpi" # paths to defoma fonts
FontPath "/var/lib//defoma/x-ttcidfont-conf.d/dirs/TruType"
FontPath "/var/lib//defoma/x-ttcidfont-conf.d/dirs/CID"

Section "Module"
Load "GLcore"
Load "i2c"
Load "bitmap"
Load "ddc"
Load "dri"
Load "extmod"
Load "freetype"
Load "glx"
Load "int10"
Load "type1"
Load "vbe"
EndSection

Section "InputDevice"
Identifier "Generic Keyboard"
Driver "kbd"
Option "XkbRules" "xorg"
Option "XkbModel" "pc104"
Option "XkbLayout" "us"
EndSection

Section "InputDevice"
Identifier "Configured Mouse"
Driver "mouse"
Option "CorePointer"
Option "Device" "/dev/input/mice"
Option "Protocol" "ImPS/2"
Option "Emulate3Buttons" "true"
Option "ZAxisMapping" "4 5"
EndSection

Section "Device"
Identifier "ATI Technologies, Inc. Rage 128 PR/PRO (AGP TMDS)"
Driver "ati"
Option "UseFBDev" "true"
EndSection

Section "Monitor"
Identifier "iMac"
Option "DPMS"
HorizSync 60-60
VertRefresh 75-117
EndSection

Section "Screen"
Identifier "Default Screen"
Device "ATI Technologies, Inc. Rage 128 PR/PRO (AGP TMDS)"
Monitor "iMac"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 4
Modes "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 8
Modes "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 15
Modes "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 16
Modes "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 24
Modes "800x600" "640x480"
EndSubSection
EndSection

Section "ServerLayout"
Identifier "Default Layout"
Screen "Default Screen"
InputDevice "Generic Keyboard"
InputDevice "Configured Mouse"
EndSection

Section "DRI"
Mode 0666
EndSection

```

---

### Post by seahuston on 2010-03-27
Hey, thanks a bunch!

I am in the process of typing this in but I want to make sure I am doing it correct. When I opened my xorg.conf using

sudo nano /etc/X11/xorg.conf

The changes I had made previously were not shown. I just got a primarily blank screen with controls at the bottom. 

I want to make sure I dont loose my work typing this in. What is proper way to exit/save the xorg.conf file after entering in all of information?
Also, should there be a "EndSection" at the end on the files sections?

---

### Post by seahuston on 2010-03-27
Oh, and also. 

I think i figured out that it is ^x and then y for yes to save.
Anything I should do next or should I just type sudo reboot and let the computer (hopefully) reboot into the GUI

---

### Post by seahuston on 2010-03-27
Okay,

Last reply...
I did ^x and did y to save the file. I got this error 
Error writing /etc/X11/xorg.conf: No such file or directory
???

---

### Post by seahuston on 2010-03-27
Please ignore the last couple.

I finally got it entered in. Saved the file and exited nano. then rebooted using sudo reboot

When it turned back on, it went though both yaboot screens and then went to a blank screen.

After these changes do i still need to use the 
Linux video=ofonly nosplash
boot command and if so how do i go from the command prompts to a GUI?

I'm a bit lost here.
Thanks!

---

### Post by linuxopjemac on 2010-03-27
it should work now...If you get into a prompt, you might want to issue:
```

sudo /etc/init.d/gdm start
```

try with your boot options and if you get into a shell, issue the command I gave you.

---

### Post by seahuston on 2010-03-27
Thank you for your help.

I booted using 
```
Linux video=ofonly
```
And tried used the command you gave me.
I recieved an error that Gnome was already running and so this action was aborted (or some similar dialogue)
I tried booting again using 
```
Linux video=ofonly nosplash
```
This time when I used the code you gave me said started the Gnome desktop manager and then on the right side there was [OK] but nothing else happened.
Is it a problem that I downloaded the XFCE environment?

---

### Post by linuxopjemac on 2010-03-27
I don't know for sure if GDM also handles XFCE. You might want to start X manually by:

startx

if it does not work, give me the output of:
```
cat /var/log/Xorg.0.log
```

---

### Post by linuxopjemac on 2010-03-27
[http://tuxicity.wordpress.com/2007/03/02/some-gdm-basics-for-ubuntu-and-xubuntu-theming-and-auto-login/](http://tuxicity.wordpress.com/2007/03/02/some-gdm-basics-for-ubuntu-and-xubuntu-theming-and-auto-login/)

Xubuntu uses GDM too...

---

### Post by seahuston on 2010-03-27
Thanks for the reply. I got it working using startx and then it said I needed to reboot once I got to my desktop.
I rebooted and didnt do any boot options and the screen went to black.
I started over and used the nosplash option and it booted awesome, right into the login screen. I havent played with the interface much yet but it works!
Looks like I need to append my yaboot so it always uses that option. 
Thanks for your help! Marking as solved!!!!!

---

### Post by linuxopjemac on 2010-03-28
Let me give you some good advice that will make your Ubuntu experience even better. I run Debian Lenny on a PowerBook G3 Pismo machine from 2000. Similar to your machine, it is a G3 with little CPU power. I switched from XFCE to LXDE. It rocks! You can simply try it yourself:
```
sudo apt-get install lubuntu-desktop
```

Then on the next login you choose LXDE in the sessions

You won't be disappointed...

PS. The only problem I have with Ubuntu as opposed to Debian, is the amount of extra installed packages if you choose lubuntu-desktop. In Debian you can choose to only install the LXDE environment, without all the extra bloated stuff

---


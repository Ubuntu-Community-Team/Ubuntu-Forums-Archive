---
title: "After Install, black screen of death."
date: 2008-04-04
forum: Absolute Beginner Talk
---

### Post by toolfan2k4 on 2008-04-04
Ok here are my specs.

COOLER MASTER Centurion 5 CAC-T05-UW Black Aluminum Bezel , SECC Chassis ATX Mid Tower Computer Case
Antec TRUEPOWERII TPII-550 ATX12V 550W Power Supply
BIOSTAR N4SLI-A9 939 NVIDIA nForce4 SLI ATX AMD Motherboard
AMD Athlon 64 X2 Dual Core Processor 3800+ Manchester
2 Gigs RAM, Dont remember what brand I think it was PNY.
EVGA 256-P2-N516 GeForce 7800GT 256MB 256-bit GDDR3 PCI Express x16 SLI Supported Video Card x2 in SLI (Windows)
NEC 16X DVD±R DVD Burner Black IDE/ATAPI
SAMSUNG HD250HJ 250GB 7200 RPM SATA 3.0Gb/s Hard Drive x2 NOT IN RAID.

I installed ubuntu 7.10 alternate because the GUI install wouldnt work. Now I got it installed but when I try to boot into it I see the splash screen and then a black screen comes up and won't go away unless I reboot. I tryed booting into ununtu's safe mode and that works and brings me to command prompt. I assume that maybe the vid cards being installed in SLI mode is maybe messing this up. Is there a way to get this working without effecting my SLI in windows.....gotta have the SLI for the games....LOL.:guitar:

---

### Post by Doorslammer on 2008-04-04
login  in recovery mode
sudo nano /etc/X11/xorg.conf
find the line" Section "Device"
then under drivers change from nvidia to nv save & reboot 
that will get you going  then you can reinstall the driver from the gui

the other thing you could do is ```
sudo dpkg-reconfigure xserver-xorg
``` this will run the set up for keyboard & few things again including your video card

---

### Post by toolfan2k4 on 2008-04-04
OK will do, where would I find drivers for my cards? Would Nvidia have linux drivers or will I need a third party set? And thanks much for the prompt answer.\

Edit: Found drivers at nvidia....now i just gotta figure out how to install.

---

### Post by bwallum on 2008-04-04
Ubuntu will get the driver for you. System>Administration>Hardware Drivers. Just check the box.

---

### Post by toolfan2k4 on 2008-04-04
> **bwallum said:**
> Ubuntu will get the driver for you. System>Administration>Hardware Drivers. Just check the box.

Sounds easy enough. If only I could get ubuntu to start up. Now I get the splash screen then some text on a black screen then it goes back to the black screen of death. This is after trying the above fix, i reconfigured....the first fix just brought me to what looked like a text editor with no text available to edit. No wonder linux hasn't taken off like it should....with compatibility problems like this why would it?:confused: Sorry I am just frustrated and ranting....I really do appreciate the help.:)

---

### Post by Therion on 2008-04-04
I've had this same issue for ages with plain vanilla installs of Ubuntu.  Try the following and see if this fixes things.  You&#8217;re going to have to edit a file called menu.lst a bit to make this fix permanent.  It takes longer to read than to actually perform. 

Ready?  Good.  Let's do this...

Reboot your PC.
When you see GRUB (it&#8217;s the countdown timer) hit the ESCape key.
Keep your selection on the first line of the menu and hit "E" to enter Edit mode.
Using the arrow keys, go to the second line of text and and hit "E" again to edit this line.
Delete the words **splash** and **quiet**.
Hit &#8220;Enter&#8221;, then "B" to continue booting.
Once you're in Ubuntu, open up the Terminal and enter:

```
gksudo gedit /boot/grub/menu.lst
```
Find and delete the words **quiet** and **splash** from the line that starts with Kernel  one more time.
Save the file, Exit&#8230; And you&#8217;re done.

Now do all your updates and such and *THEN* installl the Restricted Driver for your video card, if needed.  I use Envy for installing my drivers, but you can also let the Restricted Driver Manager do it if you prefer.  

Let me repeat: Updates first, THEN your video driver.  NOT the other way around.  The Restricted Driver Manager is going to pop up and want to install your drivers right away.  Don't do it.  Updates first.

---

### Post by toolfan2k4 on 2008-04-04
Ok i appreciate the continued help, but it did not work. The first part worked but when I pressed "B" to continue with the boot the screen showed scrolling text which stopped eventually. After it stopped the screen blinked a few times then went black again. :( Any other ideas?

---

### Post by toolfan2k4 on 2008-04-04
Also if it helps, the live cd wouldn't work either so its not the install itself I think.

---

### Post by PmDematagoda on 2008-04-04
I think it may be your VGA card.

Boot Ubuntu in Recovery Mode and install the Nvidia driver:-

1) Install the prerequisites for the driver:-
```
apt-get install build-essential
```

2) Download the driver:-
```
wget http://us.download.nvidia.com/XFree86/Linux-x86/169.12/NVIDIA-Linux-x86-169.12-pkg1.run
```

3) Install the driver:-
```
sh NVIDIA-Linux-x86-169.12-pkg1.run
```

4) Check the X-Server:-
```
startx
```

If that works then you can boot Ubuntu in normal mode properly.

---

### Post by jecker on 2008-04-09
In addition can you post the /var/log/Xorg.0.log log?

---

### Post by Hobo Joe on 2008-04-09
> **toolfan2k4 said:**
> Ok i appreciate the continued help, but it did not work. The first part worked but when I pressed "B" to continue with the boot the screen showed scrolling text which stopped eventually. After it stopped the screen blinked a few times then went black again. :( Any other ideas?

Do what Therion told you, except instead of deleting quiet and splash, simply edit it so that it says 'nosplash', instead of 'splash'.

---


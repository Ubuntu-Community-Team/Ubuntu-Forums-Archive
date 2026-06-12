---
title: "Low FPS"
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by PleaseEnjoyThis on 2007-05-11
I'm having very low FPS...help?

---

### Post by taurus on 2007-05-11
It would be real nice and helpful if you could at least list which graphic card do you have on your machine?

Applications -> Accessories -> Terminal
```
lspci
```

---

### Post by PleaseEnjoyThis on 2007-05-11
00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f2)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2)
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: nVidia Corporation GeForce 7900 GT (rev a1)
05:07.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 0a)
05:07.1 Input device controller: Creative Labs SB Live! Game Port (rev 0a)
05:0a.0 RAID bus controller: Silicon Image, Inc. SiI 3114 [SATALink/SATARaid] Serial ATA Controller (rev 02)
05:0b.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
05:0c.0 Ethernet controller: Marvell Technology Group Ltd. 88E8001 Gigabit Ethernet Controller (rev 13)

---

### Post by taurus on 2007-05-11
You need to install nVidia driver for your graphic card.

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by PleaseEnjoyThis on 2007-05-11
I fallowed all of the steps, but after I restarted I have no GUI.  The X or something is messsed up and has been disabled.  THe last time I had this happend I saved important files before hand to fix it.  .......

---

### Post by PleaseEnjoyThis on 2007-05-11
Please someone help!

---

### Post by PleaseEnjoyThis on 2007-05-12
!!!!!!!!!!!!!!!!!!!!!!!!!!!

---

### Post by RSingh on 2007-05-12
Did you backup your Xorg.conf file??? it usually resides here /etc/X11/xorg.conf

When the X server fails to start, just choose Ok and exit to the terminal output, no need to see the debug info. Come to the login terminal, login, and type this:

```
sudo cp /etc/X11/backupfile /etc/X11/xorg.conf
reboot

```



Usually I think there is a backup file present with the name: xorg.conf.backup or xorg.conf_backup in the X11 directory.

Also, there is a command that restores your original xorg.conf, don't rememmber what it was though.

If this fixes your problem then go here to install the proper nvidia drivers: [http://ubuntuguide.org/wiki/Ubuntu:Feisty]("http://ubuntuguide.org/wiki/Ubuntu:Feisty")

---

### Post by jiminycricket on 2007-05-12
Did you try sudo 'nvidia-config-display enable' ?

---

### Post by PleaseEnjoyThis on 2007-05-15
When I tried to run the backup file which I never created it said mv: cannot stat '/etc/X11/xorg.conf.backup': no such file or directory.  How can I fix this?  I really hope I can, this is really frustrating.....................

---

### Post by taurus on 2007-05-15
Can you post the output of this command from a terminal?

```
ls -la /etc/X11
```

---

### Post by pikul on 2007-05-15
Do you remember making a copy of the xorg.conf file? maybe you did and cant remember, type this at the terminal and see if there is another file named something like xorg

$ cd /etc/X11/  enter
$ dir  enter

Thats going to display the files on that folder.

---

### Post by Hobo Joe on 2007-05-15
I don't really know how to restore the xorg or anything after a crash like this, but I DO know that once you get it back up, you should use [Envy]("http://www.albertomilone.com/nvidia_scripts1.html") to install your driver, it makes the job a lot easier for people who don't really know how to do this stuff.

---

### Post by Sirhanz on 2007-05-15
```
sudo dpkg-reconfigure xserver-xorg

``` good idea to have graphics card make and chipset, amount of memory on your card, refresh rates of your display, supported resolutions of the display and the type of keyboard and mouse. kAll are listed in the ls you have done above. This will RE configure the x display including the video card and monitor.

---

### Post by PleaseEnjoyThis on 2007-05-16
I reconfigured my Xserver and when I rebooted my machine my desktop was all messed up.  I had no exit button, no bottom action bar, I couldn't drag windows, ect.  yeah...

---

### Post by Sirhanz on 2007-05-16
```
ls -la /etc/X11
``` does your mouse, keyboard and monitor appear on the ls displayed from this command? I am guessing they are not. Also is this the same or even close to the first xorg.conf file you posted before?

---

### Post by frostie on 2007-05-16
> **PleaseEnjoyThis said:**
> I reconfigured my Xserver and when I rebooted my machine my desktop was all messed up.  I had no exit button, no bottom action bar, I couldn't drag windows, ect.  yeah...

Reboot your machine and hit the ESC key to enter the GRUB menu. Choose recovery mode and hit enter, you will be dropped at a command prompt.

Then:

# cd /etc/X11
# ls -l

You will see your xorg.conf listed along with any backups that have been made. Try one of these by:

# cp xorg.conf.[add any extra bits of the backup filename] xorg.conf

Then reboot and see where it gets you. If the xserver still won't start repeat the process with each backup available until you find one that works.  If you do get one to work then it's worth going back in to /etc/X11 via a terminal and as root do:

# cp xorg.conf xorgcopy

just in case you need it again.

If all else fails you'll have to boot into recovery mode and do:

# dpkg-reconfigure xserver-xorg

and follow your nose.

hth.

---

### Post by PleaseEnjoyThis on 2007-05-16
The backup file didn't work so I reconfigured xserver for the second time.

There is still no "x" in the top right corner.  I can't move windows and when I open up a window it covers up the action bar.   !!!:confused: :confused: :confused:

---

### Post by PleaseEnjoyThis on 2007-05-16
Maybe this will help.

When I pressed the Show Desktop button this message appeared

"Your window manager does not support the show desktop button, or you are not running a window manager."

thanks for all the help and all future help!

---

### Post by PleaseEnjoyThis on 2007-05-16
!!!!!

---

### Post by Ziox on 2007-05-16
enter terminal if possible, or perhaps hit "atl + f2" then enter "metacity" without quotes. 
If that doesn't work, then enter "nautilus".

Also, if you are running Feisty, go to system > Adminstration > restricted Driver.  You should be able to enable your nVidia driver form there (you have to download nvidia-glx package)

---

### Post by PleaseEnjoyThis on 2007-05-17
thanks a TON Ziox.  LOVE.

---

### Post by PleaseEnjoyThis on 2007-05-17
I fixed the problems with the X, but I still can't install my nvidia drivers.  Everytime I fallow the instructions for installation, when I reboot my Xserver gets messed up again and I have to use my backup file.

---

### Post by Ziox on 2007-05-17
gedit /var/log/Xorg.0.log.old  I think that's the error log for the previous login session.  So you can perhaps post that to see what the problem is.

---

### Post by PleaseEnjoyThis on 2007-05-17
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Enabling RENDER acceleration
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(EE) NVIDIA(0): Failed to load the NVIDIA kernel module!
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(II) UnloadModule: "ramdac"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

Fatal server error:
no screens found




There is a ton more, but they won't let me post it because it has "40 images" and you only can post 8.  I just did my best to get what I thought was the important stuff, I can post more if needed.

---

### Post by PleaseEnjoyThis on 2007-05-18
?!?!?!??!?!?

---

### Post by orb9220 on 2007-05-18
I use Envy can be run from term or desktop. Fixed my problems. 

It will download the correct driver for you and config your xorg.conf

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---


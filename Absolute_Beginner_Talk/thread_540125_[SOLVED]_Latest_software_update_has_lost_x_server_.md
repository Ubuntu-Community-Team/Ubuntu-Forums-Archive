---
title: "[SOLVED] Latest software update has lost x server config"
date: 2007-09-01
forum: Absolute Beginner Talk
---

### Post by old_dog on 2007-09-01
I am running Fiesty Fawn 7.04 amd 64. Software updates available popped up just now, said ok when I restarted after installation the system moans about X server config file being incorrect and only gives me the command line. Please in detail what do I have to do to get back to normal. Having banged on about how good ubuntu is, the ignominy of it I am having to use XP to post this!
Cheers Old_dog

---

### Post by 505 on 2007-09-01
Find out which version of X-server you had before. E.g. go to Ubuntu's package search, and search for x-server. It should list the version number of the default X-server that worked with Feisty.
Then start Ubuntu, log in to the terminal and downgrade x-server by typing

sudo aptitude install xserver-xorg={version-number}

This will install the xserver you had before.

---

### Post by old_dog on 2007-09-01
Sorry to be a bit thick, what am I looking for in software packages? I am just a tad confused
Cheers old_dog

---

### Post by ffi on 2007-09-01
run the following and restart:

 
sudo dpkg-reconfigure -phigh xserver-xorg

if it doesnt work post the output and which graphics card, driver and kernel you were using...

---

### Post by wormser on 2007-09-01
I had the same problem with grub.  My menu.lst was reset with the new update.  Sounds like there is an issue with the update.  Did edit your xorg.conf before and back it up?  If you did maybe restoring it will solve your problem.

---

### Post by loell on 2007-09-01
> **wormser said:**
> I had the same problem with grub.  My menu.lst was reset with the new update.  Sounds like there is an issue with the update.  Did edit your xorg.conf before and back it up?  If you did maybe restoring it will solve your problem.

this also my problem too, did you just modify menu.lst? for it to be restored?

---

### Post by wormser on 2007-09-01
> **loell said:**
> this also my problem too, did you just modify menu.lst? for it to be restored?

I removed the splash on start up.  Installed the update and it was back.  Then I Looked at menu.lst and everything was back to default.  I just changed it back by modifying it.

---

### Post by Wartooth on 2007-09-01
Same problem for me, running 6.06 LTS. 

Here are some of the errors I've gotten:

The X server is now disabled.  Restart GDM when it is configured correctly.

Failed to load module "wfb" (module does not exist, 0)

Error: API mismatch: the NVIDIA kernel module has the version 1.0-8776, but this X module has the version 1.0-9746.  Please make sure that the kernel module and all NVIDIA driver components have the same version. 

(EE) NVIDIA (0): Filed to initialize the NVIDIA kernel module! Please ensure that there is a supported NVIDIA GPU in this system, and that the NVIDIA device files have been created properly.  Please consult the NVIDIA README for details. 
**aborting**

(EE) Screen(s) found, but none have a usable configuration. 

Fatal server error: 
no screens found

XIO:fatal IO error 104 (connection reset by peer) on X server":0.0" after 0 requests  (0 known processed) with 0 events remaining. 


Running dpkg-reconfigure -phigh xserver-xorg is of no use.  I bring it up, and then as I pick NVIDIA on the first screen, it kicks me out to a warning about possibly over writing a customized setting and tells me where it's made a back up, and then I'm presented with a command line under the blue box.

Sooooo...um.  What now? :confused:

Am I looking at reinstalling the NVIDIA driver, do I need to find an updated one?  Why is dpkg-reconfigure -phigh xserver-xorg acting the way it does?

I, too, am forced to use my buggy XP machine :(

---

### Post by old_dog on 2007-09-02
I'm sorry to say I gave up and blew everything away!
Have done a complete re-install. Tell me..... I want to stay with Ubuntu,  without some of the arcane knowledge some of you guys have what should I do to prevent this happening again? 
Thanks anyway 
Cheers old_dog

---

### Post by w4ett on 2007-09-02
When there is a kernel update, the restricted driver for your video card has to be reinstalled due to the fact that modules are complied and installed for your particular Nvidia driver that you are using.

From the command line type:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

This will give you the interface to modify the driver and resolutions. Controls are UP and DOWN cursor keys move the cursor and scrolls through available options, the space selects options, and <enter> confirms selections.

Select "nv" as the driver and press <enter>, then at the next screen you can enable any addttional resolutions that you want to use.....then use the cursor keys to highlight {OK} and <spacebar> to select the resolutions and press <enter> to save the selections as prompted, then type:

```
startx
```

This will get you to a GUI desktop. then go to:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Install envy and then from the terminal type:

```
sudo envy -t
```

This will run the installation script from the terminal....follow the instructions to remove the old attempted driver installation and then install the correct Nvidia proprietary driver.

Good Luck

---


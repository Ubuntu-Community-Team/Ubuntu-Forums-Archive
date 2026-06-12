---
title: "Installing Ubuntu Lucid Lynx 10.04 on an Apple iMac 11,1 27&quot;"
date: 2010-05-07
forum: Apple Hardware Users
---

### Post by supidupi on 2010-05-07
I successfully got the Ubuntu Desktop running on my iMac 11,1 27" using the following steps.
Maybe there is a better and easier way to install Ubuntu on the iMac 11,1 27" but finally it worked.

I use the minimal Ubuntu ISO image to install a commandline system. So you will need an internet connection.
Any other way to install a commandline system should also work (alternate CD or server CD).
If you choose any of the other ways to install a commandline system start with step 3.) instead of step 1.).

I am neither explaining the installation of a commandline system nor the special things about a Ubuntu installation on a Mac.
Please look at the official Ubuntu installation documentation of a commandline system:
[https://help.ubuntu.com/10.04/installation-guide/amd64/index.html](https://help.ubuntu.com/10.04/installation-guide/amd64/index.html)
To get a general idea how to install Ubuntu on a Mac look at:
[https://help.ubuntu.com/community/Intel_iMac](https://help.ubuntu.com/community/Intel_iMac)

Look at the following thread how to get the rest of the iMac 11,1 27" hardware to work:
[http://ubuntuforums.org/showthread.php?t=1439009&highlight=iMac](http://ubuntuforums.org/showthread.php?t=1439009&highlight=iMac)


 1.) Download the minimal Ubuntu installation image and burn it onto a CD.
     (e.g. [http://archive.ubuntu.com/ubuntu/dists/lucid/main/installer-amd64/current/images/netboot/mini.iso](http://archive.ubuntu.com/ubuntu/dists/lucid/main/installer-amd64/current/images/netboot/mini.iso))
 2.) Boot from the CD.
 3.) Install a command line system.
 4.) After finishing the installation do not reboot
     and go back to the "Ubuntu installer main menu" and select the option "Execute a shell".
 5.) Add "radeon.modeset=0 nomodeset" to the linux kernel parameters using the following commands:
     # sed -i 's/quiet/quiet radeon.modeset=0 nomodeset/g' /target/boot/grub/grub.cfg
     # sed -i 's/single/single radeon.modeset=0 nomodeset/g' /target/boot/grub/grub.cfg
     # sed -i 's/quiet/quiet radeon.modeset=0 nomodeset/g' /target/etc/default/grub
     # sed -i 's/GRUB_CMDLINE_LINUX=""/GRUB_CMDLINE_LINUX="radeon.modeset=0 nomodeset"/g' /target/etc/default/grub
 6.) Reboot into the new installation.
 7.) Update the Ubuntu installation:
     # sudo apt-get update
     # sudo apt-get dist-upgrade
     # sudo apt-get autoremove
     # sudo apt-get autoclean
     # sudo apt-get clean
 8.) Install the build essentials:
     # sudo apt-get install build-essential
 9.) Install the Ubuntu(Kubuntu/Xubuntu/Lubuntu) Desktop
     # sudo apt-get install ubuntu-desktop
     or
     # sudo apt-get install kubuntu-desktop
     or
     # sudo apt-get install xubuntu-desktop
     or
     # sudo apt-get install lubuntu-desktop
     (I tested it with kubuntu and lubuntu, but ubuntu and xubuntu should also work!)
10.) Put the latest ATI driver on the iMac (either via wget or via usb stick, ...).
     (e.g. [https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-10-4-x86.x86_64.run](https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-10-4-x86.x86_64.run))
11.) Start the driver installation:
     # sudo sh ati-driver-installer-10-4-x86.x86_64.run
12.) Follow the instructions of the installer and execute the following command after a successful installation:
     # sudo /usr/bin/aticonfig --initial
13.) Reboot the system:
     # sudo reboot
13.) After a reboot of the system the desktop manager should be shown
     and you are ready to start working with your new Ubuntu installation.

---

### Post by Daddazio on 2010-05-10
To solve restart issue append:
```
"reboot=pci"
```
in the line:
```
GRUB_CMDLINE_LINUX="... reboot=pci"
```
of the file:
```
/etc/default/grub
```then do ```
sudo update-grub
```

Someone get the bluetooth to work exept from the apple wireless keyboard and mouse?

Ciao, Matteo!:D

---

### Post by MountainX on 2010-10-16
> **supidupi said:**
> 
 3.) Install a command line system.
 

I'm stuck here.

I know you said:
> I am neither explaining the installation of a commandline system nor the special things about a Ubuntu installation on a Mac.


supidupi, could you just tell me if you installed grub to sda3 or to sda4? Did you delete sda3 as suggested [here]("http://ubuntuforums.org/showpost.php?p=9971694&postcount=26")?

I'm trying to figure out how to get past errors like this one:
> Status: MBR partiton table is invalid, partitions overlap.
  Error: Not Found returned from gptsync.efi 

---

### Post by MountainX on 2010-10-17
I worked around the GPT/MBR problems by just using the "Single Boot: Linux Only" option (see [https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)).

But after a successful install and performing your step 5
> 5.) Add "radeon.modeset=0 nomodeset" to the linux kernel parameters using the following commands:
     # sed -i 's/quiet/quiet radeon.modeset=0 nomodeset/g' /target/boot/grub/grub.cfg
     # sed -i 's/single/single radeon.modeset=0 nomodeset/g' /target/boot/grub/grub.cfg
     # sed -i 's/quiet/quiet radeon.modeset=0 nomodeset/g' /target/etc/default/grub
     # sed -i 's/GRUB_CMDLINE_LINUX=""/GRUB_CMDLINE_LINUX="radeon.modeset=0 nomodeset"/g' /target/etc/default/grubI get the black/blank screen on reboot. I tried several times and I checked the files for correct editing. No mistakes.

I also tried GRUB_CMDLINE_LINUX="reboot=pci" (and running update-grub) -- same bad result.

Any advice?

---

### Post by boutil on 2010-10-18
Hi,

What video driver are you using? If you use the free radeon driver, you might want to try something NOT newer than 6.12. On Debian, with 6.13, I am getting a black screen not because of KMS problems, but because the video is directed automatically to the extern DVI output (instead of the screen :( )

---

### Post by ragoster on 2010-10-29
Thank you, this worked fine for me. I was using the 10.10 ubuntu release though, and thus I used the 

[http://www2.ati.com/drivers/linux/ati-driver-installer-10-10-x86.x86_64.run](http://www2.ati.com/drivers/linux/ati-driver-installer-10-10-x86.x86_64.run)

driver installer instead.

/Ragnar

---

### Post by MountainX on 2010-10-29
> **ragoster said:**
> Thank you, this worked fine for me. I was using the 10.10 ubuntu release though, and thus I used the 

[http://www2.ati.com/drivers/linux/ati-driver-installer-10-10-x86.x86_64.run](http://www2.ati.com/drivers/linux/ati-driver-installer-10-10-x86.x86_64.run)

driver installer instead.

/Ragnar

Can you tell me which model iMac you have?

One way to do that is to check the serial number.

On the bottom of your iMac stand, you'll find a label with the serial number printed on it, or from the Apple menu, choose About This Mac. Configure To Order (CTO) models are designated with an asterisk (*). Check the **last three** characters on the serial number:
iMac (Mid 2010)
DAS, DNM* 	iMac (21.5-inch, Mid 2010)
DB7, DNN* 	iMac (21.5-inch, Mid 2010)
DB6, DNP*  	iMac (27-inch, Mid 2010)
DB5, DNR* 	iMac (27-inch, Mid 2010)
iMac (Late 2009)
5PC, B9U, CY8* 	iMac (21.5-inch, Late 2009)
5PK*, B9S* 	iMac (21.5-inch, Late 2009)
5PE, 5PJ, CYB*  	iMac (27-inch, Late 2009)
CYC*, 5PM*, 5RU* 	iMac (27-inch, Late 2009)

---

### Post by MountainX on 2010-11-02
I finally found it. Here's my problem. It's a known bug:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/597070](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/597070)

I hooked up an external monitor and booted into a Linux LiveCD and verified that this is indeed the issue I'm having. 

Using options - radeon.modeset=0 nomodeset and installing via the Alt CD do not work around the issue for me. I gave up installing Linux on my particular iMac model (for now).

---

### Post by timblack on 2011-01-02
Just wanted to confirm another case of successfully working around this little bug by following the critically important steps of:

* install refit
* use a text installer
* install grub on linux root partition, not separate boot partition
* sync MBR/GPT using refit's partition tool
* booting the kernel with "radeon.modeset=0 nomodeset" into a recovery shell
* install proprietary ATI drivers, unload the open radeon drivers and update xorg.conf accordingly.

In my case, I have a late 2009 27" iMac with ATI Radeon 4850 (ser. no. ends in 5RU), and am actually running Debian Squeeze. To install the ATI drivers, I followed the instructions at [http://wiki.debian.org/ATIProprietary#Squeeze](http://wiki.debian.org/ATIProprietary#Squeeze).

---

### Post by MountainX on 2011-01-02
> **timblack said:**
> Just wanted to confirm another case of successfully working around this little bug ...

In my case, I have a late 2009 27" iMac with ATI Radeon 4850 (ser. no. ends in 5RU)

Thanks for confirming. Your machine is just one serial number group different from my late 2009 27" iMac. So maybe this blank display problem is limited to a very small group of iMacs. My bad luck to be a Linux user and get one of those incompatible iMacs.

---

### Post by timblack on 2011-01-02
Hey MountainX, I think I read elsewhere that you wanted to install linux natively on your mac for performance reasons and that you were going to be doing SW dev with eclipse. Well, FWIW I'm doing exactly that and for exactly the same reasons. As you know, Eclipse can be a memory/cpu/diskio hog. I had been running Debian under VirtualBox in OSX, and now things are considerably faster.

Anyone that works with computer software is inherently and actively working around bugs in said software whether they know it or not. The fact that the open radeon driver has a bug that makes video output switch to the mini display port on certain hardware does not mean that it is impossible to run linux on that hardware. Assuming you're ok with using non-free software, the workaround is quite simple: don't exercise the buggy driver - instead bypass it by staying in text mode and installing the non-buggy proprietary driver.

You may have found another solution, but if you're interested in giving it another go, I believe you could probably get it working in a few hours if you make all the right turns at Albuquerque. I didn't, and it has sucked 3 days of my life from me. However, I learned several new things in the process, and for this I am grateful. My success was largely due to yours and others' prior work and documentation on this issue. I am just the lucky one that came along at the right time.

Cheers,
Tim

---

### Post by MountainX on 2011-01-02
> **timblack said:**
> Hey MountainX, I think I read elsewhere that you wanted to install linux natively on your mac for performance reasons and that you were going to be doing SW dev with eclipse. Well, FWIW I'm doing exactly that and for exactly the same reasons. As you know, Eclipse can be a memory/cpu/diskio hog. I had been running Debian under VirtualBox in OSX, and now things are considerably faster.

Anyone that works with computer software is inherently and actively working around bugs in said software whether they know it or not. The fact that the open radeon driver has a bug that makes video output switch to the mini display port on certain hardware does not mean that it is impossible to run linux on that hardware. Assuming you're ok with using non-free software, the workaround is quite simple: don't exercise the buggy driver - instead bypass it by staying in text mode and installing the non-buggy proprietary driver.

You may have found another solution, but if you're interested in giving it another go, I believe you could probably get it working in a few hours if you make all the right turns at Albuquerque. I didn't, and it has sucked 3 days of my life from me. However, I learned several new things in the process, and for this I am grateful. My success was largely due to yours and others' prior work and documentation on this issue. I am just the lucky one that came along at the right time.

Cheers,
Tim

Tim, Thanks for your very nice reply. I am very tempted to give it another try as you suggest, but I think I will resist. :) 

I did recognize that I could probably ultimately solve the issue, as you suggest. However, I stopped primarily because I felt Magic Trackpad and Magic Mouse support under Ubuntu were far from satisfactory. Even the wireless Apple keyboard support had annoying glitches. 

I built a new Ubuntu PC that is almost as silent as my iMac. This machine is faster than my iMac, has much more memory (16GB) and I have the HP zr30w monitor, so I'm not missing the 27" iMac monitor either :)

(However, I learned from my experience building this PC that one cannot beat the value of an iMac 27" if one wants a quiet machine with a great display. My custom PC cost me more than my iMac cost.)

I use this Ubuntu machine for all my work and I am now content to let my iMac remain in its near stock configuration. (All I did was replace the HDD with an SSD to make it totally silent.) 

The real deciding factor for me was the limited support for the Magic Trackpad and Magic Mouse.

On my Ubuntu PC I use the wired Apple keyboard and a Contour Roller Mouse Free2 (and EasyStroke). I'm very satisfied with my input and I don't miss the Magic Trackpad or Magic Mouse. I think the Contour Roller Mouse Free2 is the ultimate input tool. I never have to take my fingers off the home row (even when mousing) and I can work very fast.

I use my iMac mostly for watching DVDs and videos. I don't have a TV, so the iMac has become like my TV. :)

---

### Post by timblack on 2011-01-02
Sounds like a nice getup! You have quite a penchant for huge displays and ergo input devices. Do you do graphic design?

By "limited support" for magic mouse do you just mean the lack of scrolling and other gestures? I'm still trying to get my magic mouse paired with gnome-bluetooth. The keyboard wasn't too difficult but for some reason, the mouse is listed in the bluetooth devices list, but there is no option to pair it, it is not discovered when I scan for devices, and I can't figure out how to delete it and start over.. So I've got some work to be at feature parity with OSX but I've got a usb mouse so I don't care about it too much...

---

### Post by Nicbi on 2011-05-10
> **boutil said:**
> Hi,

What video driver are you using? If you use the free radeon driver, you might want to try something NOT newer than 6.12. On Debian, with 6.13, I am getting a black screen not because of KMS problems, but because the video is directed automatically to the extern DVI output (instead of the screen :( )

did you find a workarround ?? I'm using natty on an imac and have the same problem. using the restricted drivers from ati solved the problem, but i have then an issue with gnome 3 top bar, so that i would like to go back to the open source drivers...

---

### Post by slow2anger on 2012-09-22
Hello everyone with the "black screen" issue.  Please take a look at post #23 below.  It might help you.

[http://ubuntuforums.org/showthread.php?p=12255187#post12255187#23](http://ubuntuforums.org/showthread.php?p=12255187#post12255187#23)

---


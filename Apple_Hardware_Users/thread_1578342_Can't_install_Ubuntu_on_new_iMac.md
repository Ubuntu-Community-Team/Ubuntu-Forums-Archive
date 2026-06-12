---
title: "Can't install Ubuntu on new iMac"
date: 2010-09-20
forum: Apple Hardware Users
---

### Post by MountainX on 2010-09-20
At least two of us are having the same problem. I have an iMac 27" (11,1) and he has an iMac 11,2.

We have tried Ubuntu 10.04 Live CD, openSUSE 11.3 Live CD, Ubuntu 10.10 beta (2010.09.18) and Linux Mint 9 (32 bit).

Neither the "try" option nor the "install" option work. In both cases the screen goes completely black and stays black.

The installer screen with the language option comes up initially. But as soon as a language is selected, the screen goes black. The drive is still being accessed and it sounds like the installer is being loaded, but you can't see anything on the screen.

The CD stops reading after a few minutes and that's that.

Tried to set boot option vga=771 - no good. Boot option nomodeset - no good.

The other guy said all these discs worked on his old Mac Mini Solo (2006).
Looks like something's different about booting a live CD on the new iMacs. Anyone else trying this?

(BTW, I had to create a new post because a spammer caused the original thread to get locked.)

---

### Post by MountainX on 2010-09-20
I did some research on this. Here is what I found so far:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/542660](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/542660)

> I had the same problem on my iMac 27" but found a workaround for me:
* installed Ubuntu 10.04 (32 bit) with the text based installer (alternate-i386 CD)
* select the recovery mode and added "radeon.modeset=0 nomodeset" to the boot options (the line with linux ...)
* the recovery mode detected problems with the graphics and allowed me to use failsafe graphics for one session
* install the proprietary driver from ATI
* normal reboot: success.

[http://ubuntuforums.org/showthread.php?t=1476226](http://ubuntuforums.org/showthread.php?t=1476226) <-- shows a workaround
[http://ubuntuforums.org/showthread.php?t=1470389](http://ubuntuforums.org/showthread.php?t=1470389) <-- shows the original problem

more links:
[http://ubuntuforums.org/showthread.php?t=1484792](http://ubuntuforums.org/showthread.php?t=1484792)
[http://ubuntuforums.org/showthread.php?t=1456439](http://ubuntuforums.org/showthread.php?t=1456439)
[https://wiki.ubuntu.com/X/KernelModeSetting](https://wiki.ubuntu.com/X/KernelModeSetting)


> artik wrote on 2010-06-29:	 #32
As i reported here : [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/597070](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/597070)
It's not really black screen, it's the video output that switch to the mini display port output. If you plug a second screen on the mini display port, you can install ubuntu normally using this 2nd screen.

Really hope this bug will be corrected soon.


ATI-based solutions (not Mac specific, but related to this issue):
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)

---

### Post by MountainX on 2010-09-20
Could use some help here...

My steps so far:

* installed Ubuntu 10.10 (32 bit daily build for 2010.09.19) with the alternate text based installer (alternate-i386 CD).
* selected the recovery mode, pressed e to edit and added "radeon.modeset=0 nomodeset" to the boot options (the line that begins with linux ...) and press CTRL-X to boot.
* used failsafe graphics option
* install the proprietary driver from ATI. The GUI tool failed to find my ATI card, so I downloaded the latest ATI driver from the company's website and installed it in a terminal using "sudo sh ati-driver-installer-10-9-x86.x86_64.run --buildandinstallpkg". Success.
* shutdown when completed
* restart - Ubuntu drops into the shell - X doesn't load and I don't see any error messages.
* shutdown and start up again. This time the rEFIt Penguin logo never goes away and Ubuntu never starts up.

---

### Post by MountainX on 2010-10-08
bump
I am still looking for help on this...

---

### Post by jingo5 on 2010-10-13
I got a 27" iMac installed with the 7 Oct 2010 Daily of Kubuntu 10.10 alternative installer cd (couldn't get a usb disk to boot).

Your refit issue is something I also encountered.  The solution to that is to boot the installer cd, drop into rescue mode, then run 'parted' in a terminal.  Then use parted to set whatever partition contains /boot to be bootable.

The problem is EFI and MBR keep different records of the partition table, and the boot flag was set in one of the tables and not the other.

Once this change is made in parted, you can reboot, and boot linux properly with refit.

Problems you may encounter still:
1. If you use a bluetooth apple keyboard or magic mouse, the bluetooth pairing might cause you headaches - a bit of hackiness required to get it going until they triage and fix the bug.

2. Attempting to use fglrx may cause all sorts of fail with X (kdm may fail to load), so you would need to start your X session from a shell instead - and enable composite effects manually if you care about that.  One thing I haven't tried yet is to turn off kernel mode setting - I suspect this is the issue.

Hope that helps.

---

### Post by MountainX on 2010-10-13
> **jingo5 said:**
> I got a 27" iMac installed with the 7 Oct 2010 Daily of Kubuntu 10.10 alternative installer cd (couldn't get a usb disk to boot).

...

Hope that helps.


Yes, that's a lot of help. Thank you! (I do use the magic mouse and magic trackpad.)

Also, someone on Reddit gave me this link: [http://ubuntuforums.org/showthread.php?t=1476226](http://ubuntuforums.org/showthread.php?t=1476226)

I'm ready to give it another try now. I look forward to finally running Ubuntu on my iMac! :)

---

### Post by inanutshellus on 2010-10-15
I have a 27" iMac (model id "iMac11,1") and would like to install Ubuntu on it as the primary OS, but it's my work machine and tales of woe like this one have kept me away... If you get it working and can recall the steps it took to do so, toss up a tutorial or update the community Intel Imac page ([https://help.ubuntu.com/community/Intel_iMac](https://help.ubuntu.com/community/Intel_iMac)). It would be much appreciated!

---

### Post by MountainX on 2010-11-02
> **MountainX said:**
> ...In both cases the screen goes completely black and stays black.

Here's the problem. It's a known bug:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/597070](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/597070)

I hooked up an external monitor and booted into a Linux LiveCD and verified that this is indeed the issue I'm having. 

Using options - radeon.modeset=0 nomodeset and installing via the Alt CD do not work around the issue for me. I gave up installing Linux on my particular iMac model.

This issue does not affect all model iMacs. Mine is a 27" late 2009 model.

Here is how to check the serial number to determine the model.

On the bottom of your iMac stand, you'll find a label with the serial number printed on it, or from the Apple menu, choose About This Mac. Configure To Order (CTO) models are designated with an asterisk (*). Check the last three characters on the serial number:
iMac (Mid 2010)
DAS, DNM* iMac (21.5-inch, Mid 2010)
DB7, DNN* iMac (21.5-inch, Mid 2010)
DB6, DNP* iMac (27-inch, Mid 2010)
DB5, DNR* iMac (27-inch, Mid 2010)
iMac (Late 2009)
5PC, B9U, CY8* iMac (21.5-inch, Late 2009)
5PK*, B9S* iMac (21.5-inch, Late 2009)
5PE, 5PJ, CYB* iMac (27-inch, Late 2009)
CYC*, 5PM*, 5RU* iMac (27-inch, Late 2009

---

### Post by za.ch on 2010-11-23
I can confirm the bug. Primary screen is set to external display port output. Makes installing a lot less smooth than I had expected.

Thanks for your help.

So, the imac 27" blank screen problem with ati 4850 when installing ubuntu is solved with adding a external monitor. 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/597070](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/597070)

---

### Post by dylanjuran on 2010-12-03
i have a mid 2010 iMac 27" with a radeon 5750 graphics card. i would like to know if anyone has had a fix for this. i can get all the way through the installer, but then after the restart, it shows as bootable in rEFIt, but then goes to a blank black screen
.

---

### Post by arabis on 2010-12-04
Maybe you can use this iso:

[ubuntu-10.10-alternate-amd64+mac.iso]("http://cdimage.ubuntu.com/ports/releases/10.10/release/ubuntu-10.10-alternate-amd64+mac.iso")

It worked for me (Imac 11,2) with the option "radeon.modeset=0 nomodeset"

After the installation is completed (don't forget to put grub on the same partition than "/"), reboot on recovery (low graphic) and install the proprietary drivers for the video card. When you reboot, you will end with a login prompt on tty1. Don't worry, just wait about 3 minutes and gdm will start. Once on gnome, update your system. Normally, after that, you will reboot without this delay.

At the same time you can install the Mactel PPA and install the packages "btusb-dkms" "bluetooth" and "blueman" for your bluetooth keyboard and magic mouse.

When you are in recovery mode the bluetooth mouse and keyboard work with limitations, but in normal mode you have to pair them once with blueman to make them work. In normal mode you can use a regular mouse before you succeed to pair your magic mouse. If you have trouble using your keyboard you can use a virtual one (it is called "onboard") in gdm2 (accessibility) or in gnome (just make sure you make a shortcut on your desktop before when you are in recovery mode).

Hope it helps.;)

---

### Post by fipodk on 2010-12-08
Hey

I have also an iMac 11,2 and I have been trying to do the same as you did.

I'm tripple booting my system so my root partition for ubuntu is being installed in /dev/sda5 and the home folder in /dev/sda7

So when I'm asked where to install the grub I choose /dev/sda5.

When I reboot I can choose the ubuntu logo from Refit, but then it says that:
"missing operating system"

What am I doing wrong?

Thanks

---

### Post by jisaac on 2010-12-08
Try to install Grub in "/dev/sda"...

PS: You guys trying Maverick on iMac 27", let me know if you're experiencing "kacpid" and/or high temperature issues... Thanks.
See: [http://ubuntuforums.org/showthread.php?t=1639922](http://ubuntuforums.org/showthread.php?t=1639922) and [http://ubuntuforums.org/showthread.php?t=1639269](http://ubuntuforums.org/showthread.php?t=1639269)

---

### Post by fipodk on 2010-12-08
but that is the master boot record... don't you think I could mess up the computer and render it unbootable?

---

### Post by jisaac on 2010-12-08
Well it's confused for me, sorry for that. I told you to try this because I did it several times and it works well probably because I'm only booting OSX and Ubuntu.

Doing the same, you'll probably lose Windows at boot time but OSX would not be affected.

Have a look at:
[http://refit.sourceforge.net/help/windows_boots_linux.html](http://refit.sourceforge.net/help/windows_boots_linux.html)

I've just seen in my partition table that I have an "unknown" File System partition with flag "bios_grub".

Do you have such a partition?

---

### Post by arabis on 2010-12-08
> When I reboot I can choose the ubuntu logo from Refit

You should have a Tux logo rather than a Ubuntu logo unless you have themed your refit.

What version of refit did you install? Version of refit < 0.14 has problem with grub 2. I don't trible boot. I prefer using windows with Virtualbox under Ubuntu.

---

### Post by fipodk on 2010-12-08
Well writing the master boot record worked.

Somehow the windows partition did not work first from refit, but from grub it worked :)

Now the ati driver is working, however, how do I enable again the x ? so I don't have to login and startx from the command line?

Thanks

---

### Post by jisaac on 2010-12-08
I don't really understand why you have to run "startx" at login time.

Once Ubuntu is installed:

- Reboot and select "Recovery Mode" then edit kernel parameters (press "e" key) adding "radeon.modeset=0 nomodeset".
- Boot (press Ctrl+x).
- Choose "Low Graphics Mode"...

Then in an already started X session, install the proprietary driver using "System > Administration > Hardware Drivers".

The next time the machine boots (in normal mode), X starts properly using ATI Drivers. And at this stage I lose the mouse and keyboard, see: [http://ubuntuforums.org/showthread.php?t=1639129](http://ubuntuforums.org/showthread.php?t=1639129)

NB: Keep an eye on the temperature of your iMac using Ubuntu.

---

### Post by timblack on 2011-01-02
Just wanted to confirm another case of successfully working around this little bug by following the critically important steps of:

* use a text installer
* install grub on linux root partition, not separate boot partition
* sync MBR/GPT using refit's partition tool
* booting the kernel with "radeon.modeset=0 nomodeset" into a recovery shell
* install proprietary ATI drivers, unload the open radeon drivers and update xorg.conf accordingly.

In my case, I have a late 2009 27" iMac with ATI Radeon 4850 (ser. no. ends in 5RU), and am actually running Debian Squeeze. To install the ATI drivers, I followed the instructions at [http://wiki.debian.org/ATIProprietary#Squeeze](http://wiki.debian.org/ATIProprietary#Squeeze).

---

### Post by iphone3gs110 on 2011-01-13
hi
i install ubuntu 11.04 on new imac 27"
but can not install ati hd graphic driver

plz help

---

### Post by erginlee72 on 2011-05-02
I have Same problem in my imac
Ubuntu 10.10 or 11.04 have same problem
After grub ubuntu is opening, i can hear opening sound
but blank screen . .

radeon.modeset=0 nomodeset
do not work


ATI Radeon HD 4670:

  Chipset Model:	ATI Radeon HD 4670
  Type:	GPU
  Bus:	PCIe
  PCIe Lane Width:	x16
  VRAM (Total):	256 MB
  Vendor:	ATI (0x1002)
  Device ID:	0x9488
  Revision ID:	0x0000
  ROM Revision:	113-B8030H-114
  EFI Driver Version:	01.00.403
  Displays:
iMac:
  Resolution:	1920 x 1080
  Pixel Depth:	32-Bit Color (ARGB8888)
  Main Display:	Yes
  Mirror:	Off
  Online:	Yes
  Built-In:	Yes
  Connection Type:	DisplayPort
Display Connector:
  Status:	No Display Connected

---

### Post by MountainX on 2011-05-02
> **erginlee72 said:**
> I have Same problem in my imac
Ubuntu 10.10 or 11.04 have same problem

Sorry to hear that. I gave up on installing Ubuntu on my iMac. The limitations in support for the wireless Apple keyboard, the Magic Mouse and the Magic Trackpad convinced me that it would not be worth it even if I could eventually get Ubuntu installed.

Instead, I just built a custom PC with the goal of making it as fast and as quiet as my iMac. I largely succeeded, but I also gained great appreciation for the engineering quality and the design elegance of an iMac. It isn't possible to duplicate that quality at the same price IMO. But since I didn't mind spending more, I ended up with a great PC running Ubuntu and I still have a stock iMac (but with an SSD now) for those times when I need it.

---

### Post by slow2anger on 2012-09-22
This is how I overcame the black screen error.   In my case, the root cause was that Ubuntu didn't have the appropriate graphics driver installed.  But this is a chicken-and-egg issue because to install the driver, I'd typically need to first login to Ubuntu to do that, but then I can't because of the black screen error.  Here's what I did to make it work.

By the way, I have a 27' iMac11,1 with quad-core i5 and ATI Radeon HD 4850 graphics processor.  But as long as your root cause is the same as mine you should be able to follow the steps below to make it work.

0. Plug in a working internet ethernet cable to your iMac.

1. Download and install the following Ubuntu mac release.  Use something newer than 12.04 if a similar newer release is now available.
[http://cdimage.ubuntu.com/releases/12.04/release/ubuntu-12.04.1-alternate-amd64+mac.iso](http://cdimage.ubuntu.com/releases/12.04/release/ubuntu-12.04.1-alternate-amd64+mac.iso)

2. Just install that Ubuntu as usual, following the on-screen step-by-step instructions.

3. After the installation, you will reboot the iMac.  Right after the reboot, when the iMac just starts up with the sound, press and hold the alt key until you see the (wrongly labelled) Windows drive thingy.  That's your newly installed Ubuntu.  Click on it.

4. In the GRUB menu, choose the recovery mode.

5. You'll reach a menu with something like the following options.  Choose "network".  This will give you internet access.
Options: resume, clean, dpkg, failsafeX, fsck, grub, network, root, system-summary.

6. You should automatically be brought back to the menu again.  Now choose "root".  This will drop to root shell prompt.
Options: resume, clean, dpkg, failsafeX, fsck, grub, network, root, system-summary.

7. Now at the root shell, just to be sure that you have internet access, type "ping www.google.com" and observe that you're receiving bytes.

8. Run "jockey-text --list".  This will show a list of drivers (both enabled and disabled).  In my case, I had
xorg:fglrx_updates - ATI/AMD proprietary FGLRX graphics driver (post-release updates) (Proprietary, Disabled, Not in use)
xorg:fglrx - ATI/AMD proprietary FGLRX graphics driver (post-release updates) (Proprietary, Disabled, Not in use)

9. Run "jockey-text --enabled=DRIVER", where DRIVER is the driver name.  This will install/enable the graphics driver.  In my case, it was "jockey-text --enabled=xorg:fglrx".  (Don't enable xorg:fglrx_updates without first enabling xorg:fglrx)

10. Reboot (run "shutdown -r now") and you should be able to use the usual Ubuntu with GUI.

If this works for any of you, please reply the post.  Thanks!

MountainX, Don't use Apple's wireless keyboard/mouse.  Just use a  regular (even non-Apple) USB keyboard/mouse.  They should work right off  the bat.

---


---
title: "installing (k)ubuntu on Compaq Presario F560"
date: 2007-07-04
forum: Absolute Beginner Talk
---

### Post by odinb on 2007-07-04
Hi!

Anyone out there installed (k)ubuntu on the Presario F560?

Seems I have issue with the GPU (GeForce Go 6100). After booting off the Feisty 7.04 DVD, I choose to install, and my screen goes bananas. I get horisontal white lines, and some odd rainbow-colors in random spots. Seems the resolution is not compatible with the screen.

Any ideas?

---

### Post by atria on 2007-07-04
Did you try the second boot option? (Safe graphics mode)

---

### Post by odinb on 2007-07-05
Yup, same result, graphics/display freak out.

Found the drivers for the Go 6100 GPU through this page: [http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/README/appendix-a.html](http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/README/appendix-a.html)

I think this should be the one/this is the one I downloaded: [http://www.nvidia.com/object/linux_display_ia32_1.0-9755.html](http://www.nvidia.com/object/linux_display_ia32_1.0-9755.html)

(from that webpage: Type "sh NVIDIA-Linux-x86_64-100.14.11-pkg2.run" to install the driver. NVIDIA now provides a utility to assist you with configuration of your X config file.)

Installed kubuntu in text-only mode, which seems successful (but still, booting with graphics will not work), and are now trying to figure out how to load/install the drivers from a USB-stick from the root-prompt after booting in safe-mode.

Any hints?

---

### Post by odinb on 2007-07-05
This thread looks very similar to my issue:
[http://ubuntuforums.org/showthread.php?t=492214](http://ubuntuforums.org/showthread.php?t=492214)

---

### Post by odinb on 2007-07-05
Solved!

After installing in text-mode, I booted in safe-mode. Booting with graphics still did not work.

At the prompt I ran:

[I]sudo apt-get install nvidia-glx-new

sudo nvidia-glx-config enable[/I]

Then I rebooted the machine, and graphics now works, as well as audio.

Now for the next task, the Broadcom WLAN-card....

---

### Post by odinb on 2007-07-07
...and here are the instructions that made my WLAN-card (Broadcom "Dell Wireless 1390 WLAN MiniCard") work after a reinstall of kubuntu...

[http://ubuntuforums.org/showthread.php?t=297092](http://ubuntuforums.org/showthread.php?t=297092)

---

### Post by odinb on 2007-07-07
There is one more step I would mention. To get the driver to load automatically when you boot, insert "ndiswrapper" into /etc/modules. In terminal, type

*sudo echo ndiswrapper >> /etc/modules*

Then it will load automatically for you on each boot (instead of having to load it manually each time).

---

### Post by odinb on 2007-07-09
Wireless does not resume after resuming from hibernation. Reboot or logoff-logon needed to get WLAN back.

Anyone have a trick to fix this?

---

### Post by odinb on 2007-07-11
Just found this:

"For those of you with Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Cards, the kernel bcm43xx driver now supports those cards since kernel release 2.6.20.6 (check the [bcm43xx site]("http://bcm43xx.berlios.de/?go=devices") for details on what is supported).

So, if you would rather not deal with ndiswrapper, you can instead use the bcm43xx driver from the kernel. NOTE that you have to do a little extra work (installing firmware) to get it to work (explained here: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx"))"

Will see if I want to go through this to avoid issues when kernel-updates occurs....

---

### Post by odinb on 2007-12-21
This driver will work for the wlan:
# wget [http://ftp.hp.com/pub/softpaq/sp34001-34500/sp34152.exe](http://ftp.hp.com/pub/softpaq/sp34001-34500/sp34152.exe)

---

### Post by odinb on 2007-12-21
Getting Gutsy to run on this machine seems impossible!!

It will not boot after an upgrade to Gutsy.

Booting with  noapic irqpoll acpi=off will atleast get it to boot, but wlan will not work due to irq-issues. Were unable to resolve them.

Also, all powersave-features are broken......

Have given up on Gutsy for this machine, and have reinstalled Feisty. Feisty works excellent on this machine!!!!

---


---
title: "Windows 98"
date: 2006-09-30
forum: Absolute Beginner Talk
---

### Post by Gracenotes on 2006-09-30
In short:
I would like Linux to work on the computer that currently holds my Windows 98. For some reason, this Windows 98 does not support autoplay, unlike the Windows XP I'm using to post this depressing comment. My computer is organized thus:

**C drive, the one that currently holds Windows. 4.99 GB total, 963 MB free.
**D drive, the one I want Linux to be on. 13.9 GB total, 6.02 GB left. I put my programs and media files here.
**G drive, the CD-ROM/DVD drive. Currently contains a finalized CD-R with Ubuntu on it (ie, when opened, it reveals the files .disk, [BOOT], bin, casper, etc. I downloaded the ISO image and put it onto this CD-R.
**H drive, used for CD-RWs. Currently, Adaptec DirectCD works on Windows. However, once I install Linux, I'll need to transfer files from that Linux to this Windows XP. Is there any Open Source program that can handle this, if Adaptec can't?

I would greatly appreciate if someone could help me with this. If you need more information, I'd be more than happy to oblige.

[email]grac3not3s@gmail.com[/email]

---

### Post by Gracenotes on 2006-09-30
Oh, this is important:

Ubuntu 6.06 won't run on reboot.

Sorry. Should have included my problem if anyone could have any hope of solving it.

---

### Post by llamakc on 2006-09-30
You need to change the boot order in your BIOS so it attempts to boot from the CD first.

---

### Post by Gracenotes on 2006-09-30
Thanks, llamakc. I'm just a bit curious about how. Before I posted, I attempted to change the BIOS from rebooting, pressing F9, and seeing would I could do. I also tried to find BIOS in my Device Manager in system properties, but the nearest thing I could lay my mouse on was the "Advanced Configuration and Power Interface (ACPI) BIOS". This had no attached options, and was apparently provided by Microsoft.

As a student, the most hardware-related something is, the less I know about it (with exceptions). How would I alter the BIOS order, given the knowledge that that's the general idea? I'll admit that I'm asking for baby steps.

---

### Post by llamakc on 2006-09-30
BIOS loads before Linux or Windows. Do you know what type of computer you have?

Normally one presses the escape, delete, F1 keys DEPENDING on the bios to enter a configuration screen that is before the operating system loads.

If you figure out what key you need to press and get into BIOS you want to alter the order of the boot options so that your cd drive boots before the hard drive.

HTH

---

### Post by ewl1217 on 2006-09-30
You can access your BIOS just when your computer turns on, by pressing a certain key, which varies with each BIOS (if you can read fast, you may be able to see it on your computer's initial boot-up screen). It should be something like ESC, DEL, or one of the function keys (F1-F12). From there, you should be taken to the BIOS menu. Just find the boot order option and set it to boot from CD before the hard drive. Exit the BIOS **(Don't forget to save the changes!)**, and, if the CD is inserted, it should boot from the CD.

---

### Post by Gracenotes on 2006-09-30
I have a Sony VAIO. Interesting, the boot sequence says "CDROM,A,C" when I get into the BIOS options (by pressing F2). So the finalized CD-R, which contains the extracted ISO image, doesn't count as a CD-ROM for some reason. Even after I change this, that Windows emblem on the turgid light blue clouds background still appears. (Windows loads.)

---

### Post by ewl1217 on 2006-09-30
Did you burn the cd as a data or bootable CD? If you did, then try burning again as a disc image. Burning it as a data or bootable CD is just like copying the image to the CD, which is useless. Burning it as a disc image burns the contents of the image to the CD, which is what we need here.

---

### Post by theratster on 2006-10-01
Do a quick test. Put in your windows 98 CD (or a recovery CD) and reboot. Does it boot off of the CD? If it does, then your Ubuntu CD is the problem. If not, then the CD drive/BIOS is messed up.

---

### Post by Gracenotes on 2006-10-01
I seem to still be having a problem. Thanks for of your advice, however. I was able to burn a bootable CD that emulated a Hard Disk. Two more technical options, which I did not touch, were "Load Segment: 0x7c0" and "Sector Count: 1." So I loaded ubuntu-6.06.1-desktop-i386.iso to be burnt, which divided into BOOTCAT.BIN (2 KB) and BOOTIMG.BIN (715,172 KB). When I restarted my computer that contains Windows 98/that will contain Linux in the CD drive, it did NOT load Windows but instead printed on the screen
```
1. HD  System Type-(00)
```
Without any graphical interface yet visibly loaded. This remark was followed by a blinking cursor, which does not respond to any keyboard stimulus. Does anybody have any idea what is going on?

---

### Post by llamakc on 2006-10-01
Here is a great link:

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

Install this:

[http://www.cdburnerxp.se/download.php](http://www.cdburnerxp.se/download.php)

and follow the instructions on the 1st link.

---

### Post by Gracenotes on 2006-10-01
Super! I'll try it out precisely as they suggest. Thanks for the link.

---

### Post by Gracenotes on 2006-10-01
Ubuntu is now loading. This is awesome. It's loading!

Like it was loading about an hour ago.

In other words, the CD loading is taking an excruciatingly long quantity of time. I hope that I'll be able to download the Desktop version to my hard drive soon, because I can't do this every time I'd like it to load. Kudos to all who helped me.

---

### Post by Gracenotes on 2006-10-01
I'm really sorry to keep bothering everybody. But, Dapper Drake is taking an extremely long time to load. (After restarting and other such things a couple of times, it's been loading for at least an hour.) I suppose that this is because my computer reads from the CD-ROM drive at a very slow rate. I do want to keep Windows 98 (for the time being), which has Windows on Drive C. I also want to put Linux on Drive D, a hard drive, effectively partitioning the two OS's. Is there any way I could install Linux directly onto the D hard drive without all of the "try it first" stuff? I'm not sure if Ubuntu will ever load from the trial run, as it alternates between the default brownish loading screen and a blank screen every 10 minutes or so.

---

### Post by Sef on 2006-10-01
How much memory do you have?  If you less than 256 mb ram, you wuold be better off with xunbutu, a light-weight version with xfce instead of GNOME.

---

### Post by Paul133 on 2006-10-01
Don't worry. You just can't install the desktop CD for some reason. Same thing happened to me. Try the alternate CD. Burn it as an iso file. And check out [http://users.bigpond.net.au/hermanzone/p2.htm](http://users.bigpond.net.au/hermanzone/p2.htm) for some help as well as the other links. Just don't worry, you can DEFINITELY get Ubuntu installed if you try. Just try with the alternate CD, which should be much faster. I only had 256 MB of shared RAM and the LiveCD was excrutiatingly SLOW, so I tried the alternate CD and then the server install, and, as I predicted, and you predict, once it's on your drive, it should run much faster. BTW, I dualboot with XP.

---

### Post by Gracenotes on 2006-10-01
Thank you so much, Paul133. The link you provided me with has been helpful, but doesn't seem to say anything about NOT partitioning the C: drive and instead put Linux on my D: drive, which has plenty of space. I assume that I'd have to manually partition. Does anyone have any tips.

Once again, thanks for the help you people have deftly wrought. I'm sure, facetiously, that most phone tech support people would be cursing at me by now. I'm no stranger to computers, after all, just Linux.

---

### Post by gn2 on 2006-10-01
> **Gracenotes said:**
> Is there any way I could install Linux directly onto the D hard drive without all of the "try it first" stuff? 

One way, which I have used on a P3 500 192mbRam laptop is to use the 5.10 install CD. (5.10 came on two CD's Live and Install)

After 5.10 is installed and updated it will ask if you want to update to newer version (6.06) say yes, and off it goes downloading and installing.

It was all very simple point and click stuff, which for me is a good thing....

---

### Post by llamakc on 2006-10-01
Drive D:\ would be /dev/hdb1 most likely if it is a SEPARATE DEVICE. Install there.

You really need to tell us what your bios reports as the drives.

---


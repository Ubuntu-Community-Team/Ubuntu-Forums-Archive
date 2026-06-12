---
title: "Mac Mini 4.1"
date: 2010-06-26
forum: Apple Hardware Users
---

### Post by gavin0001 on 2010-06-26
Hi All,

Has anybody else tried booting ubuntu 10.04 on the latest Mac Mini?? I've removed quiet and splash from the boot options and found the following...
ata1: link slow to respond, please be patient (ready=0)
ata2: link slow to respond, please be patient (ready=0)
ata1: COMRESET failed (errno=-16)
ata2: COMRESET failed (errno=-16)

It will do this a couple of times, then turn off the screen. I've also tried the 9.10 cd and it does a similar thing, except it drops back to a busybox shell complaining that it can't find a medium containing a live cd file system (after the casper init script tries to run I think) instead of turning the monitor off.

Any ideas??

Cheers,
Gavin

Edit: When booting the 9.10 version, I think there was also a console message about limiting the sata speed to 1.5Gbps, can't really be sure, I can test again if neccessary

---

### Post by Moonman.ca on 2010-07-05
I've got exactly the same problem. I've also tried the alternate CD which said it couldn't load DVD drive drivers and prompted me to specify one. I've tried booting from the USB stick following the ubuntu wiki which did not work too. With the USB though it just didn't give me an option to boot from the USB.

---

### Post by Moonman.ca on 2010-07-06
> **ward70morris said:**
> It may be a driver issue as belvdr pointed out, but no Mac an have an  older Mac OSX version installed than the one it came with, so no Mac OS X  10.5 on a Mac, that came with Mac OS X 10.6, and no Mac OS X 10.6.3 on a  Mac that came with Mac OS X 10.6.4, although using an older Snow  Leopard Retail DVD might work, but I haven't tried that.

I'm not sure what you mean, but MacOS has nothing to do with ubuntu installation. One may completely remove MacOS and still have ubuntu (or any other linux distro) running.

---

### Post by Moonman.ca on 2010-07-10
Solution:[https://help.ubuntu.com/community/Macmini4-1/Lucid](https://help.ubuntu.com/community/Macmini4-1/Lucid)

---

### Post by fieldbio on 2010-07-15
I got it to boot by replacing quiet and splash with nomodeset in the boot options. It runs, but so far it ain't pretty...

(using the updated kernel version of Lucid found in the link from the previous post)

---

### Post by fruitpunch36 on 2010-07-17
When I boot the updated kernel dvd all I get is a purple screen with something that may be a keyboard or a GNOME desktop symbol with an arrow pointed to an "assistive technologies" symbol. Then my Mini stop sending a signal through its HDMI-DVI adapter and my screen is blank. I know there is something going on "behind the scenes"  because when I press the power button, it ejects the disc and powers off when I press the enter button (this is the normal). Can someone please help me get into boot options?

---

### Post by fieldbio on 2010-07-17
So I "think" that if you press a button while you see that screen it gets you to the normal ubuntu live-cd menu (ie: try ubuntu without installing, install ubuntu, memtest, etc). If you don't press anything then it attempts to boot to the "try ubuntu" option. But it does that without enabling the nomodeset feature that I mentioned before. So what you have to do when you see that screen:

1) press a button to get to the menu
2) press the F6 key to pull up the tab all the way on the bottom right
3) enable nomodeset
4) run "install ubuntu" from menu

Also, this kernel patched version has one major problem in that the hard drive write speed is 8Mb/s. I then updated the kernel by installing linux-image-2.6.32-24-generic. This fixes the boot nomodeset problem, but all of a sudden the wired, wireless and nvidia drivers don't work anymore :(

---

### Post by fruitpunch36 on 2010-07-18
Thank you! I successfully installed and booted Ubuntu on my Mini! Now the only problem is, that to download drivers, you need to connect to the internet to get drivers. I tried sharing my netbook's wireless via an ethernet cable, but it just doesn't see it. Is there any way to get wireless working on this. (Also a permanent nomodeset fix would be convenient :P)

---

### Post by blueridgedog on 2010-07-18
> **fruitpunch36 said:**
> Thank you! I successfully installed and booted Ubuntu on my Mini! Now the only problem is, that to download drivers, you need to connect to the internet to get drivers. I tried sharing my netbook's wireless via an ethernet cable, but it just doesn't see it. Is there any way to get wireless working on this. (Also a permanent nomodeset fix would be convenient :P)

To connect to computers directly with a cable, you would need either a crossover Ethernet cable or a hub/switch in between.  [http://en.wikipedia.org/wiki/Ethernet_crossover_cable](http://en.wikipedia.org/wiki/Ethernet_crossover_cable)

---

### Post by fruitpunch36 on 2010-07-18
Well, I've been able to connect my netbook to other computers before, so I think the case with the Mac Mini is that it has no ethernet drivers

---

### Post by fieldbio on 2010-07-18
This is what I did to get the drivers working: download the tg3 drivers from the Broadcom site using a different computer. Then you have to compile them (tar..make..make install). That will get your wired connection working- from there you can install the wireless and the nvidia drivers. Then you have an ALMOST completely running mac mini. The problem is that the hard drive write speed is still very very slow. If you can live with this for now until the kernel update goes through then great. If not, you have to upgrade the kernel from the lucid-proposed repository, and that fubars some of your drivers. Trying to figure out how to get around this.

Also, you can change the options in the grub, somehow, to add a permanent nomodeset. If you upgrade your kernel to the 32-24 the nomodeset problem goes away.

---

### Post by Moonman.ca on 2010-07-18
There is no drivers for Ethernet/wireless. You need to follow the link I posted in the 4th post to get evrything working. Also notice there's no FULL support for the chipset used in the new minis --> SATA/HDD access is slow. But at least it works. :popcorn:

---

### Post by fieldbio on 2010-07-18
Right, but the wireless/nvidia drivers can be installed from the Administration > Hardware Drivers application. Also, the SATA is supported in the new kernel patch (32-24) and that speeds up the write speeds significantly. (I got mine writing at 65Mb/s as opposed to 7Mb/s with the previous kernel). But installing the 32-24 kernel patch does strange things to the drivers.

---

### Post by Moonman.ca on 2010-07-18
> **fieldbio said:**
> Right, but the wireless/nvidia drivers can be installed from the Administration > Hardware Drivers application. Also, the SATA is supported in the new kernel patch (32-24) and that speeds up the write speeds significantly. (I got mine writing at 65Mb/s as opposed to 7Mb/s with the previous kernel). But installing the 32-24 kernel patch does strange things to the drivers.

Yes, but you need wired driver first.  Also wireless can be installed from the disk. Just tick the CD/DVD repo under Repositories. The new kernel is still beta though, so i guess strange things are expected.

What things does it do to the drivers?

---

### Post by fruitpunch36 on 2010-07-19
Can someone walk me through installing the tg3 drivers? I've downloaded them but have absolutely no clue how to do this. And this is the reason why I need linux on my Mac Mini, to learn it :P

---

### Post by fieldbio on 2010-07-20
Ok:

1.) You downloaded the zipped tg3 file to your desktop. Extract it.
2.) Open a terminal and type:
[INDENT]cd /Server/Linux/Driver[/INDENT]
[INDENT]tar -xvzf tg3-3.105h.tar.gz[/INDENT]

[INDENT]cd tg3-3.105h[/INDENT]
[INDENT]make[/INDENT]
[INDENT]sudo make install[/INDENT]

And that should install your wired lan drivers. Then you can use the system > Administration > hardware drivers to install the wireless and the nvidia drivers. 


@Moonman.ca: turns out it's not too bad. You have to make sure you install the linux-headers-2.6.32-24-generic as well, and then after make install you have to use modprobe or insmode to load the driver modules to the kernel. Make install puts the tg3.ko in the wrong place: you have to move it to /lib/modules/2.6.3-24-generic/kernel/drivers/net/tg3.ko. Then it will load on boot. The wireless and nvidia drivers need to be reinstalled but then they work fine.

---

### Post by nataraj88 on 2010-07-28
Is it still the case that reboot does not work on the 2010 Mac Mini as documented here [https://help.ubuntu.com/community/Macmini4-1/Lucid#Reboot]("https://help.ubuntu.com/community/Macmini4-1/Lucid#Reboot")?  If so, can somebody who has one, please file a bug report in launchpad.

I am considering buying a new 4,1 Mac mini, but would like to know if this bug still exists.

Also, does anyone have any performance reports for an SSD in a Mac Mini?

Thanks,
Nataraj

---

### Post by erk on 2010-07-28
I have an interest in running virtualization on Mac Mini's instead of blade servers because you can get 20 Mac Mini's into the 10RU space of a blade server at a fraction of the cost.

I just finished installing on to a brand new Mac Mini Server the daily snapshot of Ubuntu Server [http://cdimage.ubuntu.com/ubuntu-server/daily/current/](http://cdimage.ubuntu.com/ubuntu-server/daily/current/)

I can report that both the hard drives and Ethernet were detected and worked first time. I still needed to put the nomodeset flag into the boot options or the display would switch off during boot. 

The reboot command is still broken, and simply freezes the machine.

I had a problem with the GRUB install not working on /dev/sda when I accepted the default partition option of using the whole drive with LVM, the drive was no longer bootable. I don't really know what LVM does so perhaps telling GRUB to install on /dev/sda was inappropriate. Anyway when I partitoned using the whole drive without LVM GRUB worked fine.


I haven't done any performance testing, still early days but progress is good so far.

---

### Post by erk on 2010-08-02
Some more testing since my last post 4 days ago.

The reboot problem can be fixed by adding reboot=pci to the grub command line options after the nomodeset

I can't figure out how to make the options permanent.

I have tried editing the string in /boot/grub/menu.lst

eg:

> title           Ubuntu maverick (development branch), kernel 2.6.35-14-server
uuid            11712369-331c-421f-a5ba-f736b31d9e17
kernel          /boot/vmlinuz-2.6.35-14-server root=UUID=11712369-331c-421f-a5ba-f736b31d9e17 ro nomodeset reboot=pci
initrd          /boot/initrd.img-2.6.35-14-server


Then run an update-grub, but the additions I made do not appear in the startup menu when I press e to check/edit them.

Any clues on how to make it permanent?

---

### Post by camobrite on 2010-08-04
> **fruitpunch36 said:**
> When I boot the updated kernel dvd all I get is a purple screen with something that may be a keyboard or a GNOME desktop symbol with an arrow pointed to an "assistive technologies" symbol. Then my Mini stop sending a signal through its HDMI-DVI adapter and my screen is blank. I know there is something going on "behind the scenes"  because when I press the power button, it ejects the disc and powers off when I press the enter button (this is the normal). Can someone please help me get into boot options?

Hi, all.

I'm having a very similar issue to this, except that instead of going black, the screen output is heavily distorted with flashing colored lines obscuring the screen. I've tried this with several monitors and the output is always distorted, although with different patterns on different monitors. I was able to install ubuntu 10.04 with the official patch for the new mac mini, but it was difficult with the screen being obscured through the entire graphical installation process and afterwards, except for displaying the "keyboard = universal access" symbol at the very beginning. Now, even though it will boot to linux and the grub screen displays without problems, as soon as the ubuntu graphical startup screen appears the output gets distorted.

Just to be clear, I'm using the 1.4" tall 2.4 GHz mac mini with 4 USB ports. I'm triple booting using refit 0.14. If anyone know how to get my graphics working that would be great! I can still access my machine's desktop and terminal, it's just too distorted to do work on.

---

### Post by MartinAyla on 2010-08-04
> **fieldbio said:**
> Right, but the wireless/nvidia drivers can be installed from the Administration > Hardware Drivers application. Also, the SATA is supported in the new kernel patch (32-24) and that speeds up the write speeds significantly. (I got mine writing at 65Mb/s as opposed to 7Mb/s with the previous kernel). But installing the 32-24 kernel patch does strange things to the drivers.

fieldbio, how exactly did you get your write speeds to 65Mb/s?

I just installed the new 2.6.35 kernel in 10.04 daily build from yesterday (see here: [http://blog.avirtualhome.com/2010/08/02/kernel-2-6-35-available-for-ubuntu-10-04/](http://blog.avirtualhome.com/2010/08/02/kernel-2-6-35-available-for-ubuntu-10-04/)) - but my write speed still says 7,8 MB/s when I test with "dd" in Terminal.

I would think that the "fix" in the 32-24 kernel would be in the new 2.6.35 kernel too?

**EDIT**: I just ran the disk test in the "System Testing" application in Ubuntu and it says: Timing buffered disk reads = 68.58 MB/sec - is that the performance/numbers I should expect?

/Martin

---

### Post by Sirellyn on 2010-11-13
I can install Ubuntu fine, but when it reboots I get first a grey screen, then a black screen, then a cursor flashing in the corner for a second or two and then the monitor goes out and cannot detect.  (Digital Monitor)

I can't access grub.  And since this seems to be using GRUB2 I have no idea how to configure the multitude of text files it now breaks down into.

I've tried reinstalling maybe 5 times now with different options.  I didn't even see any sort of options for LVM.

I can access the grub2 files by booting the CD and then using it to run ubuntu.  So I guess I'll play around with those grub2 files for a while...

---

### Post by Jeisson on 2010-11-14
Sirellyn.

Instructions [in this post]("http://ubuntuforums.org/showpost.php?p=10053692&postcount=7") could help you get video working. The following page briefs things working on Mac Mini 4,1 with Ubuntu 10.10:

[https://help.ubuntu.com/community/Macmini4-1/Maverick](https://help.ubuntu.com/community/Macmini4-1/Maverick)

Best regards
-Jeisson

---

### Post by Sirellyn on 2010-11-17
Thanks for the help.  I tried the page you suggested, but I'm using a 10.04 LTS disk.  The one they suggested using on the 10.04 Ubuntu page.

Still when I hold down CTRL when it's booting I just get the same thing.  I tried both CTRL keys.  I've tried shift(s) and the like, I've reinstalled 7 times now and I just can't ever seem to get GRUB to show up.

I only have a few hours to work on this each week sadly so I'll try the alternate 10.10 CD as per that link you sent, and if that doesn't work I guess I'll just have to learn the GRUB 2 script and somehow get it to set NOMODESET in it.

At least I can access the installed HD via booting from CD.  Any other suggestions are welcome but thanks for the help.

---

### Post by Sirellyn on 2010-11-20
So update.  I finally got it working on it's own.

I followed the instructions on this page with a few exceptions:
[http://ubuntuforums.org/showpost.php?p=10053692&postcount=7](http://ubuntuforums.org/showpost.php?p=10053692&postcount=7)

1.) I used the Alternate link for Unbuntu 10.10. And installed that.
[http://www.ubuntu.com/desktop/get-ubuntu/alternative-download](http://www.ubuntu.com/desktop/get-ubuntu/alternative-download)

2.) Instead of just rebooting and accessing grub by holding down CTRL (this never seemed to work for me) I had to boot with the CD (After everything was installed) and then choose the option to "boot with CD" after I had modified the boot settings to include:

nomodeset reboot=pci  (Also remove splash and quiet)

3.) It booted up and I used gedit to edit grub as instructed to by the first link.

Everything booted fine (without the CD) after that.  I'm going to clean gnome and install KDE now (not a big gnome fan, but had a worse time trying to get kubuntu to work.)  And if all this didn't work I was tempted to try rEFIt.
[http://refit.sourceforge.net/](http://refit.sourceforge.net/)

Anyway good luck to anyone else.

---

### Post by Sirellyn on 2010-11-27
Bah, why is this never easy.  One month into trying to install this thing, and I'm up and running but Ubuntu can only detect 4 GBs of my 8GBs of ram.  Anyone else had an issue with this?

---

### Post by blueridgedog on 2010-11-27
> **Sirellyn said:**
> Bah, why is this never easy.  One month into trying to install this thing, and I'm up and running but Ubuntu can only detect 4 GBs of my 8GBs of ram.  Anyone else had an issue with this?

Did you install the 64 bit version?

---

### Post by Sirellyn on 2010-11-28
I just figured that out.  I had no idea you couldn't access more Ram w/o using the 64 bit version.  I guess I'll have to do it again.

Is there a page somewhere that shows what the 64 bit version can do that the 32 bit version can't?

Thanks!

---

### Post by nataraj88 on 2010-11-28
> **Sirellyn said:**
> I just figured that out.  I had no idea you couldn't access more Ram w/o using the 64 bit version.  I guess I'll have to do it again.

Is there a page somewhere that shows what the 64 bit version can do that the 32 bit version can't?

Thanks!

If you don't want to reinstall, you can also run the PAE kernel, which will limit the size of a single process to under 4GB, but multiple processes can make use of 8GB or more of memory.  This is fine in most cases where you don't have a single application that needs lots of memory.

Nataraj

---


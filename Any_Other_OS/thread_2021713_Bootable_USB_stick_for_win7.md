---
title: "Bootable USB stick for win7"
date: 2012-07-09
forum: Any Other OS
---

### Post by Kriste on 2012-07-09
Hi guys! 
I want to make a bootable USB  stick for win7. I use Linux mint operation system.  And the problem is that  when I use universal usb installer, this program can't find my usb stick letter. So then I decided to use Unebootin. The problem still the same. Last thing, I decided to install Startup disk ( usb-creator-gtk). Now this program can't find  iso file, I tried win7, xp, ubuntu desktop iso.  Not working... :confused:

Sreenshots:
[]("http://www.part.lt/img/046c167961c9c7f89f04d987ff50244d77.png")[http://wew.lt/paveiksleliai/1/Screenshotat2012-07-10000314.png](http://wew.lt/paveiksleliai/1/Screenshotat2012-07-10000314.png)
[http://wew.lt/paveiksleliai/1/Screenshotat2012-07-10000656.png](http://wew.lt/paveiksleliai/1/Screenshotat2012-07-10000656.png)

---

### Post by Double.J on 2012-07-09
Hi there!

sorry I got a bit confused. Did you want to create a USB stick that runs linux or a usb stick that runs windows?

I'm afraid that if it's the latter, none of those programs mentioned would be able to do it i'm afraid; they are all tools for creating live usb stick from unix systems that use a compressed file system; this is very different to windows.

Also, if you'd like to boot windows, is this to make a USB installer for windows, or are you trying to install windows on  a usb drive?

---

### Post by Kriste on 2012-07-09
I want to create usb stick that runs windows. 
Situation was like this: my win7 was crashing down and only one iso file was linux mint on my computer  so I used it and I made bootable usb stick which runs linux. ( I made that with Universal usb isntaller). As I am not good at linux. I want win7 on my laptop back.... but to do tha I need to create usb stick which can run win7...

---

### Post by oldfred on 2012-07-09
Windows is only licensed to run on one computer and has checks to make sure you do not install to any removable devices. 

You can put the Windows installer on a USB, but not the full program like you can with Ubuntu or most Linuxes.

If you have room you can create a primary NTFS partition with the boot flag and install Windows to that on your hard drive. Then you can dual boot. Generally 30GB is suggested as the minimum for Windows 7 or 20GB or XP.

---

### Post by Double.J on 2012-07-09
> **Kriste said:**
>  I need to create usb stick which can run win7...

Cool, well the good news is I was wrong; some versions of unetbootin can handle win 7 iso's ( :D ) - this would have saved me no end of trouble installing on my MBA last year!

Check out[ this how to]("http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html") - hope it's helpful!

---

### Post by critin on 2012-07-09
> **gnu/mirow said:**
> Cool, well the good news is I was wrong; some versions of unetbootin can handle win 7 iso's ( :D ) - this would have saved me no end of trouble installing on my MBA last year!

Check out[ this how to]("http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html") - hope it's helpful!

You can also create a usb bootable with a progam called, Rufus.  I use it for win8 and it works.

---

### Post by oklokl on 2012-07-09
[http://www.addictivetips.com/ubuntu-linux-tips/winusb-create-bootable-windows-installer-usb-in-ubuntu-linux/](http://www.addictivetips.com/ubuntu-linux-tips/winusb-create-bootable-windows-installer-usb-in-ubuntu-linux/)

[https://launchpad.net/~colingille/+archive/freshlight]("https://launchpad.net/%7Ecolingille/+archive/freshlight")


sudo add-apt-repository ppa:colingille/freshlight
sudo apt-get update
sudo apt-get install winusb

Since  WinUSB also works from the command line, you can create a Windows 7 or  Windows Vista USB installer by following the command line format given  below:



Once the USB is formatted using the above method, install a Windows partition and edit the Master Boot Record:



sudo parted -l                            

sudo mkfs.ntfs -f /dev/sdXy  



sudo winusb --install <iso path> <partition>

sudo winusb --install "win test.iso" /dev/sdc1

---

### Post by Kriste on 2012-07-10
> **gnu/mirow said:**
> Cool, well the good news is I was wrong; some versions of unetbootin can handle win 7 iso's ( :D ) - this would have saved me no end of trouble installing on my MBA last year!

Check out[ this how to]("http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html") - hope it's helpful!

[U]I made everything as was written. But when it come to boot, it was not bootable. Also files inside usb is quite stange:
[/U][http://wew.lt/paveiksleliai/1/Screenshotat2012-07-10165347.png](http://wew.lt/paveiksleliai/1/Screenshotat2012-07-10165347.png)
[]("http://wew.lt/paveiksleliai/1/Screenshotat2012-07-10134822.png")

---

### Post by Kriste on 2012-07-10
> **critin said:**
> You can also create a usb bootable with a progam called, Rufus.  I use it for win8 and it works.
I downloaded Rufus from here: [http://rufus.akeo.ie/](http://rufus.akeo.ie/). But I can't even load it... I tried 4 different versions.. it looks like it does not work on ' :icon_frown:

---

### Post by Kriste on 2012-07-10
So with Unetboot I was able to make a boot able usb which runs Ubuntu. But to make usb which run win7 - I can't. Hope it's because of iso. I will try to get new one. But one more problem come.  **BOOTMGR is missing**. The thread says: [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)  - but I am using Linux mint, and such command as sudo grub is invalid for me....

---


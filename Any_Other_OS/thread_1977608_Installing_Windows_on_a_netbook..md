---
title: "Installing Windows on a netbook."
date: 2012-05-10
forum: Any Other OS
---

### Post by iMurshaq on 2012-05-10
Hi all,

My sister's netbook had XP on it until a .dll file got corrupted so the only fix I could see possible was to install Ubuntu on it via LiveUSB since the netbook does not have a CD-ROM drive. Only problem is my sister has NO idea how Ubuntu works and teaching her is a nightmare. I have an external CD-ROM drive but the issue is that it will not work with the BIOS on the netbook so therefore I cannot figure out any way to get Windows back onto this computer.(Yes, I have a Windows XP CD)

Thanks in advance,
iMurshaq

---

### Post by samigina on 2012-05-10
Make a Windows USB install.

[http://wintoflash.com/home/en/](http://wintoflash.com/home/en/)

---

### Post by iMurshaq on 2012-05-10
I don't have another computer running Windows, because my Win 7 laptop is broken and my parents both have Macbooks.

---

### Post by samigina on 2012-05-10
Maybe this?

[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

Or this?

[http://www.makeuseof.com/tag/create-windows-usb-installation-disk-winusb-linux/](http://www.makeuseof.com/tag/create-windows-usb-installation-disk-winusb-linux/)

---

### Post by daslinkard on 2012-05-10
When you say the CD Rom will not work in the BIOS...what is it doing that you are unable to access it?

---

### Post by wilee-nilee on 2012-05-10
If the XP cd does not have sata drivers on the disc you will probably have to install it in a IDE setup, this is changed in the bios. You can download the sata drivers though and extract the XP cd and put them in if you want rather easy to do really.

[http://www.nliteos.com/](http://www.nliteos.com/)

If you decide to go IDE and want to keep Ubuntu, check the bios and see how it is set now if sata/AHCI, change to IDE and make sure ubuntu will run/boot in this configuration. It will for sure if installed in a IDE set up, you have to check if it will just changing it.

The wintoflash works great as posted earlier, but it has to be a legit XP cd.

Find a friend running windows to load that thumb, I doubt you wil get it loaded in a Linux enviroment, it can be done maybe even with the links, but XP was not designed to go on a thumb originally it is a rather difficult hack to be honest, if a supposed set of links says so thhey may sometimes for some people.

Worse case install the XP in a virtual and load the thumb from there.

---

### Post by drawkcab on 2012-05-11
You should try linux mint debian edition w/xfce.  I could see where going from xp to Ubuntu w/unity would be a shock.  Mint is an easier transition.  In the long run, she'll be much better off with Mint.

---

### Post by iMurshaq on 2012-05-11
> **wilee-nilee said:**
> If the XP cd does not have sata drivers on the disc you will probably have to install it in a IDE setup, this is changed in the bios. You can download the sata drivers though and extract the XP cd and put them in if you want rather easy to do really.

[http://www.nliteos.com/](http://www.nliteos.com/)

If you decide to go IDE and want to keep Ubuntu, check the bios and see how it is set now if sata/AHCI, change to IDE and make sure ubuntu will run/boot in this configuration. It will for sure if installed in a IDE set up, you have to check if it will just changing it.

The wintoflash works great as posted earlier, but it has to be a legit XP cd.

Find a friend running windows to load that thumb, I doubt you wil get it loaded in a Linux enviroment, it can be done maybe even with the links, but XP was not designed to go on a thumb originally it is a rather difficult hack to be honest, if a supposed set of links says so thhey may sometimes for some people.

Worse case install the XP in a virtual and load the thumb from there.

My CD is a legit copy, but I'm also worried about finding all of the drivers. I know that when I bought the laptop I'm using now, it had Vista on it and it was SO slow so I put XP on it and finding the drivers was a nightmare because I bought it from a friend and he lost the driver CD. I'm worried about having to find all of the drivers for her laptop b/c I don't think we have the Disc anymore.

---

### Post by iMurshaq on 2012-05-11
> **drawkcab said:**
> You should try linux mint debian edition w/xfce.  I could see where going from xp to Ubuntu w/unity would be a shock.  Mint is an easier transition.  In the long run, she'll be much better off with Mint.

I'm trying to stay away from any Linux distros on her laptop because she is kind of technologically retarded. Maybe she should get a Mac, lol.

---

### Post by wilee-nilee on 2012-05-11
The drivers I sure are easily available, just go to the manufacturers site or search with the computer model. XP will run fine in a IDE setup, probably just as well. XP was originally released before sata drives I believe so no big deal.

My concern was whether if you keep the Linux that it will run if switched to IDE if not there already, it will run in IDE but you have to check if when switched it still will.

---

### Post by iMurshaq on 2012-05-11
Her computer has a SATA drive in it.

---

### Post by wilee-nilee on 2012-05-11
> **iMurshaq said:**
> Her computer has a SATA drive in it.

Right but in the bios there is a place you can change how the drive is read, from sata/ahci or ide.

---


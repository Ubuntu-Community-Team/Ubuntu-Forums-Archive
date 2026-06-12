---
title: "Crashed bios makes me think about turning to Ubuntu (again)"
date: 2007-12-03
forum: Absolute Beginner Talk
---

### Post by Stolengoat on 2007-12-03
Hi everyone - perhaps someone can help - I'm a complete Newbie.

About a year ago when I got a new machine, I partitioned my hard-disk, with 60GB for Ubuntu and 60GB for Windows XP.  I hoped to use both, but I ended up using Windows exclusively, and my Ubuntu partition sat unused.

Recently, however, my BIOS was corrupted and I replaced my motherboard as a last resort (I couldn't flash it, and it was soldered in, so I couldn't get a new chip).  I've always been prejudiced against Windows because of the security and infection issues, and I blame this corruption on a virus, but perhaps I'm being unfair!  The kids seem to need windows for lots of the applications they use, and that's why I ended up using it (and also the problems I had initially trying to get a modem to work with Ubuntu!)

Anyway, the machine is now working again, using the same HDD, but it only gets as far as the menu screen which asks me to choose my preference for OS - Ubuntu or Windows.  If I choose either it crashes and reboots.

Here is my question (at long last!):  If I burn and try to install the latest version of Ubuntu, will it install before this menu (and hence get around the problem of it crashing all the time).  Also, when it is installing, will it respect my original partitions?  If it does, then presumably I can install it and access all of the files stored on the Windows side of the disk.  Is this straightforward enough to do?

If I backup the files on CD, I can then decide what to do - reinstall Windows (which will presumably obliterate everything) or stick with Ubuntu.  The idea of Ubuntu is tempting because I'm sick of these security problems - and apparently this latest issue is a bit easier to use and more plug & play.

Has Ubuntu got over this problem with USB modems - or should I go out and buy a router?

Sorry I've rambled on - Thanks!

---

### Post by PmDematagoda on 2007-12-03
You can reinstall Ubuntu on top of the old Ubuntu installation, doing this means:-

1) Your XP partition remains untouched.

2) Your GRUB will be reconfigured and everything would probably be fixed.

One question, how do you connect to the internet? Are you using an ADSL modem?

---

### Post by koleoptero on 2007-12-03
Your system crashes now, probably because the new motherboard has a completely different chipset than the previous one. It has happened to me in the past too. So yes you need to reinstall both.

When you boot from the Ubuntu CD it won't load Grub (that's the bootloader you see asking you which O.S. you want). It'll start anew, so you'll probably have no problem with it.

About the partitions: You need to be a little careful. At some point of the installation, ubuntu asks you what to do with the disk. It wil give you options to use the entire HDD which is wrong for you now. You will have to select manual. Then, when you press next, it will show you al the partitions on the hard drive. I assume that since you said you have one partition for ubuntu, you'll see there only one partition whose filesystem will be ext3. select to format that one (you will lose everything in it though) and then highlight it (click on it) and select "Edit" from the buttons below. In the dialog that appears, change the mount point of the partition to just / (only the slash thingy). Then click OK and continue with the installation.

You can also backup any data you had in your ubuntu installation (if you had any) from the live cd. Before you start the installer go from the menus above to "Places" --> "Computer". There it will show you all the hard drives you have. Just double click on them and they will be opened (or perhaps you'll have to right click on them first and select "mount"). When you find the partition that is for the ubuntu go to /home and search it's subfolders for your files. You can then copy them to a usb disk, burn them to a cd/dvd, or just copy them to the other partition.

After you install ubuntu you'll be able of course to access the windows partition, and any files in it. You can also reinstall windows in the other partition and have them both, although reinstalling windows after ubuntu will obliterate the bootloader (the thing that makes you choose / it won't obliterate everything) but then again you can reinstall that too and have both.

About the usb thing, I have a usb modem and it works fine. But it worked fine in feisty too. Try and search for solutions about your modem, you'll probably find something.

---

### Post by Bartender on 2007-12-03
You cannot just slip a different motherboard under a Windows HDD.  There are procedures for tricking Windows into accepting a new motherboard, but none of the methods are guaranteed.

I'm wondering if you've got other problems, like a failing power supply?

---

### Post by Stolengoat on 2007-12-03
Thanks to everyone who has replied!  I'm impressed at how quickly everyone seems to respond and how much effort they put into the responses!  Maybe this Ubuntu thing is a good idea, with this much support!

BARTENDER:  I told you I was a novice - lol!  I just stuck in a new motherboard because I didn't know what else to do - the power supply seems to be working fine at the moment, but no doubt I will encounter lots of problems as I get further.  I'm just impressed the thing even switched on!

KOLEOPTERO:  Many thanks for such a comprehensive reply - I'll try it tonite.

DEMATAGODA:  Again, many thanks.  About ADSL - I'm not too sure - I just connect my usb modem (Speedy I think) that came with my Tiscali package - all pretty straightforward under Windows, but it just didn't work before.  I might take the path of least resistance if I persevere with Ubuntu and use a router - I will see how it goes.

Thanks again everyone - I'll see how I get one tonite!

---

### Post by Sarteck on 2007-12-03
This might or might not have been your problem... but when I had a similar problem, but I could still access the GRUB menu (where you choose your OSes), all I had to do was tweak one character in the boot configuration.

See, it was trying to boot off of **hdd (0, 0)**, but when I changed it to **hdd (0, 1)** it worked fine.  :)

---

### Post by Bartender on 2007-12-04
You asked about USB modems -
Basically, the situation has not changed.  There are a handful of work-arounds and patches. like the Dell Conexant drivers.  Dell's drivers were originally written for 7.07 and broke when people updated to 7.10.  I believe they have new drivers out, but having a modem that breaks with each major update just doesn't sound like a good situation to me.
AFAIC external serial hardware modems still the best way to go.

---

### Post by OttifantSir on 2007-12-06
I don't know anything about USB dial-up modems' connectivity to Ubuntu. I do know however that my Motorola Surf Board Cable Modem only needed to be connected, and Ubuntu needed to be told through Networking that it should use the USB port as a network port. This was true for both 6.06 and 6.10. Since then I have gotten another computer and it has a true network port so I don't have to use the USB-choice anymore. But I would guess it still holds true.

---

### Post by jaybombalous on 2007-12-06
USB modems are still very sketchy, mostly because the drivers are third party proprietary drivers. So ubuntu/linux world can't get there hands on the code and therefor the end user suffers, blame your modem manufacture. 

Best modem to get to work with linux is one that is capable of hooking up through a ethernet cable that hooks to another ethernet card, either on-board or available in a PCI version. 

ethernet and PCI has been around for ages and so has the support, make life easier on yourself and buy good hardware.

---

### Post by Bartender on 2007-12-06
Stolen -
Hey, sorry,  I didn't read your post very carefully.  I was referring to USB dial-up modems.

---

### Post by irish_flu on 2007-12-06
Windows and Ubuntu will probably both act freaky with a new motherboard, unless it's exactly like (make, model, revision) your old motherboard.

The reason for this is that when you load an OS, it loads drivers and such specific to the hardware it finds.  It'd be far too heavy (impossible, even) to load drivers for all the potential hardware out there.  There are, of course, very generic drivers that will work with most anything, but drivers written for your specific hardware will almost always perform better.

If you change a piece of hardware like that, your OS suddenly finds itself with the wrong drivers.  I suggest backing up your data and reinstalling everything you want to keep.


BTW It's almost definitive that a virus did not destroy the BIOS on your old motherboard; in a decade of support, I've never heard of a virus that could do that.  As much as I'd like to, I can't blame Windows for it.  Sometimes they just get corrupted or smoked.  Sometimes it can be caused by power issues, as another poster noted, and other times they break all on their own.

---


---
title: "Installation"
date: 2008-02-21
forum: Absolute Beginner Talk
---

### Post by Alex. on 2008-02-21
Well I got ahold of a Feisty Fawn disc today, and am ready to install it alongside Windows XP, however I do not know how to begin the installation process..

Could someone please explain to me?

Many thanks.

:KS

---

### Post by wolfen69 on 2008-02-21
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by jan quark on 2008-02-21
great starting point

read carefully and ask whatever you want

[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

):P too late

---

### Post by northern lights on 2008-02-21
Pop the CD in your comp's drive, reboot - installation process should start.

If it doesn't, you got to add the CD-drive to the bootable devices in your BIOS.

If it's a more concrete problem, be so kind as to describe...

[EDIT]
A - too late as well
B - psychocats indeed a great resource
[/EDIT]

---

### Post by Alex. on 2008-02-21
Right, well I went into the BIOS menu and set it to detect CD-ROM Drives for OSs first, but Windows still loaded when I had the Feisty Fawn disc in.
:(

---

### Post by dstew on 2008-02-21
> I went into the BIOS menu and set it to detect CD-ROM Drives for OSsYour BIOS may not detect that the CD-ROM has a Linux operating system on it. You should look for a Boot Disk Selection or Order that you can change. I wouldn't count on a BIOS auto detecting the Live CD.

---

### Post by Alex. on 2008-02-21
I'm a complete n00b at PCs, so what sort of stuff am I looking for?

Would it also be a problem that I have two CDROM drives on my PC, and the live boot disk is placed in the lower one?

The other one is nonfunctioning.

---

### Post by dstew on 2008-02-21
For the BIOS setup, usually you press and hold one of the function keys during the early boot, usually when the BIOS flash screen appears. I depends on what kind of computer you have. Try F12 or F10 or F2, those are popular choices.

It probably doesn't matter that you have two CDROM drives in there. When you are installing, it is best to leave all your drives in place. If things don't work, you can usually reconfigure the software. Trying to correct problems by unplugging and plugging drives is not a good idea. If we can't get it booting by changing the BIOS settings, maybe then we can unplug or plug drives.

---

### Post by Alex. on 2008-02-22
[http://www.hiren.info/pages/bios-boot-cdrom](http://www.hiren.info/pages/bios-boot-cdrom)

Well I've followed all of the instructions in that page [my pc's BIOS style is featured in there] and still nothing. It's really getting to me now, is there any way I can force my PC to boot from disk?

---

### Post by northern lights on 2008-02-22
I wouldn't know, cause I don't know you're specific hardware either, but in case you can't get the CD to work at all, try [unetbootin]("http://sourceforge.net/project/showfiles.php?group_id=198821&package_id=243411") and install Ubuntu via the net.

Your Windows is functional, right? If so, download the .exe from there, run it once and reboot. Windows now won't boot automatically, instead you'll see a bootmenu with two options - "Boot Windows" or "Install Ubuntu". Select the latter - off you are. An internet connection is a prerequisite (wireless didn't work for during installation, btw). You're screen may flicker, cause the graphics driver that comes with the installation is utter crap - gotta suffer thru it - won't continue in Ubuntu. At the end, when prompted for additional software installations, make sure you mark "Ubuntu Desktop", otherwise you'll only have a commandline after installation. Any other software I'd install from within Ubuntu...

---

### Post by Alex. on 2008-02-22
Does this thing still let you do the dual boot?

---

### Post by northern lights on 2008-02-22
Of course. At the end of the installation it installs grub (bootloader), with a Windows entry (provided that you have it installed before).

---

### Post by Alex. on 2008-02-22
Okay,so I got to the partition bit and realised I didn't know what I was doing..

Could someone please explain to me what I need to do?


Sorry for being such a newbie :p

---

### Post by dstew on 2008-02-22
How many partitions do you have? Usually, you will only have one partition, and that will be for Windows, formatted as NTFS. The installer should detect this. To make room for your Ubuntu partitions, you need to shrink the NTFS partition. Shrink if from the right, to leave about 21 Gb of unallocated space after the partition. Then, from the unallocated space, create a 20Gb partition, formatted ext3, mount point /, and create a 1Gb partition of type swap. I like to use the Manual mode to do this, one step at a time. The only slightly risky part is shrinking the Windows partition. If you have a power failure or other glitch during the resize operation, that partition can be destroyed. Be sure to back up your important files, and have a re-installation plan ready in case the partition is destroyed. Hasn't happened to me yet in several tries, but it is possible. Also, defragment the Windows partition before shrinking, using the Windows Disk Tools (System menu I believe).

It takes a while to shrink the partition, maybe an hour or so if it is big.

---

### Post by northern lights on 2008-02-23
Wouldn't know what to add to dstew's post when it comes to the theory of the whole thing (unless maybe you have a really small harddrive, 5-7 gig can accomodate ubuntu, a few apps and a bit of personal data - obviously not ideal), however the methodology is a bit different with the unetbootin installer, since it does not have a gui for the partitioner - thus such things as "resizing from the right" don't really apply.

It all (the resizing of your ntfs partition(s) and creation of etx3 & swap) can be done with that installer only, you may choose to try, but since it involves the danger of screwing your Windows you might want to choose different. I hadn't really thought about the partitioning when I recommended unetbootin. Other than that it's still fairly easy and since you seem to have tried a lot with the CD, still the best option (since you're got the partitioning, it at least worked), but I'd do the resizing from within Windows also. If you know what ntfs partitions are and have win based partitioning software - awesome. If not, I know of "Partition Magic" & "Acronis something", but those are both non free.
--> May be someone else knows a windows open source partitioner?!

For the partitioning itself follow dstew instructions. If you do it from windows, the "from the right" approach applies again.

One more thing's important. I'd still not skip the unetbootin partitioning. I wouldn't trust either proprietary software to prep ext3 & swap right. Reformat both with the installer and afterwards set the ext3 as root (/).

Now you can continue the installation.

Reminder: Don't forget so select "Ubuntu Desktop" (Space Bar selects) towards the end, otherwise you'll end up installing again...

---


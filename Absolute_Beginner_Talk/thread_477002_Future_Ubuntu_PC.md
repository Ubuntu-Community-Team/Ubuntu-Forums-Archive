---
title: "Future Ubuntu PC"
date: 2007-06-17
forum: Absolute Beginner Talk
---

### Post by Morningzoo on 2007-06-17
My friend gave me an old PC while back that I planned to run Ubuntu on.  When I booted it up the bios were missing.  He told me he boot and nuked the hard drive.  Is there a site that I can possibly get Bios off online and send back my friends PC with Ubuntu?:D  Although this question really isnt regarding Ubuntu I would greatly appreciate some help. Thanks :)

---

### Post by alienexplorers on 2007-06-17
Are you sure the battery just did not die.

---

### Post by Morningzoo on 2007-06-17
No it ran perfectly fine before, after he cleaned the Harddrive using Boot and Nuke the Bios were gone (which is why he might of threw it at me :P)

---

### Post by alienexplorers on 2007-06-17
Sorry to hear that.  What a nice friend.

---

### Post by Morningzoo on 2007-06-17
Is there anyway I could get Bios for it and introduce him to Ubuntu?

---

### Post by bone43 on 2007-06-17
> **Morningzoo said:**
> Is there anyway I could get Bios for it and introduce him to Ubuntu?


You could try to flash the bios with the lastest version off a boot disk and see what that gets you but i dont know ive never heard of wipeing a bios.

---

### Post by wreti on 2007-06-17
Without knowing exactly what happened, it's hard to say. You may be able to download the latest firmware if you know the make and model of your motherboard. Checking the battery as mentioned is a good place to start. If that doesn't work you could flash your bios to reset it. With any luck one of those options will work and you won't have to buy a new mobo.:o

---

### Post by bone43 on 2007-06-17
> **Morningzoo said:**
> My friend gave me an old PC while back that I planned to run Ubuntu on.  When I booted it up the bios were missing.  He told me he boot and nuked the hard drive.  Is there a site that I can possibly get Bios off online and send back my friends PC with Ubuntu?:D  Although this question really isnt regarding Ubuntu I would greatly appreciate some help. Thanks :)

So when you boot up and hit f2 or maybe f12 there is nothing?
are you sure there is just no OS on the hardrive so that you end at a screen that says no operating sytem found?  :)

---

### Post by arvevans on 2007-06-17
If you can boot far enough to enter the BIOS (also called CMOS Setup), your BIOS is probably OK.  If you cannot see the hard drive, then either the drive is dead, or it's partitioning tables or the MBR (Master Boor Record) has been mutilated.  

If you know the motherboard manufacturer and model number it is sometimes possible to download a new BIOS flash program from the manufacturer or representative's web site.

If you can get the BIOS configuration screens to come up, the first screen usually shows the drives that are in your computer, and their size or type.  There is also usually a BIOS configuration screen that supports auto-detection of your hard drives.  If all else fails, this is worth a try.

If the hard drive partitioning or MBR is the problem (not that the hard drive is DEAD) you can sometimes recover them by re-setting the MBR data, and/or by rebuilding the partition table. _** NOTE**_:  [COLOR="Red"]This is a destructive procedure and will result in total loss of all data on the hard drive.[/COLOR].

To reset the MBR track:  Use either the Windows FDISK program or a Linux FDISK program.  Enter FDISK by typing "fdisk /mbr" at the command prompt.  Fdisk should start, write to the hard drive, and then exit (if you are not watching carefully you may think it has done nothing).  Do not do this procedure unless you are sure that the MBR is at fault.

If your MBR is OK, then the next step is to reset the Hard Disk (HD) partitioning tables.  Here you use a Linux "fdisk" program but this time at the command prompt you enter "fdisk /dev/hdb" with the :"b" in hdb pointing to your particular HD, it may be any letter, depending on how many disks you have and what type they might be.  In a computer with only one hard drive it is usually "/dev/hda" or "/dev/sda".

If you can get the computer to run using the Ubuntu Live CD, you can go to a terminal screen and work on your HD from there.
_._

---

### Post by bone43 on 2007-06-17
Though i recalled that name boot and nuke..

[http://dban.sourceforge.net/](http://dban.sourceforge.net/)

It only wipes the drive so bios should still be there unless somthing else has gone wrong which is possible.

---

### Post by Morningzoo on 2007-06-17
I flashed the bios and it is working now, thanks guys. Now back to my kubuntu install :)

---

### Post by steveneddy on 2007-06-17
Welcome back!!

[[IMG]http://img520.imageshack.us/img520/1544/postiig9bm6.gif[/IMG]](http://imageshack.us)

Just going for post count tonight, fellas. Looking for number 444.

---

### Post by Feba on 2007-06-17
If you have a flash motherboard, chances are you can find the latest BIOS on the manufacter's site.

---


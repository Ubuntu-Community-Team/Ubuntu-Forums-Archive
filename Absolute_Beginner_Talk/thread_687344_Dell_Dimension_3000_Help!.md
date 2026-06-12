---
title: "Dell Dimension 3000 Help!"
date: 2008-02-04
forum: Absolute Beginner Talk
---

### Post by ixcell on 2008-02-04
[FONT="Century Gothic"]Hi all,

I have a major problem. I have a semi-generic Dell Dimension 3000, which I have applied some upgrades to (see below), and I have also decided to change my OS, thinking that I can always go back to Windows XP using the Crtl+F11 command. Unfortunately, that was not the case for me.

I installed Kalyway OS X 10.5.1 on my Dell. First, I booted up GParted Live CD, erased my 7xGB Windows XP Home partition, then created a new blank FAT32 partition in its place. I then went ahead with the Kalyway install. In short, everything worked except for audio, and after 2.5 days of trying to get it fixed, I decided to try and get XP back. Unfortunately, my Ctrl+F11 trick wouldnt work. I believe the Kalyway installer uses the GRUB bootloader, but I am not sure.

I then decided to install Ubuntu. I once again booted GParted, removed the Kalyway partition, and added a new FAT32 partition of blank space. I then inserted my Ubuntu 7.10 CD, and proceeded to boot. The standard boot got stuck at loading scripts after telling me it couldnt figure out what monitor it had, so I rebooted into "Safe Graphics Mode". I then got to the Ubuntu desktop, and clicked install. I went through the wizard, until it asked me where I would like to install to. Since I didnt want Ubuntu to erase my System Restore partition, just in case I can get it working again, I clicked "manual". I then selected my newly created (blank) FAT32 partition, to no avail. The installer said that I needed to specify a "/" root partition or something along those lines...not what I was looking for.

My poor Dell is now operating system-less. I was hoping that some of you guys (and girls) could help be either a) get Ubuntu installed while keeping my Dell System Recovery Partition or b) Tell me how to fix my recovery partition to re-install Windows XP (I will then Dual-Boot XP and Ubuntu).

Now, I can use my Dell System Reovery Partition without Windows, right? Because if I cant, I'll just wipe the whole drive and install Ubuntu.

*sigh* If only Dell kept shipping their restore CD's, and not this stupid partition, all of this headache could have been avoided!

So, can anyone help me??

Thanks so much for any and all help!

P.S. Sorry about the long post!

As for my system specs, they are:
Dell Dimension 3000
Intel Pentium 4 @ 2.8GHz, 533MHz FSB, 1MB L2 Cache
1GB OCZ PC-3200 RAM (Upgraded from Dell's 512MB)
80GB Seagate 7,200RPM HD
Nvidia BFG Tech. GeForce FX 5500 O/C 256MB 128bit PCI (Not PCI-Express; added by me)
Sony CD-RW Drive
Lite-On DVD-ROM Drive (ordered from Dell, installed by me)
Samsung External USB DVD-RW Drive with Lightscribe (Added by me)
Dell E173p 17" Flat Panel Display
Logitech DiNovo Edge Keyboard
Logitech MX Revolution Mouse[/FONT]

---

### Post by jan quark on 2008-02-04
> I then selected my newly created (blank) FAT32 partition, to no avail. The installer said that I needed to specify a "/" root partition or something along those lines...not what I was looking for.


ubuntu needs and / root partition and a swap (recommend) partition in the file system format ext3

see these links for an installation guide

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

and ask for more help and advice

---

### Post by bumanie on 2008-02-04
You need to have both a / and a /swap partition, it is also often advised to have a separate /home partition also, this way if something becomes corrupted in /, you can reinstall without destroying your documents etc. It is also advisable to format the ubuntu partition into ext3, rather than fat32. Ubuntu now has ntfs-3g included in the kernel and can read/write to ntfs. If you want to return your computer to its original state, you rbest set would be to get test disk (an open source partition/data recovery program) and try it. If that is successful and you still want ubuntu, install and make a /, /swap and a /home partition. Test disk (a bootable live cd) apparently works very well for partition/data recovery.

---

### Post by ixcell on 2008-02-04
[FONT="Century Gothic"]So you want me to install Ubuntu, and then run Test Disk, and try to restore?

P.S. I downloaded the Linux version off of Test Disk's website, and tried to open it on Ubuntu using the Live CD, but the archive wouldnt work, so I am assuming I have to install Ubuntu to make this work?

I have NO os...when I turn on my computer, I get a b0 error.

Question: I have another one of these computers (ordered at the exact same time), that has a working Crtl+F11. Is there any way I can copy that computers MBR and load it onto mine, so that *my* Crtl+F11 will work?

Thanks for all of your support![/FONT]

---

### Post by bumanie on 2008-02-04
Test disk is a live cd (or at least there is a version that is a live cd), therefore, if you can get it to boot your computer, you should be able to recover what has been lost/deleted. I don't believe you need to install ubuntu first, because if you have to install an OS prior to using test disk, that would defeat the purpose of having a recovery program. Ensure you downloaded and burnt the live cd version.

---

### Post by dondad on 2008-02-04
> **bumanie said:**
> You need to have both a / and a /swap partition, it is also often advised to have a separate /home partition also, this way if something becomes corrupted in /, you can reinstall without destroying your documents etc. It is also advisable to format the ubuntu partition into ext3, rather than fat32. Ubuntu now has ntfs-3g included in the kernel and can read/write to ntfs. If you want to return your computer to its original state, you rbest set would be to get test disk (an open source partition/data recovery program) and try it. If that is successful and you still want ubuntu, install and make a /, /swap and a /home partition. Test disk (a bootable live cd) apparently works very well for partition/data recovery.

Go here and download the fixmbr disk. This will enable you to fix the mrb on your disk.

[http://www.softwaretipsandtricks.com/forum/windows-xp/27414-repair-mbr-without-xp-cd.html](http://www.softwaretipsandtricks.com/forum/windows-xp/27414-repair-mbr-without-xp-cd.html)

---

### Post by MinstrelBoy on 2008-02-04
You can get at the Dell system restore by press Ctrl F11 just after bootup. If Ctrl F11 doesn't work, you maybe able to restore the Dell mbr by following the instructions here.
[http://www.goodells.net/dellrestore/index.htm](http://www.goodells.net/dellrestore/index.htm)
It worked for me when my Ctrl F11 didn't work because the mbr had been messed up by vista.

---

### Post by bumanie on 2008-02-04
Try the F11 key first, I misread and thought you had lost the recovery or that it wasn't working. As the recovery partition is still in tact, try that first. The recent posts say it is F11 only, not ctrl F11.

---

### Post by ixcell on 2008-02-04
[FONT="Century Gothic"]The F11 and/or the Crtl+F11 doesnt work...I have tried it many times. The Kalyway intsaller installed the GRUB bootloader, which screwed my MBR, and the Crtl+F11 key is very picky, so it wont accpet the request. The Recovery Partition is fully intact. I can access it via the Ubuntu live CD. The .GHO file, as well as the .exe files are all there, however I cannot launch them as Ubuntu doesnt run .exe's.

The link to [www.goodells.com](www.goodells.com) is useful, however I have *no* OS, so I cannot run the applications that he mentions, and I also do not have a floppy drive. (Who has those anymore!? They are ancient!)

I am downloading another one of the Live CD's with TestDisk on it, as the last one I tried was quite confuing, and I couldnt launch the program. Hopefully this one will be more useful.[/FONT]

---

### Post by ixcell on 2008-02-04
[FONT="Century Gothic"]Ok, well I ran TestDisk, and it couldnt recover my Windows XP partition. It found the Dell Utility and Recovery partitions, which I knew were there still thanks to the Ubuntu Live CD, but nothing else.

Is there any way for me to boot from the .GHO or .exe files? Because I can save it to my external USB HD (as well as any other files), and burn it to a DVD (its 2GB). I was just wondering where I could get a boot CD that opens .GHO files? (.GHO files are from Norton Ghost 2003, and that program only lets me create Floppy Disks, of which I dont have a drive for and/or the disks themselves). Any suggestions?[/FONT]

---

### Post by DellCA on 2008-02-07
My name is Brad and I work at Dell headquarters in Round Rock, TX. I am not sure if you were able to repair the restore partition, but if not you can get the OS disk sent to you by following this link: [http://support.dell.com/support/topics/global.aspx/support/dellcare/en/backupcd_form?c=us&l=en&s=gen&redirect=1](http://support.dell.com/support/topics/global.aspx/support/dellcare/en/backupcd_form?c=us&l=en&s=gen&redirect=1) If you are outside of the US please let me know and I will see if there are other options. 

I hope this link helps out. Please let me know if you have any questions. 

Brad
Dell Customer Advocate

---


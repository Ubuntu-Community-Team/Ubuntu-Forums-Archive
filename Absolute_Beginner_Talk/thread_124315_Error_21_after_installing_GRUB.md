---
title: "Error 21 after installing GRUB"
date: 2006-02-01
forum: Absolute Beginner Talk
---

### Post by Kaustav on 2006-02-01
Hi all,
Total beginner to Ununtu. I have installed Ubuntu on an external Lacie BigBig (400Gb) which is hooked up to my desktop PC (Intel P3.4GHz, 2Gb RAM) via firewire 800.  I have reached the installation phase where GRUB is installed and the system reboots. I now see the following error message:

GRUB loading stage 1.5
GRUB loading, please wait
Error 21

I've read that sometimes Ubuntu cannot recognise drives if they are not listed in the BIOS, so I checked this and indeed the only disk that's mentioned in the devices list in BIOS is the internal system drive on the PC.  The main system drive has Windows XP installed on it which is why I installed Ubuntu on the external drive.  

Does anyone knows if :

a) I can fix the above problem, if so how? 
b) Can I still book in to XP or do I simply have to erase and reinstall XP?

Kaustav

---

### Post by Sokraates on 2006-02-01
If your BIOS does not support booting from Firewire, your best bet is to create a small boot-partition on the internal HD, so that GRUB can start up in the first place.

I guess Windows takes up the whole HD, so you will need to **defrag** (**very  **important) and then resize it to create a partition of about 50 MB. You can use a Win-app or any Linux live-cd for this. 

You can also use the ubuntu install CD. Just proceed till the partition manager starts. Then create a small partiton at the end of the disk. Ubuntu will warn you, if the partition will partially overwrite WinXP (at least it did in my case).

As for removing GRUB, use your WinXP-CD, open the recovery console (with "F2") and type "fixmbr".

Alternatively (if you only have a recovery disk provided by your vendor), use (or first download) a Win98 recovery disk. See [this](http://www.ubuntuforums.org/showthread.php?t=123684) link for a site and the commands you need.

You'll need to remove GRUB anyway, since you'll need to defrag your Windows.

---

### Post by az on 2006-02-01
Grub 21 means that linux can see your drives, but GRUB cannot.  If grub ran after the linux kernel was loaded into memory, it would be able to find the hard drive.  It does not.  It has to rely on what the bios is telling it and that<s why it can<t see your drive.

You can make a boot partition and put it on your first hard disk.  Reinstall grub and tell it to use that boot partition (for the kernel and initrd) and you will work around your problem.

To boot into XP, you will either need to do the above or remove grub from your MBR...  Rigth now, grub boots, but becomes lost.....

---

### Post by Kaustav on 2006-02-01
[QUOTE=Sokraates]You can also use the ubuntu install CD. Just proceed till the partition manager starts. Then create a small partiton at the end of the disk. Ubuntu will warn you, if the partition will partially overwrite WinXP (at least it did in my case).[/QUOTE]

Just want to check something on this point. You mentioned that defragging is very important in the previous paragraph to the above. I just want to clarify something. If I reboot with the Ubuntu install disk in my CD ROM drive and then let it run the installer up the disk partition phase and then allow the installer to create the 50Mb partition on my C drive, do I *still* need to defrag first? I assume the answer is yes, since if defragging is necessary for your first suggestion then it would also be applicable for the quoted advice above.

---

### Post by az on 2006-02-01
Parted (the partitioner that the installer uses) is very safe.  If you do not defrag and it is not able to move the data itself, it will refuse to do anything.  It is very unlikely that it will dammage your system even if you don't defrag.

---

### Post by Kaustav on 2006-02-01
Superb, thanks for speedy reply. About to try it now... stand by! :-)

---

### Post by Kaustav on 2006-02-01
I just wanted to check something before I create this 50Mb partition for GRUB to boot off.  I restarted the system with the installation CD in and got to the disk partition phase. This is the info that is printed out about my disk configuration:

SCSI1 (0,0,0)(sda) - 250.1GB ATA Maxtor 7Y250M0
  #1 primary 250.0GB :-) nfts /media/sda1
       pri/log 8.2MB FREE SPACE

SCSI3 (0,0,0)(sdb) - 400.1GB Lacie BigDisk Extreme
  #1 primary 393.9GB :-) ext3 /media/sdb1
  #5 logical 6.2GB swap swap

If I want to now create a 50MB partition on the 250GB internal disk, how do I proceed? When I click on #1 primary there appears to be no option to create a new partition. If I click on pri/log FREE SPACE it give me the option to create a new partition but obviously there's not enough disk space there.  Any advise would be much appreciated.

Once that's done, I've noticed that if I rerun the installer there is an option to reinstall GRUB on a partition of my chosing and so I presume that's what I should select to get grub on the new 50MB partition.

---

### Post by davmac on 2006-02-01
Kaustav,

There's a good article at [http://frontier05.blogspot.com/2006/01/installing-ubuntu-to-external-usb.html](http://frontier05.blogspot.com/2006/01/installing-ubuntu-to-external-usb.html) describing the trials and tribulations of getting Ubuntu to boot from an external usb drive.

Hope this helps,

Dave Mac

---

### Post by Kaustav on 2006-02-01
[http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm)

I tried to use the method on the above stated page to install Ubuntu on my internal C by using the installation CD to shrink my C drive to free up 50Gb to install Ubunutu on. However, Ununtu refused to allow me to shrink my C drive. The C drive is 250Gb in size. I put in 200Gb as the size I want to shrink to and hit "continue". I then got the summary page of my patition tables and still it said #1 primary 250.0GB.  I don't get it! Very frustrating.

---

### Post by az on 2006-02-01
I mentioned that on the -dev list once.  The message is misleading.  "new partition size" refers to the size of the new partition and not to the new size of the (old) partition.

Try entering 50 Gig.  I hope this is the problem.

---

### Post by coryisbored on 2006-02-01
I am attempting to install Ubuntu on a 100gb external hard drive.  My (my parent's) internal hard disk is only 20gb.  3.75gb are free.  Will you confirm this process or tell me exactly what to do?

From what i understand, i should defrag my system first.
Second, start the Ubuntu installation process.
When I get to the partition section, make a /boot partition on my internal hard disk of 50mb.  Do I name it /boot?  Is that an option?  I know very little about linux/unix style filesystems, I've simply come into contact with it before.  Then what?  Partition the 100gb however i desire?  What is a swap partition and where should it go?  I think I should have part of my external disk in linux-usable format and part in winxp-usable format.  I install GRUB on /boot?  Anything else.  Please respond ASAP.

Any help would be greatly appreciated.

Cory

---

### Post by Sokraates on 2006-02-02
Just to clean matters up: defraging Windows is necessary to maximize the space you can create a new partition on. 50 MB should be no problem, but you never know. Parted is a good tool and will warn you, if you will render your Win-partition unusable. With a defraged drive you will just be able to use more space.

@cory is bored:
When installing Ubuntu create a partition on you internal HD and define the mountpoint as "/boot". The folder "/boot" always contains GRUB (or LILO or what not). Only in this case the folder is a separate partition. 

Then partition the external drive to your liking. I advise creating one root-partion (mountpoint is "/"; all other folders stem from "/", e.g. "/boot") and one for your home-folder (mountpoint is "/home"). This way you can easily backup your private date by making a copy of this aprtition and you can even delete Ubuntu without destroying your data.

Also create a swap-partition (no mountpoint) which sould be about double the size of your RAM. If your RAM is full, the swap-partition will be used as a replacement by putting less used processes onto the HD and allocating faster RAM to processes, who are accessed often. This way your OS avoids constantly exchanging processess in the RAM, which would slow you machine down.

---

### Post by shawn524 on 2006-02-08
OK, I am getting a similar problem with this stuff. I'm getting the error 21 when I turn on my pc. I have and internal 60 gig hard drive that I've had windows on since i got my pc (it's a dell.) I just recentally purchased a 300 gig internal as well. I formatted it and set everything up so i could create 2 partitions. a 250gig partition and a 50 gig for using linux on.

I installed ubuntu on the 50 gig partition and it made a swap one as well. Everything looks like it should be working, but i get error 21 and don't know what to do. 

Could someone lent a hand please?

edit: also, im trying to make a 50 MB partition on my main internal HD but everytime i try to shrink the partition, it just goes back to 59.9 and wont let me shrink it.

---


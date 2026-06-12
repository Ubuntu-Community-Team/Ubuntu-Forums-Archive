---
title: "still want to try"
date: 2007-03-26
forum: Absolute Beginner Talk
---

### Post by ADH on 2007-03-26
Some folks may recall that, several months back, I tried to install Ubuntu 5.10 on my slave drive and did something wrong, as it installed Grub on my master disk and killed everything on there, which was eComStation and Win98SE.  After getting my partiition table back with the help of the author of drive utility DFSEE ([www.dfsee.com)](www.dfsee.com)), it turned out all my data was munged.  Fortunately, I had a backup, and was able to restore eCS.  Wasn't so lucky with Win98SE, but I rarely used it, anyway.

What follows is a paste of questions I posted elsewhere, but I also want to ask here (I'm looking for help everywhere.)

****

Il have the 6.06 alternate CD (if I get 6.06 installed, I figure Ubuntu will tell me there's an upgrade, and let me download and install it.) The Win98SE that was destroyed has been replaced with WinXP, which turned out to almost fill the partition, so I used DFSEE to move the partition and resize it from 3 gig to 10 gig - Airboot still found it, so I can boot eCS or XP, but still not Linux (though it recognizes Linux on the slave.)

So, what do I do? The 20 gig slave with 5.10 remains unaccessible from Airboot. I suppose if I tell the bios to boot from the slave, Grub will appear and send me on to Ubuntu Linux 5.10, which will then tell me to upgrade. Would doing this and allowing it to upgrade only touch the Linux drive, or would Grub again be installed on the master and screw things up again? Or would Grub see the other OSes on the master and a) know to leave that drive alone, and b) add the two OSes to its menu and allow me to boot eCS, XP. and Linux?  If I disable the master drive in bios, will Ubuntu leave it alone?

Does Linux have to have Grub to boot, or could I just install 6.06 on the slave without Grub, and either use Airboot or try to learn IBM's boot manager, which I'm told can be installed anywhere on the master drive, thus it wouldn't harm my eCS boot partition, which is at the beginning of the drive.

Thanks as always for any help.

As I said before. since my first experience I am very afraid of playing with Linux, though others who know more seem to do so without killing their systems. I really want to see what Linux is, though I am clueless about tar and all that stuff.

Important note, in case this was missed - while my master drive was hosed, I did have my computer fixing friend disconnect it (I'm disabled, so I couldn't), and installed Ubuntu 5.10, Grub and all, on the slave. I had to install it, as I needed Internet access to converse with Jan about DFSEE and what he'd suggest. I used Firefox that came with Ubuntu, and added Thunderbird for e-mail.

---

### Post by Cippa Lippa on 2007-03-26
I had to answer since I had exactly the same problem and I destroyed my winXP thanks to Ubuntu. :)
As far as I know grub won't touch your main hard drive once it is correctly installed in the slave drive. The thing that got me completely wrong was that if I put grub in the slave and then from the bios I boot from slave, the slave becomes hd0,0 and not hd1,0 as grub likes to think. Infact when you first install ubuntu your slave is hd1,0 because you haven't changed your bios settings...
Keep that in mind as that is what screwed me.
I have kubuntu now on my slave and I have upgraded distro in the meantime and still grub hasn't messed up with my other partitions.

Cheers



> **ADH said:**
> Some folks may recall that, several months back, I tried to install Ubuntu 5.10 on my slave drive and did something wrong, as it installed Grub on my master disk and killed everything on there, which was eComStation and Win98SE.  After getting my partiition table back with the help of the author of drive utility DFSEE ([www.dfsee.com)](www.dfsee.com)), it turned out all my data was munged.  Fortunately, I had a backup, and was able to restore eCS.  Wasn't so lucky with Win98SE, but I rarely used it, anyway.

What follows is a paste of questions I posted elsewhere, but I also want to ask here (I'm looking for help everywhere.)

****

Il have the 6.06 alternate CD (if I get 6.06 installed, I figure Ubuntu will tell me there's an upgrade, and let me download and install it.) The Win98SE that was destroyed has been replaced with WinXP, which turned out to almost fill the partition, so I used DFSEE to move the partition and resize it from 3 gig to 10 gig - Airboot still found it, so I can boot eCS or XP, but still not Linux (though it recognizes Linux on the slave.)

So, what do I do? The 20 gig slave with 5.10 remains unaccessible from Airboot. I suppose if I tell the bios to boot from the slave, Grub will appear and send me on to Ubuntu Linux 5.10, which will then tell me to upgrade. Would doing this and allowing it to upgrade only touch the Linux drive, or would Grub again be installed on the master and screw things up again? Or would Grub see the other OSes on the master and a) know to leave that drive alone, and b) add the two OSes to its menu and allow me to boot eCS, XP. and Linux?  If I disable the master drive in bios, will Ubuntu leave it alone?

Does Linux have to have Grub to boot, or could I just install 6.06 on the slave without Grub, and either use Airboot or try to learn IBM's boot manager, which I'm told can be installed anywhere on the master drive, thus it wouldn't harm my eCS boot partition, which is at the beginning of the drive.

Thanks as always for any help.

As I said before. since my first experience I am very afraid of playing with Linux, though others who know more seem to do so without killing their systems. I really want to see what Linux is, though I am clueless about tar and all that stuff.

Important note, in case this was missed - while my master drive was hosed, I did have my computer fixing friend disconnect it (I'm disabled, so I couldn't), and installed Ubuntu 5.10, Grub and all, on the slave. I had to install it, as I needed Internet access to converse with Jan about DFSEE and what he'd suggest. I used Firefox that came with Ubuntu, and added Thunderbird for e-mail.

---

### Post by igknighted on 2007-03-26
Avoid using Dapper!!!  The installer for Dapper does not have as many options.  The installer for Edgy (and Feisty) lets you choose on the very last step before install where to put grub.  There will be a (hd0) thats a blue link.  Click it, and it will let you edit it.  Make it say (hd1).  Then install, grub will be on the secondary drive.  This option is only available on 6.10 and newer.  If you use 6.06, disconnect the other HD and set up grub manually, or try the alternate CD.

---

### Post by ADH on 2007-03-26
I have the 6.06 Alternate CD.  Should I just download the latest version alternate CD before trying anything?

---

### Post by diskotek on 2007-03-26
... sounds better.

---

### Post by ADH on 2007-03-27
Do the newer versions have two CD images to choose from as well?  If so, do I choose Alternate?

Also, would I be better off (feel more familiar) with a version like Kubuntu?

---

### Post by Cippa Lippa on 2007-03-27
if you  are used to windows I feel kubuntu would be better since you can really do practically everything without ever seeing the terminal. It does look a lot like windows. If you don't care for having many options and be able to tweak everything then you can stay in ubuntu. I guess in the end you will want to try all three of the buntus.

I think the newer versions also have two cd images. I think you are safe enough going for the standard one

Cheers

---

### Post by ADH on 2007-03-31
I'm used to OS/2, actually.

I've downloaded and written the Ubuntu 6.10 CD.  To install it on my slave drive (over 5.10), without anything of Linux touching or even looking at my master drive, what steps do I follow?

---

### Post by Herman on 2007-03-31
Hello ADH,
You are will find all the information you will need about installing with the 'Alternate' CD and about  bootloaders.
You will need to either delete your old 5.10 partition or at least select it and re-format the partition as '/' for the new installation.
When you get to the point where you are asked if you would like to install the Grub bootloader, (to MBR of your first hard disk, choose <No>, and you will be given an opportunity to specify where else you might like GRUB. as illustrated [here]("http://users.bigpond.net.au/hermanzone/p6.htm#If_you_choose_No__to_Install_GRUBs_IPL_to_a_custom_location").      If you want GRUB's IPL installed to your second hard disk's MBR instead of your first one, type (hd1) or /dev/hdb on the line where you are asked to.
When you reboot, you can either go into your BIOS settings and swap the hard disks around something like as shown here,   [Changing the hard Disk Boot Priority]("http://www.users.bigpond.net.au/hermanzone/p1.htm#Changing_the_hard_Disk_Boot_Priority"), or you can press maybe your F8 key or your F12 key during boot-up for a list of bootable devices to choose from when booting.
I think you'll find that arrangement a little cumbersome and inconvenient after a while though. A better way would be to swap the hard drives around physically by the jumpers or cabling to make the Ubuntu disk master. Then use a pair of map commands to boot Windows from Grub. You'll still have your MBR with Windows bootlaoder's IPL in it on the second drive bootable by BIOS if you ever need that option. Here's a good link on how to [**Dualboot Two Hard Drives**]("http://www.ubuntuforums.org/showthread.php?t=179902"),  Also this one, [**Trying to Dual Boot, using two HD's**]("http://www.ubuntuforums.org/showthread.php?t=120994") Particularly note post #6. 
All this information and much more is already well covered and illustrated in my sig link web site. Enjoy.

Good luck with it
Regards, Herman  :)

---

### Post by ADH on 2007-06-30
I've managed to install 7.04 without killing everything else.  Grub is on the same partition *** root, not in the master boot record.

---


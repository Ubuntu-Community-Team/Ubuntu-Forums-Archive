---
title: "Dual Boot, Two SATA drives"
date: 2007-01-23
forum: Absolute Beginner Talk
---

### Post by Lowtech on 2007-01-23
After reading every thing I could get my hands on about this dual booting thing I think that I am now suffering from information overload.

Here’s my situation.  I have a PC with Windows XP Home installed on a SATA HDD that has been in use for some time.  I want a dual boot PC so I have acquired an additional SATA HDD for Ubuntu.

The additional HDD is brand new, not formatted.

After all of my reading I have decided to install Ubuntu using the alternate install CD rather than with the live CD so that I can assign where I want GRUB installed (I do not want it on the Windows MBR).

Assumption #1.  I will install the new SATA HDD and boot with the alternate install CD.  The alternate install CD will allow me to partition and format the new HDD and install GRUB on this new HDD.  Does Ubuntu prefer FAT32 to NTSF?

Assumption #2, I will have to set the boot order of my two SATA HDDs in BIOS in order to select the one with GRUB installed since these are SATA drives. 

I’ve read the guides and threads and my head is spinning but is what I’ve written above even remotely correct?

Thanks for any and all input.

---

### Post by mandrakethepenguin on 2007-01-23
The alternate CD will allow you to install Ubuntu on your new HD, and still dual-boot Windows.  Ubuntu does not prefer FAT32 or NTFS, in fact it uses neither. Instead, it uses a filesystem called ext3. And it should write to the Boot Record of the Master drive and configure Windows to boot as well by default so you won't have to mess with the BIOS.

---

### Post by mikewhatever on 2007-01-23
If I understand it correctly myself, you can install Ubuntu and GRUB on HD2, edit BIOS boot preferences to boot from HD2, and add some lines for Windows to GRUB menu.
Ubuntu can read and write from/to FAT32, but can only read NTFS. There is a work around to enable writing, and some people are quite happy with it.

---

### Post by Lowtech on 2007-01-23
> **mandrakethepenguin said:**
> The alternate CD will allow you to install Ubuntu on your new HD, and still dual-boot Windows.  Ubuntu does not prefer FAT32 or NTFS, in fact it uses neither. Instead, it uses a filesystem called ext3. And it should write to the Boot Record of the Master drive and configure Windows to boot as well by default so you won't have to mess with the BIOS.


I suppose I don't fully understand the boot order using two SATA drives since there aren't any jumper settings for master, slave, c/s.  Am I correct in the assumption that the GRUB boot loader will determine the master drive then?

Which brings me to an unrelated question.  My CPU is an AMD Athlon 64 X2 4200+.  I just paid a little closer attention than I previously had and noticed that one download is for AMD 64 bit CPUs (I thought it was for a 64 bit OS) , should I use this alternate over the Intel X86 version?

Thanks again,

---

### Post by mikewhatever on 2007-01-23
I think BIOS determines from which HD to boot.
Ubuntu 64bits for AMD is a general 64bits version. Only go for it, if you want to use 64bits. Otherwise get the x86.

---

### Post by mandrakethepenguin on 2007-01-23
BIOS Determines which HD to boot from based on order of IDE (IDE is labeled Master/Slave), or any of the ATA drives by which the order of how they are plugged into the motherboard. For example: 2 SATA HD's; One plugged into SATA1 on your motherboard (this would be the master). And the other one plugged into SATA2 (of course, this would be the slave).  BIOS automatically determines which one is the master and slave based on that information.

---

### Post by confused57 on 2007-01-23
What you might want to do is disconnect your SATA drive with Windows when you install Ubuntu...connect your new drive to the #1 SATA controller, this will be designated sda in Linux and hd0 in grub.  Once you have Ubuntu installed and working, reconnect your Windows SATA drive to SATA controller #2.  
Then you'd need to boot up Ubuntu and add an entry to your /boot/grub/menu.lst to boot Windows, similar to what's described here:
[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

---

### Post by FreakTech on 2007-01-23
I would have to agree with confused.  I did it this way with two SATA Drives and it worked wonderfully.  doing it this way takes the risk out of accidently installing the grub with the MBR.

---

### Post by Lowtech on 2007-01-23
> **FreakTech said:**
> I would have to agree with confused.  I did it this way with two SATA Drives and it worked wonderfully.  doing it this way takes the risk out of accidently installing the grub with the MBR.

OK, I'm going for it.

Thanks for the replies.

---

### Post by old_geekster on 2007-01-23
> **confused57 said:**
> What you might want to do is disconnect your SATA drive with Windows when you install Ubuntu...connect your new drive to the #1 SATA controller, this will be designated sda in Linux and hd0 in grub.  Once you have Ubuntu installed and working, reconnect your Windows SATA drive to SATA controller #2.  
Then you'd need to boot up Ubuntu and add an entry to your /boot/grub/menu.lst to boot Windows, similar to what's described here:
[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)
This is a good solution.  It will solve the problem of having GRUB in the MBR on your Windows drive.

With SATA drives, there is no Master or Slave designations.  They are both noted as Masters.  There is only one drive per cable.  My board has SATA 1,2,3, and 4.  Some boards have 6 or 8 ports.

---

### Post by Lowtech on 2007-01-24
OK, I have slept on it but I lied, I haven't gone for it just yet.

One more question popped up.

If I install Ubuntu in the manner confused described will this bugger up my drive letters?  The existing HDD is partitioned into two drives and you know that Winblows really likes being on C drive.  

Thanks again for all the replies so far.

---

### Post by Zzl1xndd on 2007-01-24
It shouldn't as only windows list them based on Letters. I know that I didnt have any problem, can someone back me up on this or am i out to lunch?

---

### Post by old_geekster on 2007-01-24
> **Lowtech said:**
> OK, I have slept on it but I lied, I haven't gone for it just yet.

One more question popped up.

If I install Ubuntu in the manner confused described will this bugger up my drive letters?  The existing HDD is partitioned into two drives and you know that Winblows really likes being on C drive.  

Thanks again for all the replies so far.
No, because technically Windows does not recognize ext3 partions.  In fact, my second drive is represented in Device Management, but shows that it is all Free Space.

---

### Post by Lowtech on 2007-01-24
Thanks again to all who answered my questions.

I followed confused's link and the install went beautifully smooth.  I now have a dual boot PC :D .

---

### Post by kevinf311 on 2007-01-26
I'm glad I came across this thread. My roommate just built a computer with an AM2 socket and SATA drives. He hasn't installed anything on it because he wanted Vista (which won't arrive until next week I think). 

He was wavering between setting up in Raid0 or Raid1. The drives are 250GB apiece so having a mirror would be cool. Three of the 6 guys here use Ubuntu (we're working on another guy too), and none of us save the one guy planned on getting Vista. One of the guys and I beta tested Vista and I was not impressed with it, and became less impressed after researching it. I've been kinda FUD'ing the guy who just bough it and now he's thinking about dual booting Vista and Ubuntu.

I was overjoyed that the house had another convert, but I wanted to make sure that his set-up would provide for a fairly painless Linux install (as I let him know which components would be down-mixed by Vista's DRM to help with his purchases). This puts my mind to ease.

As for the ext3 file format. there is now a freeware program called [FS-Driver]("http://www.fs-driver.org/") that allows windows to read/write to ext2 (which is ext3 without the Journaling). I would recommend you set up your partitions with a separate /home partition:

sda0[--Ubuntu--][------------------/home-------------][swap]
sda1[------------------------Windows--------------------------]

This will keep all of your data intact if you need to completely re-install an Operating system. You can use the /home partition to back up important files on Windows, too using that program. This set-up (on one drive) has already proven useful and time/hassle saving for me as I just recently buggered up my system 2 or 3 times in a row :rolleyes: 

Sorry for the marathon post starting with rather off-topic info, but I do hope that the FS-Driver and partition set-up prove useful to you!

---

### Post by Lowtech on 2007-01-26
kevin, 

Thanks for the link, I'll certainly give this a shot as I become more accustom to Linux and the need to xfer files back and forth arises.  I want to get to the point to where Win Xp is in the PC strictly for the games.

Yeah, I would have definitely preferred to have a separate Home partition, but I really didn't know any better at the time of the initial install so I ended up with Unbuntu and the swap partition.  In time I'll probably use gparted (or whatever it's called) to create that new Home partition.  

As far as Vista goes, if I ever do upgrade it'll be after SP1 at the earliest for sure.

---


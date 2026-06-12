---
title: "How do I install Ubuntu on an external Hard Drive on a Mac"
date: 2010-05-20
forum: Apple Hardware Users
---

### Post by hilikustue on 2010-05-20
Hi there, 

I use a Macbook Pro Mid 2009 and at my new work I have to use Linux. They use bith Ubuntu and Suse.
I have a spare USB external Hard Drive on which I would like to install both Systems (Suse and Ubuntu) just for playing around and getting to know the system better.
I don't want to install Linux on my internal HDD and would like to keep the Book itself OSX only.

How do I do that best?

I already got the necessary Suse and Ubuntu images to install (and will burn them tomorrow). Do I have to prepare the external drive in a special way or OSX?

Thank you very much.

---

### Post by cariboo on 2010-05-20
Moved to Apple Users, as you'll probably get better help here.

---

### Post by tgalati4 on 2010-05-20
Just open the disk utility in the Mac Applications folder.  It may be in a utilities folder.

Select the disk and partition it (probably 3 partitions, one for Ubuntu, one for SUSE, one small one for swap.)

Then select the partition and "Format as:" Then select ext3 and apply.  The swap partition doesn't need to be formatted.  You want your swap partition to be roughly double your RAM size.

Must be rough to be forced to use Linux at work.

---

### Post by srs5694 on 2010-05-20
Apple uses the GUID Parition Table (GPT) partitioning system, vs. the Master Boot Record (MBR) system that's used on most PCs. Although you can use an MBR disk with Apple hardware, it's probably better to stick with GPT.

When you use Apple's Disk Utility, there's an advanced option hidden away on an options screen somewhere to set the disk type: GPT, MBR, or the Apple Partition Map (APM) system used on PowerPC-based Macs. You can use Disk Utility to set up the disk, as tgalati4 suggests, but you should check that it uses GPT. Alternatively, you can use a Linux partitioner such as GParted and locate the equivalent option. My own text-mode [GPT fdisk,](http://www.rodsbooks.com/gdisk/) available for both Linux and OS X, also sets up GPT disks. IMHO, Apple's Disk Utility is very limited and awkward, so my preference would be to use GNU Parted, GParted, or gdisk for this job.

One quirk of Apple's Disk Utility is that if you tell it to put a FAT filesystem on any partition, it'll convert the disk into a [hybrid MBR](http://www.rodsbooks.com/gdisk/hybrid.html) disk, which is an ugly and dangerous hybrid of GPT and MBR. Apple's Boot Camp relies heavily on hybrid MBRs to boot Windows. I don't believe this is necessary to dual-boot Linux and OS X on a Mac, but my knowledge of the details of such configurations is a bit foggy. Thus, I recommend you research this more, and avoid a hybrid MBR configuration if possible.

On BIOS-based computers, the Linux GRUB 2 boot loader works best if you've got a [BIOS Boot Partition](http://grub.enbug.org/BIOS_Boot_Partition) on a GPT disk. I don't know if this is useful on an EFI-based system like a Mac, though. If in doubt, you might as well create a BIOS Boot Partition; the worst-case scenario is that you'll lose a tiny bit of disk space. You'll need GNU Parted, gdisk, or possibly GParted to create a BIOS Boot Partition; Apple's Disk Utility won't create one. I don't think an EFI System Partition is strictly necessary, since one will be present on your main disk, but Apple's Disk Utility will create one automatically. Creating one manually in another utility will just consume a small amount of disk space, so to be completely safe, you might as well create one.

---

### Post by hilikustue on 2010-05-21
Hi again. 

I partitioned the external HDD to 4 Partitions (2 50GB for Suse und Ubuntu, a 10GB for Swap and a 120GB for Data for both systems) in the Disk Utility in OSX. So far so good. 

I ran the Ubuntu setup but how do I set it up to "use this partition for swap and this one for the rest (the root thingy?)"

I canceled and ran the Suse Setup next. I managed to tell the setup "use the small one for swap and this one as root", so that sounds correct. One step further though it tells me i wants to install Grub on the internal disk on my Mac. Will this kill my OSX installation? Or is that just fine and I won't see a difference unlesse I press "alt" while booting to choose a volume to boot from?

---

### Post by linuxopjemac on 2010-05-21
Don't install Grub on your internal disk. I would try to put it on the external one (advanced setup?)

---

### Post by hilikustue on 2010-05-21
So the End Game would be like this:

I power on my Macbook, the "Mac Boot Loader" opens when I press "alt" and I can choose my external hard drive where Grub loads and I can then chose between Suse and Ubuntu.

Is that about right?

---

### Post by linuxopjemac on 2010-05-21
yep

---

### Post by hilikustue on 2010-05-21
Ok I successfully installed Suse on the partition I wanted it to be and Grub on the external drive (HOORRAAYYY). After the Installation it booted into Suse and I played for 5 minutes. 
Then I wanted to check my OSX Installation, so I hit reboot and didn't press any keys during booting and I had OSX again. SO far so good.

Problem now: When I power up the thing and press "alt" for the "Mac Boot Loader" it only shows me the Mac HD to boot from, no Suse or external drive whatsoever.

---

### Post by freesparks on 2010-05-21
> **tgalati4 said:**
> Just open the disk utility in the Mac Applications folder.  It may be in a utilities folder.

Select the disk and partition it (probably 3 partitions, one for Ubuntu, one for SUSE, one small one for swap.)

Then select the partition and "Format as:" Then select ext3 and apply.  The swap partition doesn't need to be formatted.  You want your swap partition to be roughly double your RAM size.

Must be rough to be forced to use Linux at work.
Hello tgalati4,


     Just out of curiosity, why do you have to-- > You want your swap partition to be roughly double your RAM size?

So for example, if my system has 4GB of RAMS, does that mean my swap partition has to be 8GB?

Any further insight on this would be greatly appreciated.  I am one of these people who are forced to use Linux, however, so far I'm hooked.  I got some really good books on it, [ ]("http://www.amazon.com/Practical-Guide-Commands-Editors-Programming/dp/0131367366/ref=sr_1_27?ie=UTF8&s=books&qid=1274471433&sr=8-27")             [ Practical Guide to Linux Commands, Editors, and Shell Programming, A (2nd Edition)]("http://www.amazon.com/Practical-Guide-Commands-Editors-Programming/dp/0131367366/ref=sr_1_27?ie=UTF8&s=books&qid=1274471433&sr=8-27") by [Mark G. Sobell]("http://www.amazon.com/Mark-G.-Sobell/e/B000APJW04/ref=sr_ntt_srch_lnk_11?_encoding=UTF8&qid=1274471433&sr=8-27")
,
  and I also got a book on Ubuntu specifically.  Anyway, so far this forum has been a great resource.  Anyhelp on this would be greatly appreciated.

Best Regards,

freesparks

---

### Post by freesparks on 2010-05-21
Hello hilikustur,

    Are you still experiencing that problem with your MAC?  I tried to install Ubuntu 9.10 on an external harddrive like yourself and was unsuccessful.  The only things I was able to do was to install Ubuntu 9.10 externally using my PC laptop, and 9.10 internally on my MAC dualboot.  We probably have the exact same machine so I would still like to know which version of Ubuntu you are installing externally 9.10 or 10.04.

Best Regards,

freesparks

---

### Post by linuxopjemac on 2010-05-22
It should be possible, have a look here:
[http://mac.linux.be/content/installing-ubuntu-910-karmic-external-fw-drive-mac-g4-ppc-0](http://mac.linux.be/content/installing-ubuntu-910-karmic-external-fw-drive-mac-g4-ppc-0)

---

### Post by tmaspoopdek on 2010-05-22
I'm trying this on my MacBook Pro right now. Let's hope I can get something up and give you some tips  if I find a way around Apple's requirement for the external disc to have OSX on it.

---

### Post by tmaspoopdek on 2010-05-22
Alright, before I look in every nook and cranny of the filesystem, have you tried rEFIt? I'm assuming not, since you asked this question. Here's a link to the website. [URL="http://refit.sourceforge.net/"]http://refit.sourceforge.net/
[/URL] Enjoy! I think I remember messing around with this and having it work quite well. It should find ALL OS installations, not just mac.

UPDATE: I have rEFIt up and running with ubuntu on an external disk, the downside is that it is labeled simply as linux. I'm trying to change the label, if anyone knows how please let me know. I personally had to run some commands to get my computer to boot rEFIt at all, so if yours doesn't work don't hesitate to ask.

---

### Post by tmaspoopdek on 2010-05-23
Alright, I can confirm that rEFIt should fix your problem. However, I'm not sure that Ubuntu will actually run on your computer with this setup. I also have a 2009 MacBook Pro and it doesn't work for me, just comes up with a black screen and that underscore-style cursor. Let me know if you get any further than that.

---

### Post by tmaspoopdek on 2010-05-23
> **linuxopjemac said:**
> It should be possible, have a look here:
[http://mac.linux.be/content/installing-ubuntu-910-karmic-external-fw-drive-mac-g4-ppc-0](http://mac.linux.be/content/installing-ubuntu-910-karmic-external-fw-drive-mac-g4-ppc-0)

That's a PPC though.

---

### Post by tmaspoopdek on 2010-05-23
OK, I've been working on this all day and I haven't quite gotten it working as of yet. I think you need to install GRUB on the MBR of your internal HD. I'll get back to you once I've done this, but I strongly recommend that you hold off until I tell you more or make a backup of it before you make changes.

---

### Post by tmaspoopdek on 2010-05-23
OK, here's the verdict: You can't. I have honestly tried EVERYTHING I could find to get this running, and you can't. MacBook Pros just don't support booting from USB (I guess you could call that a MacBook con lol), so there's not a good way to do it. At least not until someone develops some hardware or apple updates the firmware, we're screwed (yes, I'm in the same boat. MacBook Pro mid-2009). Happy trails, and I hope we end up  with a good way of doing this! Oh, and don't hesitate to ask if you have another question.

---

### Post by freesparks on 2010-05-27
Hello [tmaspoopdek]("http://ubuntuforums.org/member.php?u=1040973"),

  I had tried it as well by installing reFit, and going through the tutorial that I found on the user forums and I had no luck as well.  But as this websites states under Apple Users, I believe some have succeeded at doing it.  I'm sorry I didn't reply to you, I tend to give up easily.  And, I felt like noone was responding.  I wish I had enlough money to buy a MAC that I can hack away at, but i can't afford to experiment right now because I have a lot of deadlines with work and I can't afford to tinker with my system.  What's interesting though is I did 100% successfully cloned my MAC internal harddrive running OSX ver:10.6, and I was able to boot from the clone which is an external USB drive.  This is what I find so interesting, so if that worked, there is no reason why Ubuntu shouldn't be able to be booted from an external USB harddrive.  Someone posted instructions to doing it on PPC MAC, but i was told that's different.

Best Regards,

freesparks

P.S.  Please keep in touch, you are very kind in insisting that I ask you any questions.  I really appreciate that.

---

### Post by DagMan on 2010-05-28
The way I did it (and using the earlier grub, opposed to the newer grub 2, for simplicity) was to put put a very small ext3 partition at the end of the drive, put the /boot folder there with grub in it and manually edit the menu.lst file.  
You could just as easily make a 500 megabyte partition at the end of the drive and specify it as your /boot partition when you install. 

In either case, you can also install grub to this partition and after running refit, syncing the partition tables, rebooting to mac, rebooting entirely, etc etc etc... grub will pass the system over to the USB drive.



For the person who had stated having a blinking cursor with a blank screen.  I was previously getting that and found that I had to sync the tables with refit and even if they were fine and didn't need it, I still needed to boot into OS X and do complete login then restart again.  When this didn't work I tried the option key instead of the refit boot menu and when that didn't work, a combination of all of the above until it did work.  Its always been a stubborn process to get the bootloader going.
This said, however, I've read that newer models than mine just don't want to boot Linux, so my experience is unique to my machine if I'm to take that as true.

---

### Post by freesparks on 2010-05-29
Hello Dagman,

 Would you be so kind to tell us what version of Mac Book Pro you have.  Thank you so much for the feedback!!

Best Regards,

freesparks

---

### Post by untmdsprt on 2010-06-05
I was hoping someone would have gotten an easier step by step out of this because I too would love to use my external drive for different versions of Linux.

I had tried before with rEFIt and my white Macbook, but got the error that my system didn't support booting from an external drive.

---


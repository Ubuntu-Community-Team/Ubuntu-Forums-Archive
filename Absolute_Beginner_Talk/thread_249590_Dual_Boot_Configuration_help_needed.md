---
title: "Dual Boot Configuration help needed"
date: 2006-09-02
forum: Absolute Beginner Talk
---

### Post by 3rr0r on 2006-09-02
Hi,
  I have been trying to get familiar with linux, so about a month ago I decided to try running ubuntu from cd.  I've been fiddling with it here and there, and I really want to install it onto my hdd.

Question is, I know you need to make a partition, but I am not sure where that app is on ubuntu.  Also, I see a lot of people posting scripts for lilo or grub.  I really have no idea how to go about setting up a dual boot system on my laptop.  It currently has XP on it, and I would LOVE to install Ubuntu.

Perhaps a quick walkthrough, or even a link to a walkthrough would be marvelous!  Thank you very much.

---

### Post by taurus on 2006-09-02
If you only one harddrive and have XP on it, boot it up and defrag the hell out of it, running it a few times...  Then, boot the LiveCD and use gparted resize your harddrive, leaving some space for Ubuntu.  As with anything else, please make sure you backup your important files on XP first before resizing your harddrive because bad things can happen but shouldn't if you know what you are doing with gparted.  And when you get to the screen about boot, install GRUB on MBR since it will take care of booting XP and Ubuntu at the same time.  So basically, just follow the instructions on the screen and if you're not sure about something, just post it back here with the exactly questions or problems.

---

### Post by Raistlin355 on 2006-09-02
The partitioner (Gparted) will run automatically when you go to install the software.  Just make sure you choose "Manually Edit the Partition table" and don't leave it set for the first option or it will take over your hard drive. Hope this helps!!!

---

### Post by benfindlay on 2006-09-02
GRUB sets itself up automatically, you only need to edit it for minor changes, such as changing the default booting OS, and also how long it puses before booting the default OS.

As for partitioning, if you've got a spare partition on your computer it will allow you to install into that partition during the main install, no need to fiddle about with any complex partitioning. Just make sure to choose MANUAL partitioning during setup!

If you only have 1 partition (and Windows is installed into it) then you will have difficulties. In my expreience you will be better off backing up all your documents and files, reformatting, and reinstalling windows into a partition on your hard drive. Programs like partition magic have an alarming tendency to balls up your OS when you use it on the drive Windows is installed into.

A fresh windows install will also easily let you set up several partitions during the installation process.

Hope this helps!

EDIT: from reading a few posts, it seems that GPARTED (the partitioning tool in the ubuntu installer) has much more success when editing partition sizes of non-empty drives than programs like partition magic!

---

### Post by 3rr0r on 2006-09-02
Oh man!  My best bet is to format the drive and create the seperate partitions?  I just spent almost 6 hours removing all the trash software, updating xp, installing nero/ms office xp, norton internet security and updating all of that to only have to erase it all.

I'll run defrag on my laptop 3x before I attempt this.  From what I gather, I use Gparted to create a new partition to install Unbuntu on.  Make sure I do MANUAL, and install GRUB and MBR (what is MBR)?  

Also, do I need to set this partition to a certain type?  I have seen people refer to a linux partition versus a windows partition as something vs ntfs (windows).  Thank you very much for the support to the newb.

---

### Post by taurus on 2006-09-02
When you use gparted from the LiveCD to resize your harddrive, it will set it to the right filesystem for you; otherwise, set it to ext3.

MBR = Master Boot Record

---

### Post by 3rr0r on 2006-09-02
Almost done with the first defrag... 2 more to go.

Let me just say, I am very excited about ubuntu and really want to thank you guys for your patience.  I am really taken back by how helpful people are, I love it!  I hope soon I will become more familiar and be able to help people as well.  

I will keep you guys updated about how my dual boot is going.  2nd defrag inc!

---

### Post by eternalis on 2006-09-02
> Oh man! My best bet is to format the drive and create the seperate partitions? I just spent almost 6 hours removing all the trash software, updating xp, installing nero/ms office xp, norton internet security and updating all of that to only have to erase it all.
You dont have to delete anything, just resize your partition. Your data will still be kept intact.

---

### Post by 3rr0r on 2006-09-02
Okay, I decided I wanted to create 4 partitions.

I have the following:

/dev/sda1   21.5 GB   ntfs   boot
new #1      21.5 GB   ext3
new #2      21.5 GB   ext3
new #3      10.0 GB   fat32


on new#1 I want to put mandrake
new #2 is for ubuntu
new #3 is so I can place files on this partition to transfer them between linux base and windows base.  I know there are programs out there, but for now I'll just try this method.

So, do I confirm the partitions now?  I want to make sure I have it right.  I saw that there was a linux-swap type... do I need to make one of those ?  Thanks again!

---

### Post by taurus on 2006-09-02
Well, I guess you don't want to have a swap partition for both Mandy and Ubuntu!  If you want to share a partition between Linux and XP, make sure you format it as fat32 (or vfat) so you can read and write to it from both operating systems.

If you have 1GB of RAM, chances are you will not need a swap partition BUT it is always nice to have one...

---

### Post by 3rr0r on 2006-09-02
> **taurus said:**
> Well, I guess you don't want to have a swap partition for both Mandy and Ubuntu!  If you want to share a partition between Linux and XP, make sure you format it as fat32 (or vfat) so you can read and write to it from both operating systems.

If you have 1GB of RAM, chances are you will not need a swap partition BUT it is always nice to have one...

what is a swap partition between mandrake and ubuntu? Like, what would it do/purpose?  I am not familiar with what a linux-swap is.

---

### Post by RRS on 2006-09-02
> **3rr0r said:**
> Oh man!  My best bet is to format the drive and create the seperate partitions?
Don't format the drive, the partitioning tool in the installer will simply downsize the windows partition and create a new partition in the leftover space. Your existing windows installation will be fine.

> I just spent almost 6 hours removing all the trash software, updating xp, installing nero/ms office xp, norton internet security and updating all of that to only have to erase it all.
All that work will make the defragging and resizing work better, and it probably helps windows run better too :)

> I'll run defrag on my laptop 3x before I attempt this.  From what I gather, I use Gparted to create a new partition to install Unbuntu on.  Make sure I do MANUAL, and install GRUB and MBR (what is MBR)?  

Also, do I need to set this partition to a certain type?  I have seen people refer to a linux partition versus a windows partition as something vs ntfs (windows).  Thank you very much for the support to the newb.

You can run gparted from the live cd before installing, it sometimes works better that way. It's under System>Administration>Gnome Partition Editor. Then when installing use the "Manually Edit Partitions" option to choose your mount points, the installer will make suggestions along the way, so don't worry.

The MBR is at the beginning of the hard drive and tells the OS to boot. The live cd will automatically install Grub (the Linux boot loader) into the MBR so it will give you the choice of booting Ubuntu or windows when the computer starts.

Windows XP normally uses the NTFS file system. You'll need to format the new partition to Ext3 for ubuntu, so yes, you'll have two different file systems for the two partitions. Linux also works better with what's called a swap partition. Usually this is one to one and a half the size of your ram. You can also create this ahead of time with gparted, or the installer will remind you one is needed and ask to create it for you.

If you have enough disc space you might want to create an additional partition formatted to Fat32 to store files in that you want to share between Ubuntu and windows, 5 to 10g is usually plenty.

I hope I provided enough info to answer your questions.I highly recommend [this guide]("http://psychocats.net/ubuntu/installing.html") for installation instructions.

Lastly, don't worry, the whole proccess is much easier then it sounds and well worth the effort.

---

### Post by 3rr0r on 2006-09-02
Thank you, I'm going to make a linux swap (decrease the fat32 partition) and then confirm them from there.  I'll post as I go along.  

(using 2 comps)

---

### Post by 3rr0r on 2006-09-02
Okay... trouble. 

It made 4 primary partitions as follows

/dev/sda1 ntfs   (xp)
/dev/sda2 ext3   (mandrake)
/dev/sda3 ext3   (ubuntu)
/dev/sda4 linux-swap

unallocated 6.42 gb

I try to create new partition from this unallocated portion (i want to make a fat32) but it says, "It is not possible to create more than 4 primary partitions.  If you want more partitions you should first create an extended partition.  Such a partition can contain other partitions.


So, how do I create that with this unallocated data?

---

### Post by taurus on 2006-09-02
You can only have 4 primary partitions and if you want more than 4, then you need to make one of the primaries into extended partition.  Then, you can have as many as logical partitions under extended partitions you want.  In other words, your harddrive should look something like this

/dev/sda1 -> XP (NTFS)
/dev/sda2 -> Mandy (ext3)
/dev/sda3 -> Ubuntu (ext3)
/dev/sda5 -> swap (for both Mandy & Ubuntu)
/dev/sda6 -> share (fat32)

---

### Post by 3rr0r on 2006-09-02
mounting the drives.

are they supposed to be /media/hdaX 
it gives me multiple options... not really sure which to choose? (/home,.boot, /usr, /var)

---

### Post by taurus on 2006-09-02
Make sure you put / on /dev/sda3.  That's the main thing.  Everything else you can add later in /etc/fstab once you are done installing it...

---

### Post by 3rr0r on 2006-09-02
Ya, I made sure that was labeled as "/" to indicate it as the root (main install for ubuntu?) right.  The whole mounting thing is a little confusing to me.  That, and this GRUB thing.  

I see that it is linux's counterpart to windows MBR.  I'm installing in the following order:

1. xp
2. ubuntu
3. mandrake

I'm hoping mandrake will also install the GRUB or else I think I will have boot selection problems.

Will update when the ubuntu install is done.

---

### Post by taurus on 2006-09-02
I recommand you install XP first.  Then, you can install either Mandy or Ubuntu and each one will overwrite the MBR with it own GRUB which is fine.  However, I think you should install Mandy next and then Ubuntu last...  Have Ubuntu install GRUB on MBR and you can boot all three OSes when you turn your computer on.

---

### Post by confused57 on 2006-09-02
> **taurus said:**
> I recommand you install XP first.  Then, you can install either Mandy or Ubuntu and each one will overwrite the MBR with it own GRUB which is fine.  However, I think you should install Mandy next and then Ubuntu last...  Have Ubuntu install GRUB on MBR and you can boot all three OSes when you turn your computer on.

I agree with taurus...XP, Mandy, then Ubuntu.  What you might want to do after installing Mandy is to go into /boot/grub/menu.lst and write down the exact entry to boot Mandy...just in case Ubuntu doesn't automatically add Mandy, you can add it manually to Ubuntu's /boot/grub/menu.lst.  Ubuntu will more than likely add both XP and Mandy...

---

### Post by 3rr0r on 2006-09-02
I didn't refresh until after ubuntu finished...

So now on my desktop I see the following:

ROOT  (20 gb)
SDA4  (fat 32)
SDA5  (mandy)

So, I guess I just load in the mandy dvd and run install.  Do I have to remount the drives or?

---

### Post by 3rr0r on 2006-09-02
Ok... mandy says the following on install:

Source: /boot  (i'm guessing source of files from cd)

Install to: /mnt/sda5  (made sure this was the write one that is empty... ie: not xp, not fat32, and not ubuntu)

Write MBR to: /dev/sda


This is the part where I am confused.  Write MBR to ??? Is that right?  There is no other selection, but I can type over it with what I want.  :confused:

---

### Post by Cynical on 2006-09-02
Its asking which hard drive to write the MBR to. The MBR is located in the boot sector of every hard drive. If you are installing to /dev/sda then yes you want to write the MBR to /dev/sda.

---

### Post by confused57 on 2006-09-02
> **3rr0r said:**
> Ok... mandy says the following on install:

Source: /boot  (i'm guessing source of files from cd)

Install to: /mnt/sda5  (made sure this was the write one that is empty... ie: not xp, not fat32, and not ubuntu)

Write MBR to: /dev/sda


This is the part where I am confused.  Write MBR to ??? Is that right?  There is no other selection, but I can type over it with what I want.  :confused:
Since you installed Ubuntu 2nd, my original suggestion still applies; but boot into Ubuntu and write down the /boot/grub/menu.lst entry used to boot Ubuntu, in case you need to add it manually to the Mandy grub...which, yes, you would install to /dev/sda.
  I once installed Mepis on a 2nd partition, Dapper was on the 1st partition...Mepis installed grub to the mbr, but didn't automatically add an entry to boot Dapper.  I had to manually add an entry to Mepis /boot/grub/menu.lst to boot Dapper.

---

### Post by 3rr0r on 2006-09-02
Okay, I copied it all down on paper and even managed to use gedit to copy paste it into a new doc and saved it on the hd.  Now for the Mandy install. 

I kinda' see what is going on.  The boot folder must be something you do not want to accidently mess with.

---

### Post by 3rr0r on 2006-09-03
K, got mandy installed.... but now when it boots up, it goes straight to mandy.  It doesn't even show xp or ubuntu.

I'm guessing this has something to do with GRUB and the MBR.  I don't really know what it is though, or how I can remedy this.  I was told by a friend to install Lilo.  I am not aware of what Lilo is ?

---

### Post by 3rr0r on 2006-09-03
Alright, with the help of my friend I opened up a shell and did the following:

nano /etc/lilo.conf


then from here I added basically the mounting information to map that mount to Ubuntu.  had to know the path and name it.  Thanks for telling me to write it down, not sure how I would of done it otherwise.

Now I just need to add windows... only down-side is the Mandy loading screen dominates my loading for Ubuntu now as well.  It doesn't look like its booting up ubuntu until it pretty much prompts me for my user name and pass.  

NOW FOR XP... going to repeat the process and add xp to my lilo and see how it goes! woo hoo!  thanks for all the help guys.


But I did notice that I do not have access to Ubuntu memory test or ubuntu  recovery mode.  Any ideas what I'm doing wrong?  Do I have to set them in the lilo as well?

---

### Post by confused57 on 2006-09-03
> **3rr0r said:**
> Alright, with the help of my friend I opened up a shell and did the following:

nano /etc/lilo.conf


then from here I added basically the mounting information to map that mount to Ubuntu.  had to know the path and name it.  Thanks for telling me to write it down, not sure how I would of done it otherwise.

Now I just need to add windows... only down-side is the Mandy loading screen dominates my loading for Ubuntu now as well.  It doesn't look like its booting up ubuntu until it pretty much prompts me for my user name and pass.  

NOW FOR XP... going to repeat the process and add xp to my lilo and see how it goes! woo hoo!  thanks for all the help guys.


But I did notice that I do not have access to Ubuntu memory test or ubuntu  recovery mode.  Any ideas what I'm doing wrong?  Do I have to set them in the lilo as well?

Boot into Ubuntu, open a terminal(Applications---Accessories---Terminal), enter:
```
cat /boot/grub/menu.lst
```
You should have all the information you need to add entries to boot Windows, Ubuntu recovery, and memtest in Mandriva bootloader.
I'm not familiar with lilo, but maybe the above will work.

You can use the Dapper Live CD to install Ubuntu grub to the mbr:
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

If you do this, be sure to write down the entry to boot Mandriva from Dapper grub.

---

### Post by 3rr0r on 2006-09-03
Okay.  I'm posting from my laptop on Ubuntu.  I have configured lilo to give me the options to boot from Windows, Ubuntu, or Mandy.

I am not sure how to enable the Ubuntu Memtest and recovery mode from lilo.  I'm going to try to put them in, but if I can't is there a way where I can try using this GRUB since I know where the grub file is on my ubuntu partition?

I don't quite understand.  Are GRUB and lilo 2 programs that do the same thing?  When I selected Windows from the loadup screen, it asked me if I wanted to start XP or GRUB which really threw me off.  Needless to say, I selected Windows, and it booted up just fine.  I got online and everything.   Any/all help is very much appreciated.  Thank you.

---

### Post by 3rr0r on 2006-09-03
shameless bump for answers please

---

### Post by taurus on 2006-09-03
The entry for recovery mode should look like the one to boot into Ubuntu except with an extra word at the end, single...  And yes, LILO & GRUB are the same thing; they both allow you to boot from multiple OSes.

---


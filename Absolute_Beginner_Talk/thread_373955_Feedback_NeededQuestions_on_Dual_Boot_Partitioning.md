---
title: "Feedback Needed/Questions on Dual Boot Partitioning"
date: 2007-03-01
forum: Absolute Beginner Talk
---

### Post by skennedy1217 on 2007-03-01
I recently reformatted a 200 GB drive into two partitions and installed XP.  I want to now install Ubuntu and make it a dual-boot system.  I have been doing some research here and elsewhere ([http://www.psychocats.net/ubuntu/partitioning)](http://www.psychocats.net/ubuntu/partitioning)), but I have a couple questions I need help on before I take the plunge.

Here's how my drive is currently partitioned:

20gb (NTFS) - Windows
180gb (FAT32) - Files/Storage

Here's how I think I am going to format for dual booting:

20gb - Windows (NTFS)
?gb - Files/Storage (FAT32)
?gb - Ubuntu /home (Ext3)
20gb - Ubuntu / (Ext3)
2gb - swap

Whatever size **Ubuntu /home** becomes will determine how much (i.e, the remainder) goes to **Files/Storage**.  My understanding that the **Ubuntu /home** partition will allow me to save my system settings there, so that when the next release of Ubuntu comes out I can just do a fresh install on **Ubuntu /**.  Is this correct?  If so, then what size does **Ubuntu /home** need to be to save those settings?

My last question is somewhat off topic, but I was just wondering if it was possible to share email files between XP and Ubuntu?  That is, if I saved my current Outlook archive file (*.pst) to the Files/Storage partition, could Thunderbird access those emails?  Could my Inbox reside there, too?

---

### Post by firenurse4 on 2007-03-01
> My understanding that the Ubuntu /home partition will allow me to save my system settings there, so that when the next release of Ubuntu comes out I can just do a fresh install on Ubuntu /. Is this correct? If so, then what size does Ubuntu /home need to be to save those settings?

Yes you are correct.

As far as partition sizes go, that really depends on the types of files you will saving on your data patitions.  Also, will you be doing mor work in Ubuntu or Linux?

Without knowing what you file size needs are, I offer the following recomendations.

Windows 20 GB is fine.
Root on linux -- I belive you can get by with as liitles as 4GB, but 20 GB would be good.
Swap 2 GB is proably overkill. 1GB would fine there.

That leaves 159 GB free to divide between /home and a fat32 partition.  I would set that up to favor the OS you will be using primarily.

---

### Post by skennedy1217 on 2007-03-01
> will you be doing mor work in Ubuntu or Linux?

I didn't know there was a difference...do you mean Ubuntu or Windows XP?  If so, I'll be doing more work in XP at first, but with the hope of the pendulum shifting as I learn to feel comfortable in Linux.  How well I do with GIMP will have a lot to do with how often I have to access XP (for Photoshop).  However, my wife will probably be using the XP side exclusively.

> Swap 2 GB is proably overkill. 1GB would fine there.

The recommendation I saw was 1.5 to 2 times your RAM.  I have a gig of RAM, but if that's all the swap I need then that's good to know.

> That leaves 159 GB free to divide between /home and a fat32 partition.  I would set that up to favor the OS you will be using primarily.

I was planning on keeping all my music, office files and image files in the shared sector (FAT32) so that both OS's could read/write to them.  Is /home more like a Linux version of C:\Documents and Settings in Windows?  That is, if I save something while running an application in Ubuntu, will the program default the location to the /home partition...such that I'd have to specify the shared partition (FAT32) if I wanted to access it from XP later?

---

### Post by UltraMathMan on 2007-03-01
/home is basically where you keep your personal files and user setting, similar to C:\Documents and Settings. If you're only using the FAT32 partition for sharing you could always give that space to /home and install [Ext2ifs]("http://www.fs-driver.org/") in Windows, which will let you read/write the ext3 /home directory .

-Hope this helps :)

---

### Post by firenurse4 on 2007-03-01
[QUOTE=Me]Also, will you be doing mor work in Ubuntu or Linux?
[/QUOTE]:oops: 

My bad.  Yes I meant Windows BTW.

[QUOTE=skennedy1217]I was planning on keeping all my music, office files and image files in the shared sector (FAT32) so that both OS's could read/write to them. Is /home more like a Linux version of C:\Documents and Settings in Windows? That is, if I save something while running an application in Ubuntu, will the program default the location to the /home partition...such that I'd have to specify the shared partition (FAT32) if I wanted to access it from XP later?[/QUOTE]

Ok it looks like you need to favor the FAT 32 Partition. I would probably give the FAT patition 2/3 of the remaning space.  That would make about 100 GB FAT 32 and 59 GB /home.  You can use Gparted later on to adjust them if you need to.

As for the comparison between /home and C:\Documents and Settings goes, thats pretty much on mark.  You can change the default locations of saved files in any program such as open office.  Most of the configuration files will be in hidden folders in your /home/*you_username* folder. They typically don't use alot of space so if you music collection is large, feel free to add space to you FAT 32 space.

---

### Post by skennedy1217 on 2007-03-01
You've both helped immensely...thanks!

---

### Post by frotzed on 2007-03-02
I learned some interesting stuff from this thread!  When I installed ubuntu I just told it to erase the entire disk and do the whole installation process automatically.

---

### Post by skennedy1217 on 2007-03-02
I am trying to run the Ubuntu 6.10 installation disk and it's not seeing my hard drive as 200gb.  The Windows partition is there (although slightly smaller than XP sees it).  However, that plus the unallocated spaces only adds up to 186GB.  Is there a better way to partition than using the Ubuntu installer?

---

### Post by Amenemhet on 2007-03-02
It will not see it as 200 because it is not lying...without getting too technical, don't worry, you are not losing or have not lost any drive space, a 'real' G is 1024 M so , do the math. Windows calculates a G as 1000 M not the proper 1024 M. Whenever you buy a hard drive that says 100 G or whatever, it is never really that much, they round off to make life easier,and use 1000 but with the advent of such larger disks these days, the shortfall is quite a lot. My 100 GB drive in windows is 100, but when I use boot to linux it sees only about 93 GB.

---

### Post by skennedy1217 on 2007-03-03
Thanks...that makes sense.  I've gotten past the allocation of the partitions, but when I try to mount the partitions I get a "no root file system" error.

[Click here for a link to a screenshot.]("http://ubuntuforums.org/gallery/showphoto.php?photo=5092&cat=500")

This is what each partition is supposed to represent:

hda1 - NTFS - Windows boot
hda5 - FAT32 - Documents
hda6 - Ext3 - /home
hda7 - Ext3 - /
hda8 - swap

---

### Post by skennedy1217 on 2007-03-03
I hit the back button in the installer and noticed that there were warning flags on all of the partitions I set up under /dev/hda2.  It said that Gparted could not recognize them, read the file system, might be unformatted, etc.  I remembered when I set up the partitions originally (20gb for xp and 180 gb for documents) that windows could not read the second partition...said that it was unformatted.  I just figured that the Linux install CD would take care of that.

I hadn't gotten a response here yet on the above question, so I aborted the installation and tried to boot into windows.  However, I am now getting a DOS error that says it cannot boot from CD or Floppy.  I go into the BIOS and set HDD, but it still won't recognize or boot from the hard disk. :( 

Does it sound like I need to start all over?

---

### Post by skennedy1217 on 2007-03-03
*bump*

I don't know what I've done, but it's appeared to have corrupted the Windows partition.  I'll try to run some disk utilities.  If that doesn't work I think I may need to wipe the drive, install windows on the entire disk (one partition) and then try installing Ubuntu again.  Any other advise?

---

### Post by Amenemhet on 2007-03-03
Is hda5 an extended partition? It needs to be.

Edit: Sorry, not awake yet and didnt read the second page here. As I have missed that and you have probably proceeded, well, sorry I am too late. i will say though that I noticed you had missing partition numbers, and when you install a dual boot system with windows and linux, windows doesnt seem to take too kindly to your partition numbers being mucked about. If this advice is too late, by all means, and if you dont care or mind re-installing all, then I would do that. Safest in the long run and your partition numbers will be fixed. Remember to install Windows first though, so then you get the linux grub boot loader after, which is much better and easier to fix if need be later down the road. And recall me above post, only 4 primary partitions allowed per disk, so you will probably want one for the windows @ 20G, then you could split the drive , and use half for an ntfs or fat, as you prefer, then the rest for linux partitions. Linux has some issues writing to ntfs still, though I think there is an apt out there that now allows or has rectified this. If you are going to use both os's keep in mind that your linux os will see and be able to read your windows, but not the other way around. Personnally I would use ntfs for the windows primary, then fat32 for windows data, and ext3 for the linux data. This way your windows prime is safer but you could still write to the fat32 from linux happily. 

Good luck

---

### Post by skennedy1217 on 2007-03-03
@Amenemhet: Thanks for the quick reply.  I will probably start from scratch and install windows first (though I'll wait to install all the windows updates...eg., SP2...until *after* I get this part working).

I did upload a couple screen shots...

[#1]("http://ubuntuforums.org/gallery/data/500/Screenshot283.png")
[#2]("http://ubuntuforums.org/gallery/data/500/Screenshot312.png")

Let me know if you see anything else amiss.  Thanks!

---

### Post by Amenemhet on 2007-03-03
Don't give up, also are you using the livecd? I have read of some problems but I personally hade none with it. As for the screenshots, click next, they need to be formatted before you can install...

---

### Post by skennedy1217 on 2007-03-03
Yes, I'm using the LiveCD.  I clicked "Yes" on reformat, but when I hit "Next" to review and install that's when I got the "no root file system" error.  I do think I'm going to start from scratch, though.  Thanks for your help!

---

### Post by skennedy1217 on 2007-03-04
> And recall me above post, only 4 primary partitions allowed per disk, so you will probably want one for the windows @ 20G, then you could split the drive , and use half for an ntfs or fat, as you prefer, then the rest for linux partitions...Personnally I would use ntfs for the windows primary, then fat32 for windows data, and ext3 for the linux data. This way your windows prime is safer but you could still write to the fat32 from linux happily.

I have windows reinstalled and just want to make sure I understand correctly before I proceed.  In this screen shot you see that I've shrunk the Windows NTFS partition to 20GB.  The rest is unallocated space.

[IMG]http://ubuntuforums.org/gallery/data/500/part1.png[/IMG]

According to my plan I should just click on the unallocated space and create one primary partition (for the OS...i.e, "/") and one extended partition (with three partitions under it for /home, documents, and swap)?

20GB for "/" (make this "Ext3" and "Primary")
49GB for "/home" (filesystem=Ext3)
96GB for "/documents" (filesystem=FAT32)
1+GB for "linux-swap" (filesystem=linux-swap)

So it should look something like this?  Also, does the order matter?

[IMG]http://ubuntuforums.org/gallery/data/500/part2.png[/IMG]

I haven't done anything besides set up these pending operations.  Once I am sure that I have this correct, then I'll click on the "Forward" button in the Ubuntu installer.

[IMG]http://ubuntuforums.org/gallery/data/500/part3.png[/IMG]

---

### Post by skennedy1217 on 2007-03-04
Okay, after surfing the forum for the last hour I'm now confused.  I thought I read somewhere that "/" had to be a primary partition, but elsewhere it seemed like people only had XP as the primary and everything else as extended/logical.

To reiterate what I'm trying to do in the screen shots above, I want one partition for Windows OS, another for Ubuntu OS ("/"), a /home partition for the Ubuntu settings (so I can upgrade distros on "/" easier), a FAT32 partition to share files between XP and Ubuntu and finally the linux-swap partition.  I should add (or maybe I shouldn't) that I don't want to use all four primary partition options, because I might want to install Kubuntu later for the kids.

I really need to take this slow, even if these questions sound stupid, because I screwed up once already.  Thanks for putting up with newbies like me.

---

### Post by confused57 on 2007-03-05
> **skennedy1217 said:**
> Okay, after surfing the forum for the last hour I'm now confused.  I thought I read somewhere that "/" had to be a primary partition, but elsewhere it seemed like people only had XP as the primary and everything else as extended/logical.

To reiterate what I'm trying to do in the screen shots above, I want one partition for Windows OS, another for Ubuntu OS ("/"), a /home partition for the Ubuntu settings (so I can upgrade distros on "/" easier), a FAT32 partition to share files between XP and Ubuntu and finally the linux-swap partition.  I should add (or maybe I shouldn't) that I don't want to use all four primary partition options, because I might want to install Kubuntu later for the kids.

I really need to take this slow, even if these questions sound stupid, because I screwed up once already.  Thanks for putting up with newbies like me.
Taking it slow is a good idea, and I don't want to confuse you too much...it's pretty intimidating for a beginner.  Windows pretty much has to be installed on a primary partition, but that's not the case with Ubuntu...for now, you'd just need 2 primary partitions, one for Windows & an extended partition, which would "house" logical partitions for everything else.

Since you'll have a FAT32 partition to share "data", here's another possible partitioning scheme(this is just my suggestion, something to consider):
Windows------20 Gb
Extended partition:
Root---------- 15 Gb
Home---------20  Gb
FAT32---------130 Gb
Swap----------1.31 Gb

In my opinion, I don't believe you need your root & home partitions quite as large as you're planning on setting them up...partitioning is personal preference, and you'll get various suggestions of how to set them up...you'll have to decide in the end how you want to do so...don't be in a hurry to start partitioning, until you know for sure.

---

### Post by skennedy1217 on 2007-03-05
Thanks for the quick and thorough reply!

> for now, you'd just need 2 primary partitions, one for Windows & an extended partition, which would "house" logical partitions for everything else.

So if I'm understanding you correctly, an "extended" partition counts as a "primary," but you can set up multiple "logical" partitions under it?  That would make sense visually considering how Gparted has the partitions listed (i.e., with some left-justified and others indented).

I like your suggestions on the partition sizes.  One more question...when I mount the partitions do I "hide" linux-swap?  I seem to recall that option being in there somewhere the last time around.

---

### Post by confused57 on 2007-03-05
> **skennedy1217 said:**
> Thanks for the quick and thorough reply!



So if I'm understanding you correctly, an "extended" partition counts as a "primary," but you can set up multiple "logical" partitions under it?  That would make sense visually considering how Gparted has the partitions listed (i.e., with some left-justified and others indented).

I like your suggestions on the partition sizes.  One more question...when I mount the partitions do I "hide" linux-swap?  I seem to recall that option being in there somewhere the last time around.
Yes to your first question...initially when I set up Dapper on a 160 Gb hd, I just did a default install with root & swap...since then I've resized multiple times and now I have 11 partitions(including swap) on the hard drive...6 different Linux distros.
The gparted live cd is an excellent partitioning tool for later repartitioning:
[http://gparted.sourceforge.net/screenshots.php](http://gparted.sourceforge.net/screenshots.php)
I just boot up the gparted live cd(30 mb download), resize a partition to create unallocated space & install another distro.

I don't know anything about hiding swap...you don't mount anything when you're partitioning, formatting is done on unmounted partitions...the Ubuntu installer will add mount points to your /etc/fstab...and you can manually add mountpoints for additional partitions to /etc/fstab after installing if you create more partitions.
This site has some excellent information you might want to read over(reread your first post, you already know about this site):
[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

another great resource:
[http://users.bigpond.net.au/hermanzone/index.htm](http://users.bigpond.net.au/hermanzone/index.htm)
this is much more than a dualboot site, great info on mbr, grub, xserver, gag, mounting,etc...check out the index, you might want to burn a copy of the Super Grub Disk(500 kb download) before you begin your Ubuntu installation(it might come in handy, if you have problems).

As somebody else mentioned, may people opt to have a large ext3 partition for data sharing rather that FAT32...by installing the fs-driver(a link was provided earlier) in Windows to read & write to ext3...ext3 is probably a better option, from what I've read...then again, many people use FAT32 to share data...at least you have a choice.

---

### Post by skennedy1217 on 2007-03-05
Thanks again.  I've been to the psychocats site and found it helpful, but not all my questions were answered.  There's a learning curve in which some of what I read still sounds Greek to me, or there's an assumption on the writer's behalf of the reader's prior knowledge that I don't have yet (that, and there's a ton of acronyms :) ).  So I will definitely check out the hermanzone.  The funny thing is that I'm finding all of this fun, because I'm actually learning stuff.  If I were having the same trouble with Windows I'd be gnashing my teeth!

Here's the latest config...couldn't have gotten here w/o the great community effort here on the forum!

[IMG]http://ubuntuforums.org/gallery/data/500/part4.png[/IMG]

---

### Post by Amenemhet on 2007-03-05
Looks good dude...remember one of those ext3's must be for / (root). Also your swap should be roughly twice the size of your ram, so i assume you have 512? I have 1G of ram so I have 2G for swap. As for the fat32, well, me thinks the latest distro can now write to ntfs, or there is an apt (update) that will allow it. Been awhile in the making. (Pesky Windoze pemissions, over 100 of the bloody things, and they contradict each other left and right) Also, at a later date you can change the file system with tune2fs....but thats for later, when you are more comfy with your new OS ;)

---

### Post by skennedy1217 on 2007-03-05
I have 1024MB of RAM, but I was told be a few folks that 1 gig of swap was plenty (and that in some cases too much swap can slow things down)?

---

### Post by confused57 on 2007-03-05
> **skennedy1217 said:**
> I have 1024MB of RAM, but I was told be a few folks that 1 gig of swap was plenty (and that in some cases too much swap can slow things down)?
I have a gig of ram & never use swap...I think you're OK with how you're going to set up your partitions.

---

### Post by skennedy1217 on 2007-03-05
Well, things haven't gone perfectly...

----------

The first issue was when I was installing I got an error about the Fat32 partition (no file system specified for partition #...if you do not go back to the partitioning menu and assign a  file system to this partition, it won't be used at all).  The options were to GO BACK and CONTINUE.  So I clicked BACK (thinking I missed something) and it didn't do anything.  I reran the installer and deleted the fat32 partition and created a new one.  The second time through I got the same error message.  This time I clicked on CONTINUE and the installer shut down...again.  A third time through I clicked on CONTINUE and this time it installed everything.

----------

The second issue is that after the installation reboot I was given the following choices:

Ubuntu, kernal 2.6.17-10-generic
Ubuntu, kernal 2.6.17-10-generic (recovery mode)
Ubuntu, memtest86+
Other operating systems:
Microsoft Windows XP Home Edition

If I select any of the three Ubuntu choices I get the following error...

[B]Error 17: Cannot mount selected partition

Press any key to continue...[/B]

----------

I guess the good news for now is that it will still boot into Windows.  Any advice on what to do next?

---

### Post by skennedy1217 on 2007-03-05
Little bit of trial and error...on the OS selection screen I hit "E" and then on ROOT hit E again...changed the command line from (hd0,0) to (hd0,4) and then hit "B" for boot.  It booted into Ubuntu but then there was another command line error...

[B]BusyBox v1.1.3 (Debian 1:1.1.3-2ubuntu3) Built in shell (ash)
Enter 'help' for a list of built-in commands.

/bin/sh:can't access tty; job control turned off
(initramfs)[/B]

I am still kind of clueless and am thinking I bit off more than I can chew.  I'll have to pick this up again tomorrow (gotta get a least a few hours of sleep).

----------

BTW, when I boot into Windows I have my C: drive, D: (DVD-RW), E: (CD-RW) and F: (assuming it's the FAT32 drive...but it's listed as file system RAW and unformatted).

Also wondering if there's just something screwed up about my partition numbers and maybe that's why I can't get into Ubuntu?

---

### Post by skennedy1217 on 2007-03-05
Found this thread...

[http://ubuntuforums.org/showthread.php?t=351884]("http://ubuntuforums.org/showthread.php?t=351884")

...and changed a couple of the command lines

**(hd0,0)** to **(hd0,4)** on 'root'
**kernel /vmlinuz root=/dev/hda0...** to **kernel /vmlinuz root=/dev/hda5...**

I have no idea what I did, except I think it had to do with pointing to the right files in terms of where they ended up on the partitions?  Also, not sure if whatever I did was permanent or just a temporary work around...too tired to figure that out right now.

Also need to do something about the FAT32 partition.  XP won't read it and it doesn't seem to show up in the Ubuntu /* File Browser (I had named it "documents").

----------

Update: After installing a bunch of system updates and rebooting (for the heck of it) I discovered that the above edits did not stick.  I have a lot left to learn.  Now to get a couple hours of sleep (and I mean it this time)!

---

### Post by confused57 on 2007-03-05
> **skennedy1217 said:**
> Found this thread...

[http://ubuntuforums.org/showthread.php?t=351884]("http://ubuntuforums.org/showthread.php?t=351884")

...and changed a couple of the command lines

**(hd0,0)** to **(hd0,4)** on 'root'
**kernel /vmlinuz root=/dev/sda0...** to **kernel /vmlinuz root=/dev/sda5...**

I have no idea what I did, except I think it had to do with pointing to the right files in terms of where they ended up on the partitions?  Also, not sure if whatever I did was permanent or just a temporary work around...too tired to figure that out right now.

Also need to do something about the FAT32 partition.  XP won't read it and it doesn't seem to show up in the Ubuntu /* File Browser (I had named it "documents").
You can make the changes permanent in your /boot/grub/menu.lst by opening a terminal(Applications---Accessories---Terminal), enter:
```
cd /boot/grub
sudo cp menu.lst menu.lst_backup
gksudo gedit menu.lst
```
enter(copy & paste) each line one at a time, press enter between each
make your changes, click on file, quit, save.

The next thing you might want to do is burn a copy of the gparted live cd:
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

You can select to reformat the fat32 partition as ext3, and leave it as a logical partition...you can create a mountpoint for it and have it automatically mount by adding an entry to your /etc/fstab.
I apologize for steering you wrong, but the FAT32 probably has to be a primary partition...you could probably delete the partition, using the gparted live cd...then click on the partition & choose to make a new primary partition formatted as FAT32.  Make a note of your partition numbers as shown in gparted, then changes can be made to mount the partition in /etc/fstab.   I think all logical partitions within an extended partitiion have to be the same filesystem & this was causing the problems during installation.
Thank goodness you're still able to boot into Windows, although the mbr could have been restored:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

Again, sorry for the misinformation I gave you...getting late here, so need some sleep myself...if you still want my assistance, I'll try to help as much as I can later on.

Here's an excellent post by Herman in another thread concerning dual booting:
[http://www.ubuntuforums.org/showpost.php?p=2250418&postcount=10](http://www.ubuntuforums.org/showpost.php?p=2250418&postcount=10)

Another problem with a large FAT32 partition, see reply #2 in this thread:
[http://www.ubuntuforums.org/showthread.php?t=376340](http://www.ubuntuforums.org/showthread.php?t=376340)
I don't know if this may have caused the problems with the installer or not.

---

### Post by Herman on 2007-03-05
Hello skennedy1217,
It's odd how some machines have no problems at all installing Ubuntu but others have nothing but problems. My wife and I have identical computers, but hers gave me a lot of problems last time I installed 'Edgy Eft' in it. I had to repeat the attempt several times before I was happy with it. 
I have never had any problem installing in my computer, and it's identical, and I used the same CD. My idea is maybe she has a little speck of dust in her CD drive or some other small problem somewhere that makes reading the CD seem okay for music and data, but for tricky things like partitioning disks and installing, not quite good enough.

One idea is to verify your CD is burned correctly by clicking 'check cd for defects' before booting the CD.

Another idea is to try doing the partitioning part of the installation with the [GParted LiveCD]("http://gparted.sourceforge.net/") first. The Ubuntu installers's GParted is fine, but this is just for a way to separate the issues so it is more clear where you are having trouble, with the partitioning, or with the installing. 

I hope that helps, Regards, Herman :)

---

### Post by skennedy1217 on 2007-03-05
This afternoon I used the standalone GParted to wipe and repartition the non-Windows partitions of the drive.  One interesting thing I noticed after running the Ubuntu LiveCD is that the partition numbers changed between Gparted Live and Ubuntu LiveCD Installer.

Here's what I got after formatting in GParted LiveCD:

/dev/hda1/ - ntfs - 20GiB
/dev/hda2/ - fat32 - 130GiB
/dev/hda3/ - extended - 36.31GiB
...../dev/hda4/ - ext3 - 15GiB
...../dev/hda5/ - ext3 - 20GiB
...../dev/hda6/ - linux-swap - 1.31GiB

I rebooted in and ran the Ubuntu LiveCD installer and got this:

/dev/hda1/ - ntfs - 20GiB
/dev/hda2/ - fat32 - 130GiB
/dev/hda3/ - extended - 36.31GiB
...../dev/hda5/ - ext3 - 15GiB
...../dev/hda6/ - ext3 - 20GiB
...../dev/hda7/ - linux-swap - 1.31GiB

Is that renumbering an issue at all?

I ran the error check on the CD, too (Check finished, 0 checksums failed...)

I also seem to keep getting errors with formatting or mounting this FAT32 partition.  Is 130GiB really too big and should I just set it up as EXT3 (and if so, as a primary partition)?  I hear there's a program for Windows that will allow XP to read/write to EXT3.

Thanks, Scott

--------------------

UPDATE: So I ran Gparted again to repartition...and this time the numbering went hda1, hda2, ...3, ...5, ...6, etc.  Go figure.  I *am* beginning to wonder if my PC is cursed! :)

---

### Post by confused57 on 2007-03-05
Here's the fs-driver for Windows that allows read-write to ext3:
[http://www.fs-driver.org/](http://www.fs-driver.org/)
I've read that ext3 is a much better filesystem than FAT32, which supposedly has a 32 Gb partition and 4 GB single file size limitation...I personally haven't used the fs-driver, but I've seen nothing but good things posted about it.  If you decide to go with an ext3 "documents" partition, I don't think it would matter if it were primary or logical, might want to make it primary.  For the mountpoint, you might want to type in /media/documents in the space provided during install.

As far as your partition numbering, the Ubuntu live cd is correct:
> /dev/hda1/ - ntfs - 20GiB
/dev/hda2/ - fat32 - 130GiB
/dev/hda3/ - extended - 36.31GiB
...../dev/hda5/ - ext3 - 15GiB
...../dev/hda6/ - ext3 - 20GiB
...../dev/hda7/ - linux-swap - 1.31GiB

I say this because primary partitions are numbered 1-4, logical partitions start with partition #5.

If you decide you want to try another Linux distro later on, you could resize the "documents" partition to free up some space, create a new logical partition, install the other distro...you can use the same swap partition for multiple distros.

Just saw your update...the gparted live cd correctly identified your partitions the 2nd time...good luck, let me know how it goes.

Thanks Herman for your input...

---

### Post by skennedy1217 on 2007-03-05
Thank you...I may not have Ubuntu installed yet but at least I'm learning something along the way.  Right now it's installing again...

Two questions (the answer to which may sound obvious)...

1. Was I supposed to click the "reformat" button on the FAT32 partition?  I didn't see anything on this in what I've read so far, but this time around I left it unchecked and didn't get any errors.

2. Before I mounted the partitions was I supposed to set the flag as "boot" on the "/" partition?  I didn't do that before but did this time.

---

### Post by confused57 on 2007-03-05
> **skennedy1217 said:**
> Thank you...I may not have Ubuntu installed yet but at least I'm learning something along the way.  Right now it's installing again...

Two questions (the answer to which may sound obvious)...

1. Was I supposed to click the "reformat" button on the FAT32 partition?  I didn't see anything on this in what I've read so far, but this time around I left it unchecked and didn't get any errors.

2. Before I mounted the partitions was I supposed to set the flag as "boot" on the "/" partition?  I didn't do that before but did this time.

If you formatted the FAT32 partition with the Gparted live cd, then no you wouldn't have needed to select reformat...with a data partition, there shouldn't be any problems going back later and reformatting to a different filesystem or as FAT32.

Yes, it's best to select the root partition as bootable...I always do & haven't had any problems.

---

### Post by skennedy1217 on 2007-03-05
I just successfully booted Ubuntu, then rebooted and ran Windows!  Not only that, but the FAT32 drive is 'openable' and formatted at it's full capacity in Windows as F:\ and as the "share" folder in Ubuntu (I had named it "documents" earlier).  My only regret is not taking screen shots of the time it worked.

I have to say that I'm both thrilled and relieved!  Thank you all for your help.  I would have given up without your support.  I'm sure this won't be my last need for the forums, but consider this thread effectively closed (for me at least). ):P

PS - I was just checking my work email from Ubuntu and downloaded my first Word document into OpenOffice...that alone got me giddy.  I feel like such a geek for saying that.  Now onto customizing Ubuntu and figuring out how to use and abuse it. :mrgreen:

---

### Post by confused57 on 2007-03-05
Great, glad everything worked this time...it is quite a bit of fun and you learn a lot along the way...I must confess, I didn't know what a partition was before I tried Ubuntu(I know, fine time to be telling you  this)...

I was almost afraid to read your reply, anticipating things didn't work.  Guess your FAT32 results kind of dispels the "rumors" of partition size limitations.
Happy Ubuntuing...

---

### Post by skennedy1217 on 2007-03-05
> I was almost afraid to read your reply, anticipating things didn't work.

I was suprised, too, having gone way past the 'three times is a charm' rule.  I guess it was a combination of things that I finally got right, though whether or not the cleaning duster I sprayed into the CD-ROM drive for extra precaution was part of it, I'll never know!

---


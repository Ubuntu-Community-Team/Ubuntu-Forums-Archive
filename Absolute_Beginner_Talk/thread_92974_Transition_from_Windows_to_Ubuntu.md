---
title: "Transition from Windows to Ubuntu"
date: 2005-11-20
forum: Absolute Beginner Talk
---

### Post by chroniker on 2005-11-20
Just received my Breezy disks and I have repartitioned my HD so I can dual-boot XP. Is there anything in particular that I need to watch out for or do I just jump in and start swimming?

---

### Post by aysiu on 2005-11-20
Read this:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by matthew on 2005-11-20
[quote=chroniker]Just received my Breezy disks and I have repartitioned my HD so I can dual-boot XP. Is there anything in particular that I need to watch out for or do I just jump in and start swimming?[/quote]
If the repartitioning worked and XP is booting fine (which it sounds like it is) you can jump in and start swimming.

Post in these forums if you run into problems. You might want to take a look at this if you haven't already:

[https://wiki.ubuntu.com/WindowsDualBootHowTo](https://wiki.ubuntu.com/WindowsDualBootHowTo)

---

### Post by chajuram on 2005-11-20
Hi,

It is quite simple actually. If I could do it, you can too. Just go ahead. 

Ubuntu takes care of most of your worries. 

Chajuram.

---

### Post by ecobuntu on 2005-11-20
Also check out [www.ubuntuguide.org](www.ubuntuguide.org) for installing certain packages.  It's slightly outdated, it's for Hoary, but still applicable.

---

### Post by bluevoodoo1 on 2005-11-20
[QUOTE=aysiu]Read this:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)[/QUOTE]

I recently configured a dual boot system Ubuntu and XP (it was actually yesterday) and that site offered some great tips. Good luck.

---

### Post by chroniker on 2005-11-24
I am using the example given [here]("http://users.bigpond.net.au/hermanzone/p2.htm") to dual boot with XP. As mentioned earlier in this thread, I have already repartitioned my HD and reformatted the partition that I want unbutu loaded on to FAT32 (why? I don't know, I just did).

I have just started the installation and have goten to the point of "Partition disks" and would like to know how to tell ubuntu to install on the fat32 partition.

---

### Post by linbetwin on 2005-11-24
You cannot install on FAT32. Linux uses other file systems.
Choose the option that says **Manually ... partition table** (or sth like that) delete the FAT32 partition and then choose **Automatically partition...**

---

### Post by aysiu on 2005-11-24
[QUOTE=chroniker]
I have just started the installation and have goten to the point of "Partition disks" and would like to know how to tell ubuntu to install on the fat32 partition.[/QUOTE] Select "Manually Edit the Partition Table." Then, you'll be presented with all the partitions on your drive. It'll also tell you what types they currently are (FAT32, Ext3, NTFS, etc.). Pick the one that's FAT32 and press Enter. Then it'll say it's type FAT32 and mount point /media/hd__ (fill in the blank--/media/hda3, for example). It'll also say "Do not format." If you press Enter on an option, it'll assume you want to change that option.

So, press Enter on FAT32, you can change it to be Ext3.
Press Enter on Do not Format, and it'll change to Format.
Press Enter on mount point /media/hd__ and you can change the mount point to /

---

### Post by chroniker on 2005-11-24
On the screen where all of my partitions are listed I choose the FAT32 and the options on the next screen are:

Use as FAT32 file system
Mount point /media/hda_
Mount options default
Bootable flag off
Size
Done setting up the partition
Copy data from another partition
Delete the partition

Upon choosing "Use as..." the next screen gives me various options has to how to use this partition and "do not format" is not one of them. The options are:

Ext3 journaling file system
Ext2 file system
ResiserFS journaling file system
JTFS journaling file system
XFS journaling file system
FAT32 file system
FAT16 file system
FAT32 file system
swap area
physical volume for LVM
physical volume for RAID
do not use the partition

---

### Post by aysiu on 2005-11-24
[QUOTE=chroniker]
Ext3 journaling file system[/QUOTE] This is the one you want.
Make sure the mount point is /

---

### Post by chroniker on 2005-11-24
Am I a newb or what?

Anyway, after selecting Ext3 I get:

No root file system
No root file system is defined.
Please correct this from the partitioning menu.
Go Back
Continue

Obviously choosing "Go back" or "Continue" takes me back to the list of partitions.

Where do I go to create/define/select root file system?

---

### Post by aysiu on 2005-11-24
[QUOTE=chroniker]
Where do I go to create/define/select root file system?[/QUOTE] You can't just format it as Ext3. You also have to change the mount point from whatever it was to /

That's right. That's a slash with nothing after it: /

---

### Post by linbetwin on 2005-11-24
If you are a newbie (like yours truly) it's easier to delete the FAT32 partition and let Ubuntu partition the free space automatically.

---

### Post by linbetwin on 2005-11-24
Don't forget you have to create a swap partition too, unless you have gigs upon gigs of RAM.

---

### Post by aysiu on 2005-11-24
[QUOTE=linbetwin]If you are a newbie (like yours truly) it's easier to delete the FAT32 partition and let Ubuntu partition the free space automatically.[/QUOTE] You're probably right, but at this point, it's a bit late for that.

---

### Post by chroniker on 2005-11-24
[QUOTE=aysiu]You can't just format it as Ext3. You also have to change the mount point from whatever it was to /

That's right. That's a slash with nothing after it: /[/QUOTE]


:oops: Didn't you tell me this already?

What about "Mount options"? After setting mount point to / and then selecting "Finish partitioning...." my screen goes blank for an instenant and returns to the list of partitions and does not give any warnings or ask any questions.

---

### Post by chroniker on 2005-11-24
[QUOTE=linbetwin]If you are a newbie (like yours truly) it's easier to delete the FAT32 partition and let Ubuntu partition the free space automatically.[/QUOTE]

I'm hard headed. Besides, as you said, that is the easy way and I have over 800M for swap.

---

### Post by linbetwin on 2005-11-24
What partitions do you have now?

---

### Post by aysiu on 2005-11-24
[QUOTE=chroniker]:oops: Didn't you tell me this already?

What about "Mount options"? After setting mount point to / and then selecting "Finish partitioning...." my screen goes blank for an instenant and returns to the list of partitions and does not give any warnings or ask any questions.[/QUOTE] Hm. That's weird. What are the other partition types and their mount points?

---

### Post by chroniker on 2005-11-24
IDE1 Master (hda) 20.5 GB
#1 primary 9.1 GB NTFS /media/hda1
#5 logical 10.5 GB ext3 /
#6 logical 871.8 MB swap swap

IDE1 slave (hdb) 80.0 GB
#1 primary 38.1 GB NTFS /media/hdb1
#5 logical 41.9 GB FAT32 /media/hdb5
    pri/log 49.4 MB Free Space

---

### Post by linbetwin on 2005-11-24
"Finish partitioning and write changes to disk"

---

### Post by chroniker on 2005-11-24
[QUOTE=linbetwin]"Finish partitioning and write changes to disk"[/QUOTE]

See post #17

---

### Post by linbetwin on 2005-11-24
select / partition (ext3), ENTER, delete this partition.
Select swap, ENTER, delete partition.
select FREE SPACE, ENTER, automatically parition bla bla
Finish partitioning and write bla bla

---

### Post by aysiu on 2005-11-24
[QUOTE=chroniker]IDE1 Master (hda) 20.5 GB
#1 primary 9.1 GB NTFS /media/hda1
#5 logical 10.5 GB ext3 /
#6 logical 871.8 MB swap swap

IDE1 slave (hdb) 80.0 GB
#1 primary 38.1 GB NTFS /media/hdb1
#5 logical 41.9 GB FAT32 /media/hdb5
    pri/log 49.4 MB Free Space[/QUOTE] That setup *should* work. You've got a **/**, and you've got a **swap.** That's all the installer should need.

---

### Post by linbetwin on 2005-11-24
Maybe / is not flagged as bootable.

---

### Post by chroniker on 2005-11-24
[QUOTE=linbetwin]Maybe / is not flagged as bootable.[/QUOTE]

Good call. Bootable flag was off.

---

### Post by chroniker on 2005-11-24
Packages are now installing.

Thanks.

---

### Post by chroniker on 2005-11-24
Well, actually it wasn't solved. After 1st reboot the screen that comes up is
"Installing packages" and since today is Thanksgiving I go and do the turkey thing and I leave it to install.

When I get back I see that the status bar has been stuck on 0% for 6 hours.

I think I should start over.

---

### Post by aysiu on 2005-11-24
[QUOTE=chroniker]Well, actually it wasn't solved. After 1st reboot the screen that comes up is
"Installing packages" and since today is Thanksgiving I go and do the turkey thing and I leave it to install.[/quote] Sorry. I took "Packages are now installing" to mean it was solved. I've changed the title back.

> 
When I get back I see that the status bar has been stuck on 0% for 6 hours.

I think I should start over. You may have a bum disk. When the installer gets stuck, it means one or more of the following:

1. The disk image was corrupted during download
2. The disk image was corrupted during the burn
3. The hardware is faulty

If it wasn't #3 for sure, you should [check into #1](http://www.linuxiso.org/viewdoc.php/verifyiso.html) or #2 (burn at a slow speed--2x or 4x).

---

### Post by chroniker on 2005-11-25
I thought that it was solved too. As it turns out it was a bad disk. Since I requested 5 disks, I trashed that one, dropped another one in and went to town. I was downloading updates less than 45 minutes later. 

Toto, we're not in Kansas any more.

---

### Post by chroniker on 2005-11-25
By the way. I was not asked to provide a root p/w. I was only asked to provide a user name and p/w.

However on the failed install I was asked for a root p/w.

---

### Post by carlosqueso on 2005-11-25
Ubuntu doesn't do root passwords by default, you just use sudo and your user password to do things as root....I'm not sure why it asked you for a root password on the failed install though

---

### Post by aysiu on 2005-11-25
[QUOTE=chroniker]By the way. I was not asked to provide a root p/w. I was only asked to provide a user name and p/w.[/quote] Read this:
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

> 
However on the failed install I was asked for a root p/w. You probably chose an expert install. The regular install won't ask you for a root password.

---

### Post by junamuno on 2005-11-25
Hi!, I just got my ubuntu discs and i want to install it to my pc but without losing windows (adleast for now). Basically I'm stuck in the partitions part and that's because i'm afraid to erase something I might need later.
aparently I have 32.7 GB free space to install it, but when i hit enter to start that partition it says that's not possible to do.
so i'd like to know how to make a partition without having to lose anything else that I have in my Pc.

 :p Thanx for your help

---

### Post by aysiu on 2005-11-25
You run the risk of losing stuff any time you futz with your hard drive.

Back up your work. Burn 100 CDs. Load up 300 floppy disks. Upload to 20 websites. Do what you have to do, but back up your work. If you don't, it's like riding a motorcycle and not wearing a helmet.

That said, this guide should help:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by chroniker on 2006-06-14
After a long and inexcusable absence I have returned to the world of linux. One of the excuses that I used was that I didn't have a readily available source to go to to talk linux with, other than this forum and others. There is nothing quiet like sitting down and talking with someone that knows what you are talking about.:-({|=  But after [reading]("http://australianit.news.com.au/articles/0,7204,19345228%5E15865%5E%5Enbv%5E,00.html") where Microsoft is using it's known vulnerabilities to make money off of it's users I said to myself, "self you have got learn linux".

For those that don't know, [here]("http://www.windowsonecare.com/") is the link to the Microsoft OneCare site.

Back when I installed Breezy I did a search for linux tutorial sites and found several and they all had one thing in common. It had been at least a year since any of them had been updated. After doing another search this week I find that this has not changed.

My question is, is the information found on these sites (I know it would help if I gave site names but...) valid today? Or, what recomendations do ya'll have for an absolute beginner to go to to learn how to install, configure and administer linux on the desktop, how to use bash and shell and what in the world does "sudo mkdir /media/windows" mean? (Thanks to [http://help.ubuntu.com](http://help.ubuntu.com) I know the answer to this last question, I'm just using it as an example)

---

### Post by bruce89 on 2006-06-14
[QUOTE=chroniker]... absolute beginner to go to to learn how to install, configure and administer linux on the desktop, how to use bash and shell and what in the world does "sudo mkdir /media/windows" mean? (Thanks to [http://help.ubuntu.com](http://help.ubuntu.com) I know the answer to this last question, I'm just using it as an example)[/QUOTE]
Well they will know after a while.
Anyway welcome back, we are now mostly using Dapper Drake.

---

### Post by chroniker on 2006-06-15
I just requested 5 disc's.

---


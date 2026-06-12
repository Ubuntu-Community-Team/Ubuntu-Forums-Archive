---
title: "just got Ubuntu 7.10,need to know how to install it without losing Windows XP"
date: 2007-11-28
forum: Absolute Beginner Talk
---

### Post by Amit G on 2007-11-28
I  want to know whether I can install Ubuntu 7.10 without losing Windows XP...I ran wubi through the Ubuntu Installation CD though and saw what was there but couldn't take the risk of pressing the install button there,just in case I might lose data,fact is I got two earlier versions of Ubuntu as well but had to donate it to the computer institute  because of the fear that I might lose all the data at home and o'er there they like experimenting with their machines and were too  happy to accept it but I don't want to part with Ubuntu 7.10 and want to give it a try but then there's the risk factor,this just isn't my computer alone,my mom and dad also use it and will definitely kill me for certain if by accident their data is gone too...I have an intel dual core processor,512 MB RAM and Windows XP SP2. I have a 40 GB Hard Disk partitioned into two with one 20 GB partition having the core Windows OS plus most program files etc. etc.with 7.74 GB used and 10.8 GB free and then the other drive 20 GB with 17.9 GB free and 807 MB used with some files and data plus some program files which I installed there. Now I want to know how can I use both without losing Windows XP plus all the data inside,can Ubuntu be installed on the second drive cause' most of the space there is free but the hitch is there are some program files plus data there on that partition too.I also want to know if this is possible and I go about it and have both OS's on my computer,how can I import all files,bookmarks etc. etc. from my Windows OS into Ubuntu and will 2 OS's put more pressure on the system? Please do help me out,I want to use Ubuntu as I have used a lot of Open Source softwares but this one last inch I'm finding difficult to take and want to use both Windows XP and Ubuntu 7.10 and can't go without any of these 2,and want to use both on the sort of hardware I have that I mentioned without putting pressure on the system...it's the love of open source softwares and I want to try Ubuntu as well and my mom and dad don't know what Open Source is at all and want to stick to Windows so this is the compromise,I want to use Ubuntu for most of my work and at times Windows while they use Windows entirely and if need be give Ubuntu a try,please do help me out on this,I get totally confused with computer jargon and don't know what NTFS,Disk Resize and all that is,I want plain and simple procedure to carry it out.

Help!!!!!:(

---

### Post by Paqman on 2007-11-28
Firstly,don't do anything until you're sure all your data is backed up. Back up everything on your data partition, as well as the Documents & Settings data for the users and make sure you have discs and licence keys for any non-free software.

Also, since it's not you're computer, do you have the owner's permission to install Ubuntu?

If you do go ahead, you'll want to partition your data drive. You'll then install Ubuntu onto the new partition(s)

Have a read through of some guides:
[How to install Ubuntu on a Windows PC](http://www.sp0rk.co.uk/Archive/Issue10/stayingin_install_ubuntu1.php)
[Psychocats](http://www.psychocats.net/ubuntu/)

---

### Post by Grey Box on 2007-11-28
Instead of doing everything through the installer use the partition editor that comes with the LiveCD. 

It should be under System -> Administration -> Partition Editor.

You have to choose the correct hard drive (if you have more than one), and they are usually designated /dev/hda1 or /dev/sda1 and /dev/sda2 and so on. 

(Before you do this, you still have to back up important data on your windows installation. Just take the time and do it, or you'll be sorry one day)

Now, the partition editor (gparted) is very powerful and can do some amazing things but you have to think before you leap with these things.

If your previous windows installation used up the entire hard drive, you'll have to resize the partition. That's easy to do and gparted can resize NTFS partitions (of course you have to make up free space on the windows partition).

You need at least two partitions for linux, usually. A big one for everything, and a 1 or 2 gigabyte partition for swap (when your RAM gets overfilled). 

edit: And yes, definitely follow Paqman's advice - go and read some tutorials and howto's. It rapidly becomes clear what you are doing and, by understanding what you're doing, you can learn with confidence.

Format the big one as EXT3, for example. And the othe as Linux Swap. 

Remember the names of the partitions (eg: /dev/sda2) 

When you go to install Ubuntu, choose to manually set up your partitions. You then don't have to do anything major except make sure the main partition is made to be the root partition ( just '/' ) and the other as swap.

I hope that helps.

---

### Post by anilbhx on 2007-11-28
And be careful . Ubuntu offers to install on the XP partition by default. :) Mine did many times....Maybe in a few months this will be what you want :)

---

### Post by hyper_ch on 2007-11-28
And before you tinker with your partitions: **MAKE A BACKUP!**

---


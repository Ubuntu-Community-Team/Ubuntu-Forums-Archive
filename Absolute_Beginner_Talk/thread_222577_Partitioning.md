---
title: "Partitioning"
date: 2006-07-25
forum: Absolute Beginner Talk
---

### Post by pennyminstrel on 2006-07-25
I've just (yesterday) installed ubuntu in a dual boot with windows and feeling quite pleased with myself that I've managed various things like adding repositeries and adding programs. 

I've even managed to mount the windows partition so I can see the stuff on there. Now I'd like to repartition so I can create a FAT32 partition for shared data and create a /home partition.(I'm acautious soul so I thought I'd do the partitioning in stages rather than all at once when I installed.)

 To start with I went into gparted and tried to resize the partitions, but although I can highlight the one I want to resize, the Resize/Move option is always greyed out. 

Then I found aysiu's instructions [URL="http://psychocats.net/ubuntu/separatehome.html"]here but every time I try to boot into a live session from the CD it still goes into the existing installaation.

I'm clearly missing something in both cases, but what?

---

### Post by Indras on 2006-07-25
> **pennyminstrel said:**
> but every time I try to boot into a live session from the CD it still goes into the existing installaation.

The live CD shouldn't boot into your existing installation, ever.  When it starts up, you should see a selector with options "Start or install" "memory test" and "boot from hard disk" with a timeout on the left.

If you aren't seeing that, then your computer isn't booting from the CD at all, which is either a BIOS setup problem, or a damaged CD.  First, try going into your BIOS and make sure that it tries to boot from CD-ROM drives before hard drives (exactly how is different for different motherboard manufacturers).  If that is already set properly, try turning off the option to boot from hard drives entirely (if available), then you'll know for sure if you have a bad CD, since it will fail to boot from any drive and most likely give some sort of warning like "non system disk or disk failure, please insert a system disk and restart."

---

### Post by Ares Drake on 2006-07-25
> **pennyminstrel said:**
> but every time I try to boot into a live session from the CD it still goes into the existing installaation.

I'm clearly missing something in both cases, but what?

You have to change your BIOS settings to first try booting from CD and only second from the harddisk. It usualy says something like "1st boot device, 2nd boot device, etc". Then you should be able to boot into the live-CD

---

### Post by pennyminstrel on 2006-07-25
hey guys

thanks for your replies

I've made some progress. Managed to boot from the cd, don't know why, I already had it set to boot from cd anyway, but it just started working.

In gparted I got as far as creating the FAT32 (by the way, do I have to mount this now to use it?) so I've now got 4 partitions, an ntfs for windows, the FAT32, an ext 3 for ubuntu and the extended partition which was there already for the SWAP file. I've attached a screenshot.

I created some space to create the /home partition in but when I tried to format this as ext 3 it told me I couldn't have than 4 partitions and i would have to create an extended partition with logical drives. I do remember reading something like this before so I wasn't surprised, but I can't find anythng that tells me how to do this.

thanks ever so for your help. its doing my head in but i'm determined to get there.

---

### Post by OU812 on 2006-07-25
First we need to find its name. In a terminal do

sudo /sbin/fdisk -l

Look for an entry with W95 FAT32 in the last column. As an example, let's say the device name is /dev/hda5. Now we need to update fstab. From a terminal do

sudo gedit /etc/fstab

add the line

/dev/hda5 /mnt/winfat vfat rw,users,umask=000 0 0

I usually put this with the other hard drive entries (hda or hdb). Note: winfat is the name of the directory you will use to browse the contents or your partition. Call it whatever you want. Now we need to create the directory. In a terminal do

sudo mkdir /mnt/winfat

At this point, I would reboot. Your partition should then be recognized and usable.

john

---

### Post by pennyminstrel on 2006-07-25
Thanks for your help OU812....

[I]First we need to find its name. In a terminal do

sudo /sbin/fdisk -l

Look for an entry with W95 FAT32 in the last column. As an example, let's say the device name is /dev/hda5. Now we need to update fstab. From a terminal do

sudo gedit /etc/fstab

add the line

/dev/hda5 /mnt/winfat vfat rw,users,umask=000 0 0[/I]........

I got this far, and received a message saying bash: /dev/hda4: permission denied (/dev/hda4 being the device name). Any suggestions?

Also, whaat did you mean by 'I usually put this with the other hard drive entries (hda or hdb). '  Where do you do that?

Thanks again

Penny

---

### Post by OU812 on 2006-07-26
Ok. That is the entry I have always used. I just installed kubuntu. Here is the entry generated by kubuntu

/dev/hda2       /media/hda2     vfat    defaults,utf8,umask=007,gid=46 0       1

Modify as needed and give it a try.

john

---

### Post by Sef on 2006-07-26
> I created some space to create the /home partition in but when I tried to format this as ext 3 it told me I couldn't have than 4 partitions and i would have to create an extended partition with logical drives. I do remember reading something like this before so I wasn't surprised, but I can't find anythng that tells me how to do this.

You can have more than 4 parititions, but you can't have more than 4 primary partitions.  If you want more than that, you need to have logical (extended) partitions.

---

### Post by pennyminstrel on 2006-07-26
thanks OU812, I'll give that a try.

Sef, what's confusing me is that I only have 3 primary partitions plus the swap file which is already in an extended partition (see my screenshot earlier in this thread)

thanks everyone for all your help. I'm finding getting used to ubuntu really hard, but then its probably only as hard as it was getting your head round pc's at all years ago.

penny

---

### Post by pennyminstrel on 2006-07-26
The other thing was that I thought it would be a good idea to give some of the free space in the ubuntu partition to the FAT32, but because you can only increase or decrease to the right of a partition and the FAT32 is on the left of ubuntu I can't do that.Would it matter if the FAT32 was on the right of ubuntu; it would then no longer be between windows and ubuntu.

I've attached a screenshot in case this is all confusing you.

---

### Post by Ares Drake on 2006-07-27
> **pennyminstrel said:**
> Would it matter if the FAT32 was on the right of ubuntu; it would then no longer be between windows and ubuntu.

Should be no problem at all. Just remember the numbers of your /hdaX change in this case.

---

### Post by pennyminstrel on 2006-07-27
_OK, this is where I'm at:_

Partitions from left to right:
/dev/hda1,ntfs with windows on
/dev/hda4,FAT32
/dev/hda2,ext3 with ubuntu
unallocated space
/dev/hda3,extended,with one logical drive /dev/hda4 containing linux swap
I've attached a screenshot too.


_What I want to do:_

1. be able to access /dev/hda4 and use it for my shared files 

2.create a /home partition in the unallocated space and add the remaining unallocated space to /dev/hda4


_Problems:_
1. I've followed everything everone's told me, but I still can't get at the FAT32 partition.

2. If I try to create a partition for /home, it tells me I've already got 4 primary partitions and I must first create an extended partition. However as far as I can see I've only got 3 primaries. I also tried increasing the size of /dev/hda3 to put the /home partition in there, but it won't let me resize.



I really feel I need someone to hold my hand through this process and  I'm now worrying that I've made various changes to the installation, some of which may be wrong and I'm just storing up trouble for the future. Should I just reinstall ubuntu and start again? 

I'm even wondering whether it would just be easier to wipe the lot (I am backed up you'll be glad to know) and partition the drive from windows, but I'm really committed to changing to linux and I don't want to give up.Somebody help, please!

---

### Post by Ares Drake on 2006-07-27
> **pennyminstrel said:**
> 
_What I want to do:_
1. be able to access /dev/hda4 and use it for my shared files 
_Problems:_
1. I've followed everything everone's told me, but I still can't get at the FAT32 partition.


You need to create an empty folder (e.g. in your home folder) and mount your Fat32 Partition there. Here is an easy-to-follow guide: [http://doc.gwos.org/index.php/DapperGuide#Windows](http://doc.gwos.org/index.php/DapperGuide#Windows)

> **pennyminstrel said:**
> 
_What I want to do:_
2.create a /home partition in the unallocated space and add the remaining unallocated space to /dev/hda4
_Problems:_
2. If I try to create a partition for /home, it tells me I've already got 4 primary partitions and I must first create an extended partition. However as far as I can see I've only got 3 primaries. I also tried increasing the size of /dev/hda3 to put the /home partition in there, but it won't let me resize.


You can either have 4 primary partitons or 3 primary and one extended, I suppose. You can only resize partitions to the right side - but hda3 is already as right as can be.

So I suppose there are 2 ways of archiving your goal:
1) Use a Windows software like Partition Magic, it can resize and move your partitions as you want it, I think (-no guarantee!)
2) Delete your Linux partitions and start over installing Linux again.

If you choose the later, I suggest you delete all partitions execpt the windows one (/dev/hda1) and create one large extended partiton for the rest of the space. In this extended partiton you can create logical partitons for your linux, home, swap and a FAT32 partition for shared data. Be sure to have the size of each planed out - changing partitions **after** the operating system is installed is always a pain in the a...

---

### Post by RRS on 2006-07-27
> create a /home partition in the unallocated space

Two possible solutions;
Resize the extended partition to include the unusable space and create your /home there. I think it's only ext3 that can't be expanded forward, not 100% sure though.
Or;
I don't recall a limit to the number of extended partitions, only primary. If true you could create another in the unallocated space.

I'd also suggest you try the gparted live cd [from here]("http://gparted.sourceforge.net/livecd.php") rather then using it from the Ubuntu live cd, works a little better.

Just thought of a 3rd option, delete the extended partition with swap in it and create a new larger extended and then recreate your swap in the new one.

> be able to access /dev/hda4 and use it for my shared files

[This guide]("http://www.psychocats.net/ubuntu/mountwindows.php") will take you thru the steps needed to mount both your Fat32 and NTFS partitions. You won't be able to write to the windows partition but you can read and copy from it.

Hope this helps solve your problems.

---

### Post by Indras on 2006-07-28
> **Ares Drake said:**
> 1) Use a Windows software like Partition Magic, it can resize and move your partitions as you want it, I think (-no guarantee!)

I know Ares Drake meant well with this comment, but I very very highly recommend against using Partition Magic with Linux partitions.  I've had it hose a perfectly good ext3 partition twice, once on my main machine (ouch!) and the other in VMWare while testing out a dual-boot config.  It does not matter if you're moving or stretching an ext3 partition, it will do most of the job and then suddenly fail at the end while rewriting the tables, leaving you with a completely unusable partition.

I've heard good things about using Acronis Disk Director, so perhaps you could try that, but all in all, I'd just stick with stuff you can do in gparted.

---

### Post by Ares Drake on 2006-07-28
> **Indras said:**
> I very very highly recommend against using Partition Magic with Linux partitions.  I've had it hose a perfectly good ext3 partition twice, once on my main machine (ouch!) and the other in VMWare while testing out a dual-boot config.  It does not matter if you're moving or stretching an ext3 partition, it will do most of the job and then suddenly fail at the end while rewriting the tables, leaving you with a completely unusable partition.

Uuuh, thanks, I didn't know that, I very much appreciate the warning!

---

### Post by pennyminstrel on 2006-08-01
Thanks so much for all your help guys.
I'm ashamed to say that I got so frustrated in the end that I gave up and decided to reinstall ubuntu from scratch. I had a feeling that I might have messed up one or two other things i'd been playing with so all in all it seemed the easiest option.

that said, i'd learnt such a lot in the previous few days that i felt quite confident to set up the partitions exactly as I wanted during the reinstall and yippee! it works! so now i'm feeling pretty pleased with myself and my daughter is now going to put ubuntu on her pc too.

just one other question, apart from a few others which i hope to find the answers for somewhere on the forums - is it possible to rename the partitions from dev/hda 123etc to something more descriptive, eg window, documents,etc?

penny

---

### Post by Ares Drake on 2006-08-01
> **pennyminstrel said:**
> just one other question, apart from a few others which i hope to find the answers for somewhere on the forums - is it possible to rename the partitions from dev/hda 123etc to something more descriptive, eg window, documents,etc?

Well, yes and no. You cannot change the the name linux calls the partitions, internally, i.e. /dev/hda1. You can however change the way they are shown to you, i.e. the path where you find them. Instead of having them in /media/hda1 you could have them in, lets say /home/YOURUSERNAME/windows. To do that, you need to either change SYSTEM -> Administration -> Disks, or change the file /etc/fstab. (wich is where SYSTEM -> Administration -> Disks stores its settings). If you need help with the fstab file, have a look here: [http://doc.gwos.org/index.php/DapperGuide#Windows](http://doc.gwos.org/index.php/DapperGuide#Windows) or search for "howto AND fstab"

---

### Post by pennyminstrel on 2006-08-03
Thanks for this Ares Drake. I'll have a go. just one last thing, hope you don't mind. 

I'm still learning about editing configuration files and feeling a bit nervous of it(I've only had linux a week) and I'm not sure whether you should delete what's there and replace it or whether it's ok just writing the new text will just override the old. Sometimes instructions people give explicitly say to delete something first, sometimes they just give you the new code. Or maybe it depends on the situation.

thanks again

penny

---

### Post by Ares Drake on 2006-08-03
Well, as you already guessed, it depends ;)

First of, I can only strongly suggest to always make backup copies before editing config files - if something breakes, you can easily copy the backup over.

Second, it's very rarely necessary to delete everything in a file when you change something. Usually you will be explicitly told about deleting.

Instead of deleting, you may put an # at the start of the line. Then this line will be ignored by linux.

Third: Usually when you change a config file, you add a configuration for something that was not configured at all before. Like a fresh virgin fstab might have not configured all your partitions, so you add it -no need to delete something anyway.
When you however change a configuration made before (i.e. changing /dev/hda5 to be mounted to /home/username/win instead of /home/username/data) then you can just modify the existing lines. So if you are unsure about deleting, just have a look on what's already there. It might work if you had a line saying to mount /dev/hda5 to /home/username/win and a second line saying mounting to /home/username/data, i don't know. However it would be a mess and difficult to understand if you wanted to make changes later on. So I suggest to try to keep the config files as clean and structured as possible :)

So best wishes for a nice experience with your new linux!!

---

### Post by pennyminstrel on 2006-08-03
thankyou!

---


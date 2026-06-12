---
title: "Dual boot / Disk Partioning"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by 01steven on 2007-11-01
Hi
I'm a Windows XP user who's just about to make the switch to Linux/Ubuntu.
Been getting to grips with Ubuntu through a live CD but haven't as yet done a full install.

I think I'd like to be able to dual boot into Windows or Ubuntu and want to be 100% sure that I know what I'm doing before I mess up my computer in the process!

My laptop has a 60GB hard drive. I've backed up all the files I need onto an external hard drive.

I've been looking at the Graphical Install help page in the documentation:
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

I'd like some advice regarding the 'Select a Disk' section.
Should I just use the 'Use the largest continuous free space' option?
I've read that I should allow 20GB for Ubuntu. Is that including any files I may subsequently generate/download etc.?
How much space will Windows XP need?

All advice on this issue will be greatly appreciated.

Many thanks
Steven

---

### Post by Partyboi2 on 2007-11-01
> **01steven said:**
> Hi
I'm a Windows XP user who's just about to make the switch to Linux/Ubuntu.
Been getting to grips with Ubuntu through a live CD but haven't as yet done a full install.

I think I'd like to be able to dual boot into Windows or Ubuntu and want to be 100% sure that I know what I'm doing before I mess up my computer in the process!

My laptop has a 60GB hard drive. I've backed up all the files I need onto an external hard drive.

I've been looking at the Graphical Install help page in the documentation:
[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

I'd like some advice regarding the 'Select a Disk' section.
Should I just use the 'Use the largest continuous free space' option?
I've read that I should allow 20GB for Ubuntu. Is that including any files I may subsequently generate/download etc.?
How much space will Windows XP need?

All advice on this issue will be greatly appreciated.

Many thanks
Steven

Using the 'Use the largest continuous free space' is the easiest way I think. As for size of partition depends really on personal preference. Xp works well with about 10gig. If you are planning on using ubuntu more then I suggest making that a larger size partition.
You could just go for 30 gig win and 30 gig ubuntu. Can always resize at a later date.

---

### Post by benerivo on 2007-11-01
At the moment, your 60GB disk is probably just one big partition with XP on it with no free space. Firstly, I would go into XP and check how much space is left on the drive, and also defragment the drive twice. My Ubuntu partition is only 8GB, and the standard install only uses around 2GB. So what I would do next, is to boot in to the live cd, and run the Gparted Partition Manager from the menu. From here you can shrink your XP partition to create at least say 8GB free space. From here you can run the installer and select the 'Use the largest continuous free space' option.


EDIT > If you want to ditch windows you are best off making the Ubuntu partition as large as possible. Partyboi2 is right, XP only needs 10GB - but it depends on how many apps / games you have installed on it already.

---

### Post by Crandom on 2007-11-01
It depends what your going to use more. Leave some space for xp if your still going to use it, but give some to ubuntu. 10gbs is fine for the main OS block of ubuntu. Here's what to do.

In xp, go into Disk Management and right click the disk your going to use then press Shrink Volume... Shrink it by 11Gb (11264mb). You should now have 11Gb unallocated space.

Load up your ubuntu live cd and go System > Administration > Partion Editor. Select the correct hdd using the drop bar at the top-right hand corner and make these partitions:

[LIST=1]
[*]8Gb - ext3
[*]1Gb - ext3
[*]2Gb - linux-swap
[/LIST]

Now check the 8Gb partition - it should be called something like /dev/hdax where x is a letter. REMEMBER THIS.

Load up install, and when you get to the install locaton step choose Manual. Make the:

[List=1]
[*]8Gb - ext3 - format it - Mounted as: / 
[*]1Gb - ext3 - Mounted as: /home
[*]2Gb - linux-swap - Mounted as: swap
[/list]

contiune until you get to step 7 of 7. Click advanced. Instead of the normal (hda) it says in where to "install bootloader" change this to /dev/sdax where x is the letter you remembered. [COLOR="Red"]EDIT: WAIT FOR CONFIRMATION BEFORE DOING THIS; IT MAY BE (hda0,x) I CAN'T REMEMBER[/COLOR]

the /home partition (where you store your documents and settings) isn't very big because you can just use your xp partition to store documents. The reason for splitting them is so you can do a clean install to / when an update comes out.

---

### Post by mikewhatever on 2007-11-01
How much free space is there, and how is the disk partitioned? The regular Ubuntu installation requires only about 3 BG of space, but more is advisable to allow you to install more software. If you can allocate about 20 BG, that is excellent.
Please review some suggested schemes here [http://psychocats.net/ubuntu/partitioning](http://psychocats.net/ubuntu/partitioning)

---

### Post by 01steven on 2007-11-01
Thanks for all advice so far.
Sorry if this sounds like an obvious question, but if I only give say 20GB to Ubuntu, and I want to import videos/music etc. - does that mean I'll only be able to use up to a maximum 20GB of hard disk space within Ubuntu?

---

### Post by alpha080 on 2007-11-01
if you only give 20GB to Ubuntu,and you just have a maximum 20GB of hard disk space
wiehin Ubuntu,but you can write  ntfs in XP .

---

### Post by 01steven on 2007-11-01
Sorry I don't understand this.
Please can someone explain this to me in plain english?
Forgive me for being ignorant, but that's what this forum is about isn't it?!
Thanks

---

### Post by benerivo on 2007-11-01
> **01steven said:**
> if I only give say 20GB to Ubuntu, and I want to import videos/music etc. - does that mean I'll only be able to use up to a maximum 20GB of hard disk space within Ubuntu?

Yes. Any file that is saved or imported on the Ubuntu file system wil take up part of the 20GB. You can if you want, save or keep files elsewhere on the computer such as on an external hard drive, or on your xp partition, and still be able to open them from Ubuntu. Much like someone who saves music files to an external hard drive, yet can still open them from xp.

Keeping all your personal files on a separate partition or external disk can be very useful, especially if you plan to dual boot.

---

### Post by 01steven on 2007-11-01
OK, so bearing in mind I'll probably need more than 20GB of hard disk space for videos/photos/music etc., what do you think would be my best strategy?
Is it simple to access the files on a separate partition?
I have an external hard drive but it's not always convenient to keep it plugged into laptop.

---

### Post by 01steven on 2007-11-01
Also, if at some point I decide I no longer need to use XP what are my options? Can I increase the size of the Ubuntu partition, or even make it the size of the entire hard drive, without having to re-install Ubuntu?

---

### Post by maybeway36 on 2007-11-01
I think you can resize ext3 and reiserfs. Then you would just remove Windows from your menu.lst.

---

### Post by benerivo on 2007-11-01
> **01steven said:**
> OK, so bearing in mind I'll probably need more than 20GB of hard disk space for videos/photos/music etc., what do you think would be my best strategy?
Is it simple to access the files on a separate partition?
I have an external hard drive but it's not always convenient to keep it plugged into laptop.

> Also, if at some point I decide I no longer need to use XP what are my options? Can I increase the size of the Ubuntu partition, or even make it the size of the entire hard drive, without having to re-install Ubuntu?

If it's not convenient to have the external drive plugged in, then I would reduce XP as much as possible. Check how much XP takes up now, defrag at least twice, and then shrink (using GParted Partition Manager) to leave XP only 5GB more than it currently uses. Then still in Gparted, make a 1 GB swapfile partition (for swap), an 8GB ext3 formatted partition (for Ubuntu), and the rest (eg. 45GB) as an ext3 partition for your videos etc. It is very simple to access files from another partition (no different to the way you now work with your external drive) Then install selecting 'Manually edit partition table. Install '/'  on to the 8GB partition ('/' is the linux root and will contain the whole of Ubuntu). Then that's it. If you want to get rid of XP at a later date you can format this partition and use it as extra storage.

---

### Post by benerivo on 2007-11-01
And i'd also reccomend reading this on Ubuntu partitioning and installation. It's excellent.

[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

---

### Post by mikewhatever on 2007-11-01
Nobody ever said your files, music and videos must be on Ubuntu partition. They can be anywhere else, say, storage or Windows partition and access them from Ubuntu. Gutsy Gibbon can read and write to NTFS by default. You'll need the space on Ubuntu partition to install programs, things like vmware, etc. If you Know in advance, you do not want a lot of programs, 5 GB would be more then enough.

---


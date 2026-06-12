---
title: "Mounting NTFS Partitions"
date: 2006-04-18
forum: Absolute Beginner Talk
---

### Post by jazzyt on 2006-04-18
Hey guys, I'm pretty new to the Linux World and would appreciate some help on a problem I am having. 
Heres the Setup:

Windows XP NTFS Partition  :   /dev/hda1
NTFS Data Partition : /dev/hda2
Ubuntu on another .....

I am trying to mount and view/edit files saved to these partitions through Ubuntu.....
First I tried doing it through the GUI, and for some reason ran into permissions issues, with the mounted folders being read-only.

Next I tried from the prompt --->    mount /dev/hda1 /home/<username>/<folder_name>
Of course I had to be su to do this, so the permissions were the default 644 with root as the owner/group. I can view the files in the partitions, and cat text files such as boot.ini.... however I cannot change the owner of the <folder_name>(using chown) or chmod the permissions... 
This is probably a very simple thing..... please be gentle! lol.. 
P.S. I have tried chmoding/chowning as both users and as root...

edit : Just read something that said MS Windows NTFS = read-only... that would explain a lot.. lol

---

### Post by Nequeo on 2006-04-18
You're not actually doing anything wrong. NTFS is a closed Microsoft format, and despite valiant attempts to reverse engineer it - write access isn't really stable enough to make it safe for general use. You can find more information here:
[http://www.linux-ntfs.org/](http://www.linux-ntfs.org/)

The generally accepted way to share data between Windows and Linux on the same computer is to have a FAT32 formatted data partition. 

[EDIT] There are also some utilities that let you access Ext3 partitions from Windows. Pretty sure there are some free ones, too. Never used any - but if you Google around I'm sure you'll find some. You could always copy the files onto the Linux partition, edit them, then boot into Windows and copy them back. [/EDIT]

Hope that helps a little,

---

### Post by WolfJay_83 on 2006-04-18
<edit> awe, man, too slow... crazy similar reply<>


NTFS is a "secret" microsoft file system and reverse engineering read/write support has been difficult for linux developers.  So, generally, it's not recomended to try to write to NTFS partitions that have not been backed up.  You may want to educate yourself before trying to write to it. 
[https://wiki.ubuntu.com/NTFSReadWrite](https://wiki.ubuntu.com/NTFSReadWrite)
[https://wiki.ubuntu.com/MountNtfsOnBoot](https://wiki.ubuntu.com/MountNtfsOnBoot)

 An alternative, if you want a filesystem that is the "least common denominator" that works with both windows and linux, use a fat32 filesystem.  (but remember to defrag and all that old-school stuff).

---

### Post by yager on 2006-04-18
Here is the link to a previous thread around this same topic.

[http://www.ubuntuforums.org/showthread.php?t=155368](http://www.ubuntuforums.org/showthread.php?t=155368)

The issue is that you will need some additional tools to be able to edit the files as NTFS is not officially read/write under Linux yet.  Write is still experimental and to be used only at your own risk.

The safest approach is to set up a partition on one of your drives as FAT or FAT32 that could then be shared between Windows XP and Ubuntu.  This is the safest option but of course this may not be possible in your case.

Update:  I don't want to look like I am piling on.  I only took 3 minutes to type this answer and everyone was there to help right as well.  This is a great community of people who all want to help each other.  I love it here.

---

### Post by jazzyt on 2006-04-18
Cool thanks for the replies guys! 

RE: Yager...

Agreed the speed of help and quality of advice I've read on here so far is definetly better-than-par.

---


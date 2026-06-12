---
title: "changing my user folder ?"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by enfantterrible on 2007-06-15
hello all

i have one 80gb hd (40 gb winxp, 40gb ubuntu) and a fat32 320gb hd that i use as a shared data repository between xp and ubuntu (and where all my userdata goes)

can i change my home folder (and all the folders for users i create) to that drive (which now is /media/hdc1/) ?

and... what happens to windows? will any user in xp be able to browse my ubuntu home folder, when ubuntu is not running ?

thx...

---

### Post by Golyadkin on 2007-06-15
You can change the mount point of /home to the big drive yes. For that you have to edit /etc/fstab

Now, your shared drive doesn't have to be FAT32 to work with Ubuntu, Ubuntu can read and write NTFS very well too :) NTFS is much faster and allows you to store larger files.

---

### Post by enfantterrible on 2007-06-15
thanks golyadin - i'll read some on fstab hoping to make no harm :)

and ntfs support... i am still at the "out-of-the-box" efficiency... upgrades later!!
thx

---

### Post by machoo02 on 2007-06-15
Alternatively, Windows can also read/write to ext2/3 drives with the [Windows Ext2 driver]("http://www.fs-driver.org/").

---

### Post by Happy_Man on 2007-06-15
What about using [http://psychocats.net/ubuntu/separatehome](http://psychocats.net/ubuntu/separatehome)? That works too....

---

### Post by avik on 2007-06-15
My guide of choice (the one I used) is [http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/]("http://ubuntu.wordpress.com/2006/01/29/move-home-to-its-own-partition/").

I have Ubuntu on a 10GB IDE HDD and my /home directory on a 250GB SCSI HDD.

---

### Post by enfantterrible on 2007-06-16
thanks for the tutorial, i will do it right now.

my question is... will any winxp user be able to enter my home folder without problems??

---

### Post by avik on 2007-06-16
> my question is... will any winxp user be able to enter my home folder without problems??

No, not unless they install something like Ext2 ([http://www.fs-driver.org/]("http://www.fs-driver.org/")).

---

### Post by Golyadkin on 2007-06-16
> **avik said:**
> No, not unless they install something like Ext2 ([http://www.fs-driver.org/]("http://www.fs-driver.org/")).

If the filesystem of the partition the home directory is on is NTFS or FAT32, the Windows users can read and write those files without trouble. 

However, I do not know how this works with case sensitive filenames. Linux knowns the difference between a file called "Thesis.doc" and "thesis.doc" and will allow them both to be in the same directory. Windows however will cough, choke and throw up when it sees these two files in one directory.

---

### Post by enfantterrible on 2007-06-20
yes, my shared folder is in a FAT32 partition - i dont plan in making all filenames the same with different cases though.
i think i should just remove winxp then... only too bad there's no itunes here (and no other softwear i tried manages my ipod the same easy - hasslefree way)..

---

### Post by Golyadkin on 2007-06-20
I heard good things about Amarok and Banshee. But I don't have an iPod, so I don't know about whether it is supported well. A program called GTKPod should allow you you to synchronize your iPod with Ubuntu.

[here is another big guide]("http://www.linuxjournal.com/article/9266").

---

### Post by enfantterrible on 2007-06-25
i am starting reading it (the ipod guide) and thanks - looks like a pretty good guide.

unfortunately though i am starting to udnerstand that until itunes will be ported to linux (maybe never) there will never be a perfect way to manage it.

i have a few good mp3 player programs and a couple good ipod managers but problem is all the same: music programs dont manage ipod well enough (it's not a matter of transferring files from one hard disk to the other) and ipod managers suck as music playing programs.

i switched to ubuntu and not planning to go back anytime soon - but since i have ubuntu, i cant listen to my favourite music on the ipod the way i used to (aka, plugging the ipod on the usb and having intelligent playlists managing the synchronization without touching anything else - from the same program i listen music to)

---


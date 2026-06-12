---
title: "cannot write to other partition"
date: 2007-06-10
forum: Absolute Beginner Talk
---

### Post by ongla on 2007-06-10
I'm newby for linux.
I'm have worked with partition magic in windows but it failed.And it lock this partition. So I can't access to my whole works in that partition.But in Ubuntu ,I can see my whole files (about 30 GB). I want to copy to another partition that windows know it.When I try to copy my files(by drag 'n drop) it tells that "You do not have permissions to write to this folder" .(My lost files are in /sda7  and I want to copy them to /sda6X
So help me please.
Thanks so much.
ongla (from Tailand)

---

### Post by drowner on 2007-06-10
could you show us the output of 

sudo fdisk -l

and

cat /etc/fstab

---

### Post by ongla on 2007-06-10
My fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda7
UUID=56166994-629b-4c47-a11a-8f3264834d78 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=7E2045462045071D /media/sda6     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda6
UUID=70B0CAA5B0CA70E0 /media/sda7     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda8
UUID=e33a91eb-88a8-4aa5-9f24-5ef8c70c55f3 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


.........................................................

sda6  is partition D inwindows
sda7 is partition E in windows (that is locked by partiton magic and I cannot access to this part.in windows , and all of my files are here.)
And I want to copy my files from  sda7 to sda6
so help me please

---

### Post by drowner on 2007-06-10
sda7 is an ext3 partition.

I dont think this was 'locked' by anything

It is a linux file type, and it cannot be written to by windows (without installing programs).

I am not sure exactly what happened.

Can you give me a rundown of how you 'locked' the partition, and possibly what data is there, like did you save it to there from ubuntu or windows?

ta.

---

### Post by drowner on 2007-06-10
and the reason you can't write to the sda6 is because that is a NTFS filesystem, for windows, and linux cannot write to it without drivers

But before we install them, i really would like to know what you are trying to do.

On your sda7 is where your linux install is. If you had work in there previously from windows, this partition was created when you installed ubuntu, when you made the sda7.

Tell me the history of your computer

---

### Post by ongla on 2007-06-10
1. I've 2 hdd  no.1 is  (IDE) 40 gb Seagate that  I,ve installed windows XP. And it was Drvie C
2. No.2 hdd is 200 GB (SATA) that I've made to drive D,E  and I 've kept all of my files in drive E
3. I've worked with Partition Magic to resize drive E  to have free space for Linux
4. While I've worked with partitonmagic it hanged and it changed that partition to PqRP that windows cannot access it anymore
5. I use only SATA (200 GB) to installed Ubuntu 7.04 

And now in my ubuntu destop ,I can find that all of my files are in /media/sda7 (that cannot access in windows) and I want to copy all of these files to /media/sda6 (that can access in windows)
When I drag these files to sda6 it tell that I have no permissions to write to this folder.

so help me pls.

---

### Post by drowner on 2007-06-10
Ok cool.

[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

That thread has the info. We can help if you need.

I still don't understand why linux can read that partition but windows cant.

---

### Post by ongla on 2007-06-10
I'll try more to fix this.
Thanks so much

---


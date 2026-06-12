---
title: "Make sure I mounted and allowed access to these partitions properly."
date: 2006-06-06
forum: Absolute Beginner Talk
---

### Post by Sydney Losstarot on 2006-06-06
I've been messing around some, and I think I've finally managed to mount my partitions where I want them, and allow myself access to them.  I also thought I'd be a good idea to ask some of you more experienced users if I've done this appropriately.

My hard drive looks like this:

primary partition
{
  15GB NTFS; for Windows
}
extended partition
{
  logical partition  {  9.5GB ext3; for /  }
  logical partition  {  500MB for swap  }
  logical partition  {  50GB ext3; for my data  }
}

Originally, my ubuntu install would only automatically detect my 9.5GB NTFS partition, and it was mounted to /media/sda1.  My goal was to get the 50GB ext3 partition mounted and accessible to a convenient directory.  What I did was use the Disks tool under System -> Administration to figure out what ubuntu had named it, and then added a line in /etc/fstab to get it to mount to /home/<my name>/Archive.  This it successfully did, but I couldn't write to it.  After some thinking, I ran nautilus using 'sudo nautilus' and changed the permissions on the /home/<my name>/Archive directory to allow me, the file owner, to write to it.  This also worked.

I'd originally decided to mount my data partition in /home/<my name>/Archive because, at that time, I thought it would allow me to write to it, because I could already write to /home/<my name> (I didn't know about file permissions).  Now that I've realized that changing the file permissions allows me to access it from anywhere, I decided to move it to a location that made more sense.  I decided that that location would be /media/Data.  So to move it, I unmounted it from /home/<my name>/Archive using the Disks tool, then modified /etc/fstab to mount it to /media/Data.  Then I deleted the /home/<my name>/Archive directory, made a /media/Data folder, and restarted my computer.  This worked, but I have a question about it.  Sometime during the moving process, a warning showed up in my terminal window telling me that nautilus was saying "file already in tree" and then something about a null parent pointer.  Is this significant?  Everything seems to work fine.

I used the same process to rename the file that ubuntu had mounted my 15GB NTFS Windows partition in (from sda1 to Windows, I think it makes more sense), and I remember getting the same warning.

I plan to use fs-driver ([www.fs-driver.com](www.fs-driver.com)) to allow Windows to read my 50GB ext3 partition, and then use that 50GB partition to store both my Windows programs/stuff and my ubuntu programs/stuff.

Opinions?  Could I have done this better?

I have some random questions now.  

1. Can I use the Windows defragmenter to defragment ext3 partitions (for example, my 50GB ext3 partition) when I have fs-driver installed?

2. Would it have been better for me to format the 50GB ext3 partition as a FAT32 partition?

3. Any difficulties in running programs in Windows from my 50GB ext3 partition?

4. Check out this copy of my /etc/fstab file, and make sure it looks alright.  Pay close attention to the /dev/sda7 line, because that's the one I added myself.

----------------------------------------------------

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda5       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda1       /media/Windows     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sda6       none            swap    sw              0       0
/dev/sda7	/media/Data	ext3	rw,user	0	1
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

------------------------------------------------------

5. What do the numbers under the columns <dump> and <pass> mean?

6. Are files that have a period (.) as the first character in their name the ubuntu equivalent of hidden files in Windows?

---

### Post by gerbman on 2006-06-06
[QUOTE=Sydney Losstarot]Opinions?  Could I have done this better?[/QUOTE]I think what you've done sounds reasonable.

> Can I use the Windows defragmenter to defragment ext3 partitions (for example, my 50GB ext3 partition) when I have fs-driver installed?No need to defrag ext3 drives. Isn't that nice?

> Would it have been better for me to format the 50GB ext3 partition as a FAT32 partition?I'm not sure of the technical comparison, but FAT32 would probably be easier to share between Ubuntu and Windows.

> What do the numbers under the columns <dump> and <pass> mean?I'm not sure about dump, but pass specifies the order in which the partitions are checked by fsck at boot-up time. The man page for fstab says the pass value should be 1 for the root partition and 2 for other partitions.

> Are files that have a period (.) as the first character in their name the ubuntu equivalent of hidden files in Windows?Yup.

---

### Post by catlett on 2006-06-06
[http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html) It is easiest to send you to this page. It explains /etc/fstab clearly and concisely (at least I think so). I use ext3 but I haven't run a program out of it. I would read up on it at their sight first. But if you don't have data on it yet, I would make it Fat32. That way you DEFINATELY aren't going to get issues. Fat32 is well supported in windows and linux. If you don't have too much importabt data I wouldn't go crazy to change it to fat32.

---

### Post by Sydney Losstarot on 2006-06-06
No need to defragment ext3 partitions?  That's great.

I'm planning on storing important stuff on that large 50GB ext3 partition from Windows, as well as run games off of it from Windows, so it needs to be stable as I do those things.  I don't have any data on that 50GB ext3 partition that isn't backed up.  Would I be smart to make it a FAT32 partition?

I've heard that ext3 partitions are faster than FAT32 partitions.  True?  If so, that could help the hard drive access times while gaming.  Plus, there's no need to defragment ext3 partitions, apparently.  I'm somewhat reluctant to give that up ...

Opinions on anything in my first post are still welcome.

---

### Post by gerbman on 2006-06-06
It sounds like the partition's primary use will occur in Windows, so it might be best to format it with FAT32 if Windows supports FAT32 without additional drivers. I haven't had any problems with my FAT32 filesystems.

---

### Post by Sydney Losstarot on 2006-06-06
Yeah, the partition's primary use would be from Windows, but I've heard that ext3 is faster, plus, as you say, it doesn't need defragmenting.  I'd like to get more input on this before I make a move, just to be sure.

---

### Post by obnibolongo on 2008-02-05
Well hopefully someone will have this thread subscribed, since this is old...

Anyway, I just to say this and expect someone to correct me (or not): AFAIK, the fs-driver.org's ext2 Windows driver doesn't handle the defragmentation thingy as well as a Linux ext2 driver.

After some heavy file copying over a network share using Windows to a ext2 partition mounted on Windows, I'd have around 15% non-contiguous files which, considering the partition wasn't full (can't remember how much free space I had, sorry) was considered by me as too much...

Was it a coincidence or doesn't the ext2 Windows driver com fs-driver.org handle "intern" defragmentation very well?

---


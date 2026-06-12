---
title: "Question: Setting file permissions"
date: 2005-11-21
forum: Absolute Beginner Talk
---

### Post by Listoff78 on 2005-11-21
Hello!  Allow me to run down my situation quickly before asking the question.

* hda1 is NTFS for Windows XP
* hda2 is a FAT32 data storage area (for use between both OS's)
* hda3 is EXT3 for Ubuntu
* hda4 is my swap area

... pretty standard dual-boot setup, I'm assuming.

Both operating systems can mount and see the FAT32 partition with no problems.  In XP, I can read and write to any folder I want, all day long.  For some reason, in Ubuntu, there are five directories that say I can't write to the directory.  Not only that, but I can't change the permissions because they're grayed out and it says I'm not the owner.  It says the root is the owner and I can't figure out how to log on as root to even attempt to reset things.

How do I reset the file permissions for these directories and have all the files and subdirectories inherit the same permissions?

Thank you in advance for your help!
Mike

---

### Post by earobinson on 2005-11-21
can you post your /etc/fstab

also do a ls -la in the dirs that you cant read or write to.

---

### Post by Kyral on 2005-11-21
I am going to assume that they are in the FAT32 partition. Thing is, FAT32 has no concept of file permissions (this data is actually stored within' the filesystem data). 

So, the best bet would be to add this to the options area in the FAT32 line (in the area where things like "defaults" and "rw" are)

```
umask=1000, gid=0000
```

I think that will work

---

### Post by Listoff78 on 2005-11-21
Here is the /etc/fstab/ that I edited last night to have the FAT32 partition automatically mount on bootup.



# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda2       /media/DATA  vfat    iocharset=utf8,umask=000 0 0

---

### Post by earobinson on 2005-11-21
make Kyral's changes then type sudo mount -a in the terminal.

also if its not the fat drive thats having the problems give us an ls -la of the directory

---

### Post by Listoff78 on 2005-11-21
It is indeed the FAT32 partition that's having the issue.

Kyral, I'm so new to this, and I fear sounding like an idiot...  Where do I make those changes you suggested?  in the /etc/fstab/?

Thank you everyone for your help and patience.
-Mike

EDIT:  ARGH!  I tried to add that info into the fstab and somehow it's locked to read only now too!  Grrr!

---

### Post by earobinson on 2005-11-21
/dev/hda1       /media/windows  vfat    iocharset=utf8,umask=000,gid=0000   0       0

Im a bit woried that this may not work however (since im assuming its only some dirs on the fat drive that dont work), but it cant hurt

---

### Post by Listoff78 on 2005-11-21
I actually already have that line in my fstab.  Still with the same result.

---

### Post by earobinson on 2005-11-21
You asked before where to put the gid=0000 since yours is missing that. (at least in your copy that you posted)

can you also do a ls -la of the dirs that you cant edit, and one that you can edit on the fat dir (even though fat shouldent have permisions)

---

### Post by Listoff78 on 2005-11-21
Sorry, I think I'm confusing myself and everyone reading.  My apologies for the confusion.  I will try to add that line into the fstab and see how that goes.

Here is a ls -la clip of the directory of my FAT32 partition.  I think this is what you're asking for:

I can't write to:  drwxrwxr-x  47 root root 98304 2005-11-19 22:04 My Music
I can write to:  drwxrwxrwx   2 root root  4096 2005-11-19 17:43 Recent Downloads

I'm having trouble editing the fstab at the moment.  It'll be a few minutes...

Thank you,
Mike

---

### Post by Listoff78 on 2005-11-21
SUCCESS!!!  I added the line:

/dev/hda2       /media/DATA  vfat    iocharset=utf8,umask=1000,gid=0000 0 0

As suggested to my /etc/fstab and it works perfectly!  I have no idea what it's doing, but it works!  Sorry for any confusion earlier.  I had a friend helping me on IM giving me suggestions at the same time forum members were giving me suggestions and I started to get the two confused.

But, everything works great.  Thank you so much everyone for your help.  It is much appreciated.  I only hope I get good enough at this that I can return the favor for someone soon!

Take care,
Mike

---

### Post by earobinson on 2005-11-21
gid is the groupe id that can use the partition. So now and gid 0000 is everyone (im pretty sure its everyone). Anyways now your account is in the group that can use the fat drive.

Glad we got your problem to work.

*extra points for posting the soultion at the end making it easy for other people to find it*

---

### Post by earobinson on 2005-11-21
double post :(

---


---
title: "cannot enable mounted partition"
date: 2007-01-31
forum: Absolute Beginner Talk
---

### Post by pluskwa on 2007-01-31
Hey, 
Before Installing ubuntu I'd made a partition, I've mounted it using fstab:
/dev/sda1	/storage	ext3	defaults	0	0
Now the partition is visible, But I cannot enable it. The funny thing is that i can copy the files but it doesn^t change anything. The drive still seems to be empty and it doesn't release any more free space on another artition.
Any clues?

---

### Post by PointSource on 2007-01-31
Are you sure the device node is correct (/dev/sda1 is usually removable disks like flashdrives)?

another suggestion is to add ",rw" just after "defaults" (before space) (I think thats part of the "defaults" settings, but its worth a try)

ext3 is also a permissions based filesystem, do you have the correct permissions for it?

---

### Post by PointSource on 2007-01-31
and also have you tried

sudo mount /dev/sda1

---

### Post by eternalsword on 2007-01-31
with an ext3 mount, the folder where it's mounted must have the correct permissions as well.  So you might want to unmount and see if you have permission to write there.  If not, chmod that directory and remount.

---

### Post by pluskwa on 2007-01-31
I try to edit fstab with
sudo -e /etc/fstab
but after i try to save the changes I get a message that i don^t have the permission to do this???

---

### Post by PointSource on 2007-01-31
If you are running as the user you first added to the system during installation then the command you have given should be running as root.

instead of "sudo -e /etc/fstab" try "sudo nano /etc/fstab" or "sudo gedit /etc/fstab" or "sudo kate /etc/fstab". Those last two are GUI editors and related to the GNOME and KDE desktops respectively.

---

### Post by pluskwa on 2007-01-31
+
when I type 
sudo unmount /dev/sda1
i get a reply
command not found

---

### Post by pluskwa on 2007-01-31
ok, i edit fstab, thanks
but still i cant unmount this drive

---

### Post by PointSource on 2007-01-31
Command should be:

sudo umount /dev/sda1

Just take out the "n" in the unmount.

---

### Post by pluskwa on 2007-01-31
ok, its umounted,
i  stil cannt enable it,
should I use chmod command now?
and which digits?

---

### Post by pluskwa on 2007-01-31
the properities of the /storage catalouge where i want to mount my drive are 
File owner: Root
Group owner: Root
Writing reading editing enable for everybody (but grey and impossible to change)
text view: drwxrwxrwx

---

### Post by pluskwa on 2007-01-31
Re: cannot enable mounted partition
the properities of the /storage catalouge where i want to mount my drive are
File owner: Root
Group owner: Root
Writing reading editing enable for everybody (but grey and impossible to change)
text view: drwxrwxrwx
Edit/Delete Message

---

### Post by pluskwa on 2007-01-31
And i cannot mount it again 
sudo mount /dev/sda1
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by PointSource on 2007-01-31
ARE YOU SURE its /dev/sda1, sounds very suspicious to me, and ext3 is not usually affiliated with that device node.

---

### Post by PointSource on 2007-01-31
could you expand a bit more on how you set it up, when, etc

---

### Post by pluskwa on 2007-01-31
when i go to system/adminstrations/disks it says 
Partition 1 
Device: dev/sda1
filesystem : extended 3
accespath: /storage
status : inaccesible

---

### Post by pluskwa on 2007-01-31
plus i set  it up by editing fstab
and it works for a while
but than it stoped

---

### Post by PointSource on 2007-01-31
> **pluskwa said:**
> when i go to system/adminstrations/disks it says 
Partition 1 
Device: dev/sda1
filesystem : extended 3
accespath: /storage
status : inaccesible

I cannot help you by the GUI because I'm running kubuntu (KDE)

Try editing fstab again but this time putting "auto" instead of "ext3".

Also please post the output of the console/terminal command "sudo fdisk -l" (this command can be potentially dangerous if you specify something other than "-l").

---

### Post by pluskwa on 2007-01-31
here u go

/dev/sda1               1        9197    73874871   83  Linux
/dev/sda2           11675       12161     3911827+   5  Extended
/dev/sda3   *        9198       11674    19896502+  83  Linux
/dev/sda5           11785       12161     3028221   82  Linux swap / Solaris
/dev/sda6           11675       11784      883512   82  Linux swap / Solaris

---

### Post by PointSource on 2007-02-01
Okay, I'm sorry for my disbelief, it really is /dev/sda1.

Try:
sudo umount /dev/sda1
sudo nano /etc/fstab
  ^ Then edit it and put in "auto" instead of "ext3" on sda1 line
sudo mount /dev/sda1

---

### Post by pluskwa on 2007-02-01
no prolem:)
even holy thomas disbelved

I unmount, change digits, but now whe i try to mount...

cis@cis-laptop:~$ sudo mount /dev/sda1
mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by PointSource on 2007-02-01
Not good.

I've almost used up my bag of tricks, and it seems to be getting nowhere.

And whats worse is that you had it half working BEFORE I tried to help!

A couple more attempts:
sudo fsck /dev/sda1
    ^ there might be a problem with the filesystem itself and thats why we cannot access it.

otherwise pehaps try mounting it with all info supplied on the command line:
sudo mount -t auto /dev/sda1 /storage

If all else fails you could always wipe it and rewrite the filesystem with gparted.

---

### Post by pluskwa on 2007-02-01
I think u were right

$ sudo fsck /dev/sda1
fsck 1.38 (30-Jun-2005)
e2fsck 1.38 (30-Jun-2005)
Group descriptors look bad... trying backup blocks...
fsck.ext3: Bad magic number in super-block while trying to open /dev/sda1

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

---

### Post by wirelessmonkey on 2007-02-01
It's looking like there may be a problem with that drive. After you've fsck'd it, you may want to recreate the filesystem on it, but not if you have important data on that partition. 

# umount /dev/sda1 
# rm -r /storage
# mkfs.ext3 /dev/sda1
# mkdir /storage  ## I would make this in either /media/storage or /mnt/storage instead  

then remount w/ full path

#mount /dev/sda1 /storage ( or /media/storage etc...)

As a last resort, I've seen some systems that didn't deal well with more than one swap partition...

If none of this works, try  # cat /etc/mtab and  post the results.




WM
________________________________________________________________________
[SIZE="1"]There is no heaven of glory bright, and no hell where sinners roast. Here and now is our day of torment! Here and now is our day of joy! Here and now is our opportunity! Choose ye this day, this hour, for no redeemer liveth. Say unto thine own heart I am mine own redeemer. [/SIZE]

---

### Post by PointSource on 2007-02-01
Well then, that makes it a whole lot easier. If you don't have any data on it, then you can use gparted to delete the partition and create a new one.

Otherwise, this command will do the same thing:
sudo mkfs.ext3 /dev/sda1

---

### Post by pluskwa on 2007-02-01
I cant use those commands???

cis@cis-laptop:~$ root mount /dev/sda1/ /media/storage
bash: root: command not found
cis@cis-laptop:~$ root cat /etc/mtab
bash: root: command not found

And amount works fine

---

### Post by PointSource on 2007-02-01
use the word "sudo" instead of "root"

---

### Post by pluskwa on 2007-02-01
wow ,

it works, great job, thanks 4 help:D

---

### Post by pluskwa on 2007-02-01
the last thing
i don't have permission to acces it
is ti good to change it with chown?

---

### Post by PointSource on 2007-02-01
I'm not sure if this will work, but try:
sudo chown {INSERT USER HERE} /storage

---

### Post by pluskwa on 2007-02-01
everyting works perfect
one more time lots of thanks

---


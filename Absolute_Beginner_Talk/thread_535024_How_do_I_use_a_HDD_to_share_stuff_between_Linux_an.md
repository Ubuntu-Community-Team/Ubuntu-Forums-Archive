---
title: "How do I use a HDD to share stuff between Linux and Xp"
date: 2007-08-25
forum: Absolute Beginner Talk
---

### Post by microsoft92sucks on 2007-08-25
I have Linux and Windows installed on 1 80gb HDD and I have another 80gb HDD that I want to use to put my files (music, pics, games ect) on how do I do this.
A howto link would be great or just tell me but please help. Thanks.

---

### Post by the.phantom on 2007-08-25
is the drive #2 external or internal?

the easy way would to have it formatted as FAT32
linux and XP can both read/write to it

if it is a usb drive there is a good chance it is already formatted in fat32

but that is just me a lightweight on Ubuntu

---

### Post by mckryptyk on 2007-08-26
You can use ntfs-3g and keep the drive NTFS. 

You will see a performance boost over using FAT32 and 
Ubuntu will be able to read and write to it just fine.

You can follow this thread here to read more about it:

[http://ubuntuforums.org/showthread.php?t=437670](http://ubuntuforums.org/showthread.php?t=437670)

This thread here has instructions to install it:

[http://ubuntuforums.org/showthread.php?t=217009&highlight=ntfs-3g+easy](http://ubuntuforums.org/showthread.php?t=217009&highlight=ntfs-3g+easy)
 
Cheers.

---

### Post by microsoft92sucks on 2007-08-26
Thanks for quik replys.
And I tried to format it to fat32 earlier but it gave me error with gpartion but then I tried again a differnt way in gpartion and It work.
I still cant access it in Ubuntu but I can in Xp Ill try those Links thanks.

---

### Post by logos34 on 2007-08-26
You need to create a mountpoint and add it to fstab:
[http://www.psychocats.net/ubuntu/mountwindows#fat32](http://www.psychocats.net/ubuntu/mountwindows#fat32)

---

### Post by thinsoldier on 2007-08-26
> **the.phantom said:**
> 
the easy way would to have it formatted as FAT32
linux and XP can both read/write to it
but that is just me a lightweight on Ubuntu

fat32 doesnt support files over 4 gigs (at least that's what windows keeps telling me :( )

---

### Post by mckryptyk on 2007-08-26
Windows tells you that, due to a limitation in file size creation for FAT32.

It could be worse, just wait till you get to the partition size limitation Windows XP has in creation FAT32 partitions.  :)

You are better off going with NTFS and ntfs-3g.

---

### Post by microsoft92sucks on 2007-08-26
OK I had it set up before so it was easy to mount again but I had to change the file system with
<code>
sudo nano /etc/fstab
</code>
So im able to look in it (its empty)
But I cant write to it. So How do I make it let me write to it.
Heres what it looks like now.
<code>
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=4862c251-f5a6-4039-a774-13502a423498 /               ext3    defaults,erro$
# /dev/sda5
UUID=34bedccc-c20f-4535-9d9b-98033de98518 none            swap    sw           $
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
<b>/dev/sdb1        /media/HDD2    vfat    rw,user,noauto        0       0<b>
</code>
and Ive tried
<code>
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=4862c251-f5a6-4039-a774-13502a423498 /               ext3    defaults,erro$
# /dev/sda5
UUID=34bedccc-c20f-4535-9d9b-98033de98518 none            swap    sw           $
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
<b>/dev/sdb1        /media/HDD2    vfat    defaults        0       0<b>
</code>
And thanks for all the help so far this is a really good forum.> 

---

### Post by microsoft92sucks on 2007-08-26
and y isent my html working ^
sorry about the sloppy look.

---

### Post by logos34 on 2007-08-26
Yeah, the formatting is all wonky tonight...can't do bold or anything.

But taking out the 'noauto' was a good move.

/dev/sdb1 /media/HDD2 vfat defaults 0 0

That should work.

To make changes, go

gksudo gedit /etc/fstab


Create mount point if it doesn't already exist:

sudo mkdir /media/HDD2

---

### Post by microsoft92sucks on 2007-08-26
I tried that it wont work?

---

### Post by logos34 on 2007-08-26
> **microsoft92sucks said:**
> I tried that it wont work?

what, creating the mount point or opening fstab with root priviledges?

---

### Post by microsoft92sucks on 2007-08-26
I can copy to it with 
<code>
sudo cp /something/somewhere.txt /media/HDD2
</code>
But not graphicly wich ide like.
Ive tried 
<code>
sudo chmod 777 /media/HDD2
</code>
but it still wont work.
So I tried changing the folder permission but it wont since im not root so my question is how do I become root and change it.

---

### Post by microsoft92sucks on 2007-08-26
> **logos34 said:**
> what, creating the mount point or opening fstab with root priviledges?

I got all the fstab stuff setup fine just dont know how to change the folder permision.

---

### Post by logos34 on 2007-08-26
try 

sudo chown <username> /media/HDD2

---

### Post by microsoft92sucks on 2007-08-26
<code>
spaje@EggHead:~$ sudo chown spaje /media/HDD2
chown: changing ownership of `/media/HDD2': Operation not permitted
</code>
Isent there a way to log on as root. To make me own it.
Or force it to let me own it.

---

### Post by logos34 on 2007-08-26
logon as root:

sudo -i

---

### Post by microsoft92sucks on 2007-08-26
It still wont let me even as root.
Could it have something to do with windows.

---

### Post by logos34 on 2007-08-26
try either of these fstab entries:

/dev/sdb1 /media/HDD2 vfat iocharset=utf8,umask=000 0 0

/dev/sdb1 /media/HDD2 vfat defaults,umask=0000 0 0

the umask setting should allow everyone access

reboot

---

### Post by microsoft92sucks on 2007-08-26
I got it thank u SO much.
By the y I like ur signature

---


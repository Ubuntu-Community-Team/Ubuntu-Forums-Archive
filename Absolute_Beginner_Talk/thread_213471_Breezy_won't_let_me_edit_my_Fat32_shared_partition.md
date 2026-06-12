---
title: "Breezy won't let me edit my Fat32 shared partition )c:"
date: 2006-07-11
forum: Absolute Beginner Talk
---

### Post by roncg41677 on 2006-07-11
This may be a bit confusing, so here is the basic chain of events:

   1. Did my first Linux HD install with Breezy, and was very happy.

   2. Tried to upgrade via the Update Manager to Dapper, with problems (due mostly I think to a slow internet connection) So I ordered the free CDs for Dapper.

   3. I thought that since my Breezy install wasn't acting right, I would install Mepis until I received the Dapper discs. When I installed Mepis I added a 10GB Fat32 partition to share with my XP (on the same HD, I'm dual booting). Everything worked fine in Mepis. I could read write and execute in both Windows and Mepis to the Fat32. However I really didn't like Mepis as much as Ubuntu so...

   4. I formatted and reinstalled Breezy, and (other than formatting the swap partition) left everything else untouched.

Now I do not have permission to edit the Fat32 drive. I can see it, and open documents from it, but I am unable to save anything onto it in Breezy.  It simply says "error while copying to hda4" or whatever the drive is, "you do not have permissions to write to this folder." In XP it's still fine. I tried to change the permissions, and it apparently let me, but then it seems to default back to the original permissions. I was thinking it might have something to do with the location of the partition. I think it is physically the 3rd (NTFS, then Ext2, then Fat32, then swap). But Ubuntu, during install called it hda4. If this is the problem I have no idea how to fix it. Any help is greatly appreciated!

---

### Post by john_spiral on 2006-07-11
you need root powers to write to a mounted drive, have you got super powers?

---

### Post by roncg41677 on 2006-07-11
Yes, I have super powers, I can melt things with my mind:) 

Seriously, no. I tried doing all of this as a regular user. In Mepis it was just a matter of saving to the drive or dragging and dropping, even logged in as a normal user.

So Ubuntu requires root permissions to be able to write to a Fat32 partition? Does that mean that any saving or editing would have to be done using the terminal? I am not quite sure how to do tasks as sudo in Gnome without using terminal.

---

### Post by bohboh on 2006-07-11
Post your /etc/fstab here

---

### Post by scxtt on 2006-07-11
ubuntu probably mounts the drive in a different way [umask issue] than mepis did (so posting your fstab like bohboh suggests is a good idea) ... if you're using gnome and want to use a program as 'root' you can type **gksudo <program_name>** to use it (for example **gksudo gedit** ...

---

### Post by roncg41677 on 2006-07-12
Sorry about the delay in replying. I wasn't at work, which is where this computer is.

I can't find etc/fstab. I'm viewing hidden files, and in Nautilus under "File System" I go to the "etc" folder, and there is nothing called "fstab". ??:???:

---

### Post by bohboh on 2006-07-12
Do this:

1. Open a terminal "Alt - F2"
2. sudo gedit /etc/fstab
3. Copy and paste here

---

### Post by roncg41677 on 2006-07-12
Rock on! Thanks! Here it is:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda1       /media/hda1     ntfs    defaults        0       0
/dev/hda4       /media/hda4     vfat    defaults        0       0
/dev/hdb1       /media/hdb1     vfat    defaults        0       0
/dev/hda3       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

There is another hard drive, hence the hdb1. That's probably obvious, but just in case it isn't :)  .

---

### Post by bohboh on 2006-07-12
Yeah, your drives arent mounted for writing.
I could explain it but not as good as this guide:

[http://www.psychocats.net/ubuntu/mountwindows.php](http://www.psychocats.net/ubuntu/mountwindows.php)

---

### Post by roncg41677 on 2006-07-12
That did it! Thanks so much! BTW, where is the best place to get more in depth info on mounting drives for beginners?

---

### Post by bohboh on 2006-07-12
That site is all i have ever needed. For an explanation of fstab read this [http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

---


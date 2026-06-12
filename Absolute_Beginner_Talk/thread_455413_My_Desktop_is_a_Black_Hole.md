---
title: "My Desktop is a Black Hole"
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by mlhudson on 2007-05-26
Ok, so every time I reboot, my desktop image disappears AND nothing that I save to the desktop show up there. It all shows up fine in the desktop window in nautilus, but the files don't visually appear on the desktop. I can't even drag things there.

I don't recall changing any settings for my desktop. And, I don't have compiz/beryl or "Desktop Effects" running.

On a Mac I've heard people talk about "rebuilding a desktop" is that an option in ubuntu?

---

### Post by dbott67 on 2007-05-26
Can you post the output of:
```
ls -all ~/Desktop
```

Also, the wallpaper selection; what is the filename & path of the image used?

Thanks,
Dave

---

### Post by mlhudson on 2007-05-26
Here's the output:

```
matt@matt-laptop:~$ ls -all ~/Desktop
total 1200
drwxr-xr-x  2 matt matt   4096 2007-05-23 14:37 .
drwxr-xr-x 90 matt matt   4096 2007-05-26 14:49 ..
-rw-r--r--  1 matt matt   3895 2007-05-23 14:36 5-20.ods
-rw-r--r--  1 matt matt 117668 2007-05-20 14:49 BF Team Meeting 5.20.07.pdf
-rw-r--r--  1 matt matt  15335 2007-05-21 11:03 export.opml
-rw-r--r--  1 matt matt 619574 2007-05-21 15:23 First%20Marathon%2001.jpg
-rw-r--r--  1 matt matt  75066 2007-05-22 10:13 iTunes%20Podcast%20List.pdf
-rw-r--r--  1 matt matt  26624 2007-05-21 12:49 Librarian%20Assistants%20Analysis.doc
-rw-r--r--  1 matt matt  55858 2007-05-21 13:30 Librarian Assistants Analysis.pdf
-rw-r--r--  1 matt matt  69477 2007-05-20 15:42 Nahum.pdf
-rw-r--r--  1 matt matt  68943 2007-05-21 14:37 Previously Served NOMCOM.pdf
-rwx------  1 matt matt 126926 2006-02-27 15:30 ._VBS 07 Logo.eps
matt@matt-laptop:~$ 

```

Ok, & when I go to the "Desktop Background", oddly my image appeared without me selecting anything. It sort of "reappeared" when the Desktop Background program ran.

---

### Post by dbott67 on 2007-05-26
Everything looks okay permissions-wise.

Do you have a separate /home partition (i.e. does /home reside on another drive or partition)?

I had a strange issue similar to yours where certain items did not appear on my desktop.  I re-mounted my fstab and all was okay:

```
sudo mount -a
```

If that helps, can you post the output of:
```
dbott@feisty:~$ cat /etc/fstab
# /etc/fstab: static file system information.
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=7366345e-067b-44b6-ab33-c8af8c31ae86 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda2
UUID=d98db2a6-db44-4405-bbb1-4bb5f1cb8faa /home           ext3    defaults        0       2
# /dev/sda3
UUID=4c5a5618-2d15-441f-b847-3b1b0d796a82 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

//192.168.1.2/Music /home/dbott/music   smbfs  auto,credentials=/root/.credentials,uid=1000,umask=000,user   0 0
//192.168.1.2/Data /home/dbott/data   smbfs  auto,credentials=/root/.credentials,uid=1000,umask=000,user   0 0
//192.168.1.2/Archive /home/dbott/archive1 smbfs auto,credentials=/root/.credentials,uid=1000,umask=000,user 0 0

```

-Dave

---

### Post by mlhudson on 2007-05-26
Thanks for the tip. My /home is all in the standard place, no extra partitions.
I attempted
```
sudo mount -a
```
No luck.

Here's my fstab dir just for giggles, in case it helps.
```
matt@matt-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=1af1dfba-ea53-4799-8002-9b48718b4672 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=e42c8baf-6f91-4110-8faa-1a71fb6b6f84 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
matt@matt-laptop:~$ 

```

just fyi, we're in over my head. i thought fstab was a criminal offense.:D

---

### Post by dbott67 on 2007-05-26
Yep... everything is pretty normal.

Are you using Gnome or KDE?

If Gnome, you can also try this:
> **Steve.K said:**
> ... your gnome settings might have gotten borked. Enable view hidden files in nautilus and rename all of the following directories (add a '_backup' or something to them)

.gnome
.gconf
.gconfd
.gnome2
.gnome2_private

Then restart.

This will reset all of your gnome settings; [COLOR=Purple]<snip>.[/COLOR]

To restore them, if this doesn't work, simply rename them again and remove the _backup bit.

(someone will probably come along with a far far simpler solution, but this is what springs to mind for me anyway)

Hope this helps

After that, we may have to re-install Metacity.  About the only thing I can find is that someone else who had a similar problem re-installed 'Metacity' (which is the Window Manager for Gnome).

```
sudo apt-get remove --purge metacity && sudo apt-get install metacity
```
-Dave

---

### Post by mlhudson on 2007-05-29
Dave - 
That absoutely fixed it. From terminal I went "sudo nautilus", then went and typed "_backup" on each of those files. And then, presto! like linux magic my desktop was unfrazzled.

Thank you for your help. I NEVER would have figured that out without you.

Matt

---


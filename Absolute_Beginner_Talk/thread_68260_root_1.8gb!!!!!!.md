---
title: "/root/ 1.8gb!!!!!!"
date: 2005-09-22
forum: Absolute Beginner Talk
---

### Post by aran384 on 2005-09-22
i was looking around to see where i can access my 2nd hdd thats in the system and i noticed that /root is 1.8gb ...... is there a way i can lower this to say around 500 - 600megs ?

---

### Post by Wolki on 2005-09-22
[QUOTE=aran384]i was looking around to see where i can access my 2nd hdd thats in the system[/quote]

You need to mount it. If it's a windows hdd, look here: [https://wiki.ubuntu.com/AutomaticallyMountMSWindowsPartitions](https://wiki.ubuntu.com/AutomaticallyMountMSWindowsPartitions)

If it's a linux partition, tell us what kind of partition it is and where.

>  and i noticed that /root is 1.8gb ...... is there a way i can lower this to say around 500 - 600megs ?

you mean the /root/ dirctory? That's really large. What files are there?

---

### Post by aran384 on 2005-09-22
the /root/ only has i think 2 files i can see.....

---

### Post by Wolki on 2005-09-22
[QUOTE=aran384]the /root/ only has i think 2 files i can see.....[/QUOTE]

And what files are they? Are they both big, or is one 1,8 gb and the other empty? We need more details :)

---

### Post by aran384 on 2005-09-22
there just a few kb......

am not on this site on my ubuntu comp so wont have to keep switching on kvm...

just gotta install something and then will try sort this other problem...

---

### Post by Wolki on 2005-09-22
[QUOTE=aran384]there just a few kb......

am not on this site on my ubuntu comp so wont have to keep switching on kvm...

just gotta install something and then will try sort this other problem...[/QUOTE]

Try showing hidden files. a /root/ dir of 1,8 gig is very unusual.

---

### Post by aran384 on 2005-09-22
my 2nd hdd is on /dev/hdb

---

### Post by Wolki on 2005-09-22
[QUOTE=aran384]my 2nd hdd is on /dev/hdb[/QUOTE]

OK. Can you tell me the output of "sudo fdisk -l /dev/hdb"?

---

### Post by aran384 on 2005-09-23
Disk /dev/hdb: 3240 MB, 3240000000 bytes
255 heads, 63 sectors/track, 393 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1         373     2996091   83  Linux
/dev/hdb2             374         393      160650    5  Extended
/dev/hdb5             374         393      160618+  82  Linux swap / Solaris

---

### Post by az on 2005-09-23
How about
df -h

---

### Post by doclivingston on 2005-09-23
As others have said, having a 1.8Gb /root directory is odd. Can you tell us the output of "ls -al" while in /root?

---

### Post by John.Michael.Kane on 2005-09-23
My root dir show's 2 items, totalling 1.5 KB..  so it's odd that your's is pushing 2gigs. 
also here's what should be in the folder

files listed will show when you click on show all files
.aptitude
.gconf
.gconfd
.gnome2
.gnome2_private
.gstreamer-08
.synaptic
.bashrc
.esd_auth
.fonts.cache-1
.profile
.recently-used

these should be the only two files shown when you dont use show all files
dbootstrap_settings
install-report.template

hope this helps

---

### Post by Wolki on 2005-09-23
[QUOTE=aran384]Disk /dev/hdb: 3240 MB, 3240000000 bytes
255 heads, 63 sectors/track, 393 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1         373     2996091   83  Linux
/dev/hdb2             374         393      160650    5  Extended
/dev/hdb5             374         393      160618+  82  Linux swap / Solaris[/QUOTE]

OK, this is getting a little confusing.... This is the harddrive you want to access from linux, or the one containing the large /root/ directory?

---

### Post by aran384 on 2005-09-24
that is the hdd i want to access.... 

well i gess mount to a folder or summat....

this is the output of ls -al while in /root

root@aran002:~ # ls -al
total 96
drwxr-xr-x  13 root root  4096 2005-09-23 20:05 .
drwxr-xr-x  22 root root  4096 2005-09-19 14:59 ..
drwx------   2 root root  4096 2005-09-19 15:37 .aptitude
-rw-------   1 root root  1390 2005-09-23 16:28 .bash_history
-rw-r--r--   1 root root  1333 2004-09-21 17:49 .bashrc
drwxr-xr-x   2 root root  4096 2005-09-23 16:16 bin
-rw-r--r--   1 root root   172 2005-09-19 15:03 dbootstrap_settings
-rw-------   1 root root    16 2005-09-19 21:26 .esd_auth
-rw-r--r--   1 root root 10263 2005-09-22 19:22 .fonts.cache-1
drwx------   3 root root  4096 2005-09-23 16:44 .gconf
drwx------   2 root root  4096 2005-09-24 12:30 .gconfd
drwx------   3 root root  4096 2005-09-19 21:38 .gnome2
drwx------   2 root root  4096 2005-09-19 15:34 .gnome2_private
drwxr-xr-x   2 root root  4096 2005-09-19 15:34 .gstreamer-0.8
-rw-r--r--   1 root root  1336 2005-09-19 15:03 install-report.template
drwxr-xr-x   3 root root  4096 2005-09-23 20:05 .k3d
-rw-------   1 root root    39 2005-09-23 08:43 .nano_history
-rw-r--r--   1 root root   141 2004-11-17 00:07 .profile
-rw-------   1 root root   865 2005-09-22 20:13 .recently-used
drwx------   3 root root  4096 2005-09-24 12:26 .synaptic
drwxr-xr-x   4 root root  4096 2005-09-23 16:20 .wine
drwxr-xr-x   4 root root  4096 2005-09-23 16:16 .winetools
root@aran002:~ #

---

### Post by aran384 on 2005-09-24
this is bit werid cause i just completely removed everything to do with wine and its all still there like in the ls -al i posted before....

---

### Post by aran384 on 2005-09-24
[QUOTE=azz]How about
df -h[/QUOTE]
Here is the output of df -h

root@aran002:~ # df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1             3.8G  2.6G  1.1G  72% /
tmpfs                 253M     0  253M   0% /dev/shm
/dev                  3.8G  2.6G  1.1G  72% /.dev
none                  5.0M  2.8M  2.3M  56% /dev
/dev/hdc              587M  587M     0 100% /media/cdrom0
root@aran002:~ #

---

### Post by doclivingston on 2005-09-24
[QUOTE=aran384]this is the output of ls -al while in /root
<snip output of ls -al>[/QUOTE]

According to that, the largest file in /root is only a few kilobytes, so it doesn't look like you /root directory is 1.8Gb

---

### Post by Wolki on 2005-09-24
[QUOTE=aran384]that is the hdd i want to access.... 

well i gess mount to a folder or summat....
[/QUOTE]

OK, create a folder where you want to mount that drive - I suggest somewhere in /mnt/ or /media/. THen, find out what kind of file system you have on that partition (most likely ext3, but ext2 and reiser3 are sometimes used, too). Then add the following line to your /etc/fstab ("sudo gedit /etc/fstab"):

```
/dev/hdb1  /mnt/<foldername> ext3 defaults 0 0
```

Replace /mnt/<foldername> and ext3 as described above.

then. "sudo mount -a" and it should work.

It that's too complicated for you, breezy will have a graphical tool to mount hdds.

---

### Post by aran384 on 2005-09-24
wtf is when i first started typing then it was in some werid language.....

well anyways how can i add a link to that folder ... in /home/aran and on my desktop....

---

### Post by aran384 on 2005-09-24
how do i find file type again ?

also is 1588 files in /.dev right ?

---


---
title: "HDDs being mounted in both /mnt and /media...why?"
date: 2007-09-04
forum: Absolute Beginner Talk
---

### Post by toddtemaat on 2007-09-04
Even though I mount the Backups and NAS partitions below  through fstab to be mounted in /mnt, once I am in Nautilus, they show up in bot /mnt and /media.  Why?  Any help to fix this would be appreciated.

Current fstab
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0

#boot
/dev/evms/boot	/boot		ext2	defaults,errors=remount-ro	0	1

#root
/dev/evms/ubuntu /		ext3	defaults 	0       1

#swap
/dev/evms/swap	none		swap	sw		0	0

#var
/dev/evms/var	/var		ext3	defaults	0	2

#CD-ROM
/dev/cdrom      /media/cdrom    udf,iso9660 	user,noauto	0       0

#Floppy
/dev/fd0	/media/floppy  	auto   		rw,user,noauto 	0       0

#NAS
/dev/evms/NAS		/mnt/NAS	ext3	rw,user,auto	0	1

#Backups
/dev/evms/Backups	/mnt/Backups	ext3	rw,user,auto	0	0

#home
/dev/evms/home		/home		ext3	defaults	0	1

Output of mount
> /dev/evms/ubuntu on / type ext3 (rw)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
/dev/evms/boot on /boot type ext2 (rw,errors=remount-ro)
/dev/evms/var on /var type ext3 (rw)
/dev/evms/NAS on /mnt/NAS type ext3 (rw,noexec,nosuid,nodev)
/dev/evms/Backups on /mnt/Backups type ext3 (rw,noexec,nosuid,nodev)
/dev/evms/home on /home type ext3 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)

Please let me know if there is anything else you might need.

Thanks,
Todd

---

### Post by vanadium on 2007-09-04
Nothing in your output suggests that they would be mounted in /media as well. In fact, I don't think you could mount the same partition twice. The only mechanism I can think of that would allow you to access the drives from /media as well is that there are symbolic links there pointing to the drives. You might want to post the output of 

ls -l /media /mnt

here.

---

### Post by toddtemaat on 2007-09-04
Thanks for the reply.  As requested, here is the output from ls -l /media /mnt

> total 16
drwxrwx--- 10 todd admin 4096 2007-07-25 00:48 backups
lrwxrwxrwx  1 root root     6 2007-04-14 22:30 cdrom -> cdrom0
drwxr-xr-x  2 root root  4096 2007-04-14 22:30 cdrom0
lrwxrwxrwx  1 root root     7 2007-04-14 22:30 floppy -> floppy0
drwxr-xr-x  2 root root  4096 2007-04-14 22:30 floppy0
drwxrwx--- 10 todd users 4096 2007-08-07 07:40 NAS

/mnt:
total 8
drwxrwx--- 10 todd admin 4096 2007-07-25 00:48 Backups
drwxrwx--- 10 todd users 4096 2007-08-07 07:40 NAS


---

### Post by bashologist on 2007-09-04
Well, it's not a symbolic link. Maybe a hard link? Hard links shouldn't be anything to worry about. You're not worried are you?!

---

### Post by toddtemaat on 2007-09-04
I would like to have them only show up in /mnt rather than in both places.  It's no big deal, really, just a nuisance.  Is there a way to find out if they're hard links and remove them?

---

### Post by kerry_s on 2007-09-04
just go into /media and delete those folders.

---

### Post by bashologist on 2007-09-04
If you're interested you could read about hard links; they're very interesting things. [http://www.askdavetaylor.com/how_do_unix_linux_hard_links_work.html](http://www.askdavetaylor.com/how_do_unix_linux_hard_links_work.html)

I don't know about deletion, I don't suggest playing with it. Figure out how you got it maybe? Deletion not a good idea.

It should just unlink, but why play with it? It's not hurting anyone!

---

### Post by nonewmsgs on 2007-09-04
/mnt is where temporary drives are
/media is where permanent drives are

i thienk they do an automatic 
mount /dev/hda /media/hda
thing

(im new too, but i always use the /media ones

---

### Post by bigboy_pdb on 2007-09-05
> **nonewmsgs said:**
> 
/mnt is where temporary drives are
/media is where permanent drives are


Then "mnt" folder is for mounted file systems. If I remember correctly, the media folder didn't always exist. The following source also indicates that this is true:
[http://www.oreilly.com/catalog/debian/chapter/book/appa_01.html](http://www.oreilly.com/catalog/debian/chapter/book/appa_01.html)

It doesn't make sense that they would be hard links since no user can create hard links to a folder (including root). To test this you can use the commands "mkdir test" and "ln test test2" both as a regular user and root. You'll find that they don't work.

On the other hand, both "NAS" and "backups" folders have the same number of hard links when you listed them using "ls -l" so this is an indication that one set of folders might be hard links.

To check if they are hard links you can use the information from the following site:
[http://osr507doc.sco.com/en/OSUserG/_whether_file_has_links.html](http://osr507doc.sco.com/en/OSUserG/_whether_file_has_links.html)

If you want an explanation of the commands from the link above, ask me for one and I'll explain them to you.

---

### Post by vanadium on 2007-09-05
bigboy_pdb, from what I learned from your post, we might learn whether they have the same inode by the command

ls -i /mnt /mount

I am testing with my USB and it is in fact possible to mount a drive twice under Linux. Then in this case one of the mounts would be performed during bootup (/etc/fstab), the other would be done through the automatic mounting mechanisms. What kind of a drive is this these partitions are on, in other words, why would your device trigger an automatic mount? What is your version of Ubuntu?

---


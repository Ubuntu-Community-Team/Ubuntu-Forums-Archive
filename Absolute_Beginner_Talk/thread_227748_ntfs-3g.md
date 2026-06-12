---
title: "ntfs-3g"
date: 2006-08-02
forum: Absolute Beginner Talk
---

### Post by benner on 2006-08-02
i was able to follow the instructions from: [http://www.ubuntuforums.org/showthread.php?t=217009](http://www.ubuntuforums.org/showthread.php?t=217009)
to install ntfs-3g to allow ntfs read and write support.
when i tried to mount the drives, i got the following error message:

[mntent]: warning: no final newline at the end of /etc/fstab
mount: according to mtab, /dev/fuse is already mounted on /media/windowsC
mount failed
Please check that the device is plugged correctly.

this morning, i was able to mount the drive with only read support, so i know that it works.  here are the contents of fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda6       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda7       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda1 /media/windowsC ntfs-3g silent,umask=0,locale=en_US.utf8 0 0
/dev/hda5 /media/windowsE ntfs-3g silent,umask=0,locale=en_US.utf8 0 0

is there something missing?  any suggestions?

-benner

---

### Post by cantormath on 2006-08-02
I think you have to mount it in /dev/

like 
/dev/sda1
or
/dev/hda2

etc.

I believe /media is just a mount point directory, were you can open mounted images and see what is mounted.
what are you trying to mount.

---

### Post by benner on 2006-08-02
hda1 is my windows xp (ntfs) C: drive and i am trying to mount it to a folder called windowsC that I created in my media folder.  hda5 is another ntfs partition that i am trying to mount using 'ntfs-3g'.  when the instructions asked me to insert a 'mount point' into the command line, this is what i put in.  mistake?  I am running kubuntu and all of this is on one physical drive in a p4 notebook.  there are 4 partitions.  hda1 is windows C, hda5 is windows E, hda6 is kubuntu and hda7 is the kubuntu swap.

-benner

---

### Post by RRS on 2006-08-02
The problem is in trying to use ntfs-3g to mount two partitions at a time.

For a partial explanation se the last page in this thread;
[http://www.ubuntuforums.org/showthread.php?t=217009&page=23]("http://www.ubuntuforums.org/showthread.php?t=217009&page=23")

---

### Post by givré on 2006-08-02
@cantormath: definitly not, you miss of mount point in linux and unix in general.
/dev/hd* or /dev/sd* are device block. They are the link between the hardware and the system (if you look at /dev, you will see /dev/ram* /dev/lp0...)
But to browse them, you have to mount it on a mount point of your filesystem.  /dev /sys and /proc are virtual system directory that are create at each boot so you can't mount them here. But except that, you can mount a partition wher you want.
If we mount windows partition on /media, it's just because in that way, gnome will show them on the desktop (except that you will be able to see only one mounted with fuse, see the common problem at the end of the HowTo) bu you can also mount it on /home/<your username>/windows or whatever.

---

### Post by benner on 2006-08-02
i seem to be able to access the drives now.  in konqueror (storage media) they appear unounted but when i go to the media folder in the linux partition, the folders that i created have everything there.  thanks folks.

-benner

---

### Post by givré on 2006-08-02
It's not really that they appear unmounted. it's just that kde/gnome are confuse by the two partition mounted on the same device block : /dev/fuse. If you really want to know if a partition is mounted or not, more /etc/mtab is the way to go.

---

### Post by cantormath on 2006-08-02
> **givré said:**
> @cantormath: definitly not, you miss of mount point in linux and unix in general.
/dev/hd* or /dev/sd* are device block. They are the link between the hardware and the system (if you look at /dev, you will see /dev/ram* /dev/lp0...)
But to browse them, you have to mount it on a mount point of your filesystem.  /dev /sys and /proc are virtual system directory that are create at each boot so you can't mount them here. But except that, you can mount a partition wher you want.
If we mount windows partition on /media, it's just because in that way, gnome will show them on the desktop (except that you will be able to see only one mounted with fuse, see the common problem at the end of the HowTo) bu you can also mount it on /home/<your username>/windows or whatever.

I realize they are device blocks, maybe I should have been more clear in what I was suggesting.  Again, I was saying I think you need to write into fstab

/dev/(your partition like hda1 or sda1) /media/(mount point) ntfs-3g silent,umask=0,locale=en_US.utf8 0 0

Reading closer, I see that you posted your fstab and put that in there that way.

So.....sorry for not being clear there.

Now my next question would be, did you install fuse and add fuse to the bottom of the /etc/modules file?

if not, 
wget [http://flomertens.keo.in/debian/ntfs-3g/binary-i386/fuse-utils_2.5.3-1_i386.deb](http://flomertens.keo.in/debian/ntfs-3g/binary-i386/fuse-utils_2.5.3-1_i386.deb)
wget [http://flomertens.keo.in/debian/ntfs-3g/binary-i386/libfuse2_2.5.3-1_i386.deb](http://flomertens.keo.in/debian/ntfs-3g/binary-i386/libfuse2_2.5.3-1_i386.deb)
sudo dpkg -i libfuse2_2.5.3-1_i386.deb fuse-utils_2.5.3-1_i386.deb
then
sudo gedit /etc/modules
Add fuse to the bottom of the file.

Now you can either reboot and the drive will be mounted or you can try mounting it without rebooting by typing this command in the terminal:
ntfs-3g /dev/(your partition like hda1 or sda1) /mnt/(mount point)

Now your NTFS drive should be loaded and ready to read & write.

---

### Post by benner on 2006-08-02
i did install fuse.  at least i followed the instructions to do so and didn't get any obvious error messages or anything.  here are the contents of my modules file:

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
psmouse
sbp2
sr_mod
fuse

---


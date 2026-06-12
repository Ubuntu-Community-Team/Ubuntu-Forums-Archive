---
title: "Reading a DVD"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by RedStone on 2007-06-28
Can read a zip file on a dvd. 

I get a pop up window.
My Disc -KDE Daemon
A new medium hs been detected. What do you want to do? Medium type: unmounted DVD
Currently there are 2 options. Either open new window or Do Nothing.

I was able to play music cd with Amorak.

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=88758808-3d3e-4ac5-985a-ce9e752beb3f /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=20244876-64fb-4b49-a353-c07e29930e33 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by Pragmatist on 2007-06-28
What is your question?

---

### Post by RedStone on 2007-06-28
Sorry cant read dvd's.

---

### Post by Pragmatist on 2007-06-28
Does the disk mount?  Put in a DVD and then type this to see:
```
mount
```

What is the Make and Model of your DVD drive?

---

### Post by RedStone on 2007-06-28
scobbrt@scobba-laptop:~$ mount
/dev/hda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
procbususb on /proc/bus/usb type usbfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.20-16-generic/volatile type tmpfs (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)

The make and model is Toshiba DVD-ROM SD-R2312

---

### Post by Pragmatist on 2007-06-28
You typed "mount" after you inserted a dvd?
What type of DVD?  DvD-R? DVD-RW?  Something else?
What is on the DVD?  Is it blank?  Is it a film?  Is it a data disc?

---

### Post by euler_fan on 2007-06-28
If you are trying to play a movie, I would suggest going [here]("http://www.videolan.org/vlc/download-ubuntu.html") and installing VLC media player. Then go through it to open you movie.

If that's not what you're trying to do, then you'll have to post more information as the last poster suggests.

EDIT: I see now it appears from your first post to be a data disk. Did you try opening a new window? I'm a GNOME guy myself, but it seems like from what you posted that KDE recognized the disk and was asking if it should let you see what's on it or if it should just ignore it. I suggest popping the disk out and back in and letting it open in a new window. End EDIT.

---

### Post by RedStone on 2007-06-29
Prag

Mount after I inserted a dvd-rw that has a 3 gig zip file.

---

### Post by Pragmatist on 2007-06-29
What happens if you put in other types of DVDs?

---

### Post by RedStone on 2007-06-29
When I put a movie dvd it reads it and ask what player to use.

---

### Post by Pragmatist on 2007-06-29
> **RedStone said:**
> When I put a movie dvd it reads it and ask what player to use.
Ok, so your computer reads DVDs. Problem solved! :)

What happens if you insert a blank DVD-RW?
What happens if you insert a DVD-RW with normal small files (i.e. not a zip file, and no files larger than a few MB)?

---

### Post by RedStone on 2007-06-29
will try tonight, but  I was able to mount manually with sudo mount /dev/cdrom /media/cdrom
and use xarchive to see the zip file. I cant extract one file which happens to be 3 gigs the rest I can. Note: When I try to eject the dvd it give: error-kio_media_mounthelper

Unfortunately, the devise system:/ media/hdc (/dev/hdc) named 'my disc' and currently mounted at /media/cdrom0 could not be unmounted. the folloeing error was returned by unmounted command:

umount: only root can unmount /dev/hdc form /media/cdrom0

---

### Post by Pragmatist on 2007-06-29
> **RedStone said:**
> umount: only root can unmount /dev/hdc form /media/cdrom0

You need to run the umount command with sudo:
```
sudo umount /media/cdrom0
```

---


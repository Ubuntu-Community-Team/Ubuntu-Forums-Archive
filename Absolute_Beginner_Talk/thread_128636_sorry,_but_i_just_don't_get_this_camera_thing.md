---
title: "sorry, but i just don't get this camera thing"
date: 2006-02-11
forum: Absolute Beginner Talk
---

### Post by fuscia on 2006-02-11
if i use nautilus, i can click on 'computer' and get pics of my camera. for some odd reason, i can't find anything remotely close to 'computer' on rox-filer. nautilus is to big for me to be loading as pics as i do. i don't get mounting and none of the camera apps work for me.

---

### Post by codejunkie on 2006-02-11
[QUOTE=fuscia]if i use nautilus, i can click on 'computer' and get pics of my camera. for some odd reason, i can't find anything remotely close to 'computer' on rox-filer. nautilus is to big for me to be loading as pics as i do. i don't get mounting and none of the camera apps work for me.[/QUOTE]
you can run "nautilus" and "gnome-volume-manager" in xfce and get the same functions you would have using gnome and xfce still seems just as fast.

---

### Post by fuscia on 2006-02-11
[QUOTE=codejunkie]you can run "nautilus" and "gnome-volume-manager" in xfce and get the same functions you would have using gnome and xfce still seems just as fast.[/QUOTE]

i've gotten rid of both gnome and xfce (too slow on my old fart machine, and besides, i like spartan) and this is the only issue that's keeping me from getting rid of nautilus.

---

### Post by codejunkie on 2006-02-11
[QUOTE=fuscia]i've gotten rid of both gnome and xfce (too slow on my old fart machine, and besides, i like spartan) and this is the only issue that's keeping me from getting rid of nautilus.[/QUOTE]
i hear that speed is the main thing to shoot for on older hardware, i don't know if it has what your looking for but have you tried xfe it's a pretty lightweight file manager and it's a little nicer than rox.

---

### Post by fuscia on 2006-02-11
thanks for the suggestion. i just tried it and i still can't find my camera.

---

### Post by xmastree on 2006-02-11
presumably you usually plug the camera into a USB port? where is it mounted?
If I plug mine in (well, if I plug the card intot he card reader. Same effect) and run 'mount' I see this at the end:
```
/dev/sdb1 on /media/NIKON D70 type vfat (rw,nosuid,nodev,sync,noatime,quiet,uid=1000,gid=1000,umask=077,iocharset=utf8)

```
Armed with the knowledge that it's mounted at /media/NIKON D70 I can navigate to that using a terminal. would that help?

---

### Post by cwaldbieser on 2006-02-12
[QUOTE=fuscia]thanks for the suggestion. i just tried it and i still can't find my camera.[/QUOTE]
Well, there a couple things you can try:
If your camera is detected by gphoto2, you could try installing and using that package:
```

$ ghpoto2 --list-cameras
$ gphoto2 --auto-detect

```

If your camera is a USB mass storage device (many digi-cams are these days), you can try looking at the output of dmesg after you plug in the camera.  It should create a device file (like for a pen-drive aka flash drive).  It is usually something like /dev/sda1 or /dev/sdb1 (it varies depending on what other SCSI hardware drivers are installed and active).

Once you figure out the device, you can mount it in the usual fashion.  E.g.
```

$ pmount /dev/sdb1
or
$ mkdir ~/camera
$ mount /dev/sdb1 ~/camera

```
When you are finished, you can unmount it with pumount or umount.

If you can get it working from the command line, it is not usually much more effort to set up some launchers, shortcuts, etc.

---

### Post by fuscia on 2006-02-12
thanks for the responses, guys. 'mounting' is totally foreign to me. i don't even know what it means or what it does. when using gnome, or kde, my camera would just magically appear on the desktop, even using the live cd.

so i just tried *mkdir ~/camera*, followed by *sudo mount /dev/sdb1 ~camera* and got *"you must specify the filesystem type"*. at that point, i had to stop posing as someone who knew what he was doing.

before this thread, i'd tried a whole pile of things (gphoto2, mvmount, pmount, something else mount, cam this and kam that, etc.) and either couldn't figure out how to use them, or my camera wasn't recognized (one of them lists coolpix5400 and 5700, but not 5600. doh!).

---

### Post by xmastree on 2006-02-12
so, you do this:
sudo mount /dev/sda1 ~/camera -t vfat -o mask=000
and see if that works. If it does, you make a simple script to do it next time.

---

### Post by kombipom on 2006-02-12
I'm certainly no guru but as far as I understand 'mounting' is just attaching a peice of hardware (well the file in /dev which represents that hardware) to a directory.

From the man page for mount (type "man mount" in a terminal):
>        All files accessible in a Unix system are arranged in one big tree, the
       file hierarchy, rooted at /.  These files can be spread out  over  sev&#8208;
       eral  devices. The mount command serves to attach the file system found
       on some device to the big file tree. Conversely, the umount(8)  command
       will detach it again.

In order for the system to be able to communicate with the hardware it has to know what type of file system it has (CD or Win XP or whatever) the "-t vfat" bit of the command tells mount that the camera has a windows (pre-XP) style file system.  I think that this is the filesystem used on all digicams and flash drives but don't quote me on that.

I hope that that helps in some small way.

---

### Post by fuscia on 2006-02-12
~$ sudo mount /dev/sda1 ~/camera -t vfat -o mask=000

mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

~$ dmesg | tail
[4296029.269000] sda: Write Protect is off
[4296029.269000] sda: Mode Sense: 18 00 00 08
[4296029.269000] sda: assuming drive cache: write through
[4296029.287000] SCSI device sda: 990976 512-byte hdwr sectors (507 MB)
[4296029.290000] sda: Write Protect is off
[4296029.290000] sda: Mode Sense: 18 00 00 08
[4296029.290000] sda: assuming drive cache: write through
[4296029.290000]  /dev/scsi/host0/bus0/target0/lun0: p1
[4296029.306000] Attached scsi removable disk sda at scsi0, channel 0, id 0, lun 0
[4296086.338000] FAT: Unrecognized mount option "mask=000" or missing value


i did this with my camera plugged in and turned on, if that matters. (this would be a good time to bring out the linuxdeer...)

[IMG]http://img.photobucket.com/albums/v342/unknownentity/linuxdeer2.jpg[/IMG]

---

### Post by cwaldbieser on 2006-02-12
[QUOTE=fuscia]~$ sudo mount /dev/sda1 ~/camera -t vfat -o mask=000

mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

~$ dmesg | tail
[4296029.269000] sda: Write Protect is off
[4296029.269000] sda: Mode Sense: 18 00 00 08
[4296029.269000] sda: assuming drive cache: write through
[4296029.287000] SCSI device sda: 990976 512-byte hdwr sectors (507 MB)
[4296029.290000] sda: Write Protect is off
[4296029.290000] sda: Mode Sense: 18 00 00 08
[4296029.290000] sda: assuming drive cache: write through
[4296029.290000]  /dev/scsi/host0/bus0/target0/lun0: p1
[4296029.306000] Attached scsi removable disk sda at scsi0, channel 0, id 0, lun 0
[4296086.338000] FAT: Unrecognized mount option "mask=000" or missing value


i did this with my camera plugged in and turned on, if that matters. (this would be a good time to bring out the linuxdeer...)

[IMG]http://img.photobucket.com/albums/v342/unknownentity/linuxdeer2.jpg[/IMG][/QUOTE]
I think the option should be:
```

$ sudo mount /dev/sda1 ~/camera -t vfat -o **umask**=000

```

---

### Post by fuscia on 2006-02-12
[QUOTE=cwaldbieser]I think the option should be:
```

$ sudo mount /dev/sda1 ~/camera -t vfat -o **umask**=000

```[/QUOTE]

 that worked, except the last thing should be 3 zeroes, not 3 Os. awesome! thank you, very much.

edit: oh damn! now, how do i unmount it?

---

### Post by cwaldbieser on 2006-02-12
[QUOTE=fuscia]that worked, except the last thing should be 3 zeroes, not 3 Os. awesome! thank you, very much.

edit: oh damn! now, how do i unmount it?[/QUOTE]
Use the "umount" command.  You can pass it either the directory or the device.  Make sure you are not in the directory first.  E.g.
```

$ sudo umount ~/camera
or
$ sudo umount /dev/sda1

```

BTW, did you want to set up some sort of shortcuts, or do you think you will just run the commands from the terminal?

---

### Post by fuscia on 2006-02-12
[QUOTE=cwaldbieser]Use the "umount" command.  You can pass it either the directory or the device.  Make sure you are not in the directory first.  E.g.
```

$ sudo umount ~/camera
or
$ sudo umount /dev/sda1

```

BTW, did you want to set up some sort of shortcuts, or do you think you will just run the commands from the terminal?[/QUOTE]

oh god, i'm not up to shortcuts yet. i'll just run them from the terminal. thanks very much for your help, btw. i've been banging my head on this one for a while.

---

### Post by xmastree on 2006-02-12
[QUOTE=fuscia]that worked, except the last thing should be 3 zeroes, not 3 Os. awesome! thank you, very much.[/QUOTE]
erm... sorry about that, my mistake. And yeah, it's umask, not mask.. ](*,)

---

### Post by fuscia on 2006-02-13
[QUOTE=xmastree]erm... sorry about that, my mistake. And yeah, it's umask, not mask.. ](*,)[/QUOTE]

no problem. i'm a firm believer in 'close enough'. your effort is appreciated.

---


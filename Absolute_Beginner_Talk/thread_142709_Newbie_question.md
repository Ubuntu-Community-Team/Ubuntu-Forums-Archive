---
title: "Newbie question"
date: 2006-03-11
forum: Absolute Beginner Talk
---

### Post by don cole on 2006-03-11
What does mount mean.

Don Cole

---

### Post by amohanty on 2006-03-11
[http://www.tldp.org/linuxfocus/English/September2004/article349.shtml](http://www.tldp.org/linuxfocus/English/September2004/article349.shtml)

---

### Post by gruepig on 2006-03-11
Mounting is what you do to a file system (which you would have on a hard drive partition, CD, USB stick, etc) to make it accessible so you can use it.

Most likely you don't need to worry about mounts, as the default config is probably fine and automount will take care of most mounting for you.  (So if you pop a CD into your computer it gets mounted automatically.)

More info anyway ....

In Linux/Unix, you have a directory tree which starts with the root-level /.  Under / are a bunch of directories, which in turn have subdirectories, ..., and so on down to files.  In order to access files, they must be mounted somewhere under /.  By convention, removal media is often mounted under /mnt or /cdrom.

You can see what is currently mounted on your system by typing "mount" at a command prompt.  You'll see "<device> on <mountpoint> type <filesystem> (<options>)".  You should have something mounted on /, special mounts for proc, tmpfs, etc (used internally), and maybe some other partitions if you have multiple partitions, removable media, or use nfs.  What gets mounted at boot is defined in the config file /etc/fstab.  You can also mount things manually.  As an example, to mount an ext3 filesystem on the third partition of your disk to /mnt, you might run "sudo mount -t ext3 /dev/hda3 /mnt".  To unmount, use the umount (not unmount) command.  

For more information about mount, see the mount manpage: "man mount".  In general, you can find lots of information in the manpages.  (If you're not sure the name of a manpage you can also do "man -k <string>" or "apropos <string"> to search for a particular string.)

---

### Post by takayuki on 2006-03-11
thanks amohanty and gruepig for the good info.

how do i unmount an sd memory card from a usb card reader?  i guess i don't just pull it out of the reader...

takayuki

---

### Post by taurus on 2006-03-11
Assuming it is mounted as /dev/sda1, then

```

sudo umount /dev/sda1

```

If you are not sure the name of the device, this command would tell you everything that currently has been mounted on your system...

```

df 

```

---

### Post by Klaidas on 2006-03-11
Here's a quinck tutorial about mounting: 
[http://www.linux.org/lessons/beginner/l13/lesson13d.html](http://www.linux.org/lessons/beginner/l13/lesson13d.html)

Anyway, in Ubuntu most of things are automounted :)

---

### Post by pdaoust on 2006-04-15
The easiest way to unmount a CD or plug-in USB drive safely is to right-click on its icon on the desktop (assuming you're using Ubuntu proper and not Kubuntu or Xubuntu, which I have no experience with) and click 'Eject'. Generally, you can safely pull out the drive without unmounting it first, because Ubuntu doesn't, by default, do 'delayed writing', which means saving a file later while you're busy doing other stuff. But don't take that to the bank, because that may change (and it may already have changed).

---


---
title: "Mounting my Windows partition"
date: 2007-01-27
forum: Absolute Beginner Talk
---

### Post by Kenaf on 2007-01-27
Obviously since I am in this forum, I am a newbie to Linux and Ubuntu.  I know a bit about it, but I'm still confused on some things.  I was attempting to mount my Windows drive to Linux so I could access files, but I encountered a problem.

Here is what my Terminal says:

kevin@kevin-desktop:/mnt/windows$ sudo mount -t ntfs /dev/hda1 /mnt/windows
kevin@kevin-desktop:/mnt$ cd windows
bash: cd: windows: Permission denied

Any other time I had an error, I just threw "sudo" in front of it, but it didn't work in this case.

kevin@kevin-desktop:/mnt$ sudo cd windows
sudo: cd: command not found

Any help is appreciated.. the ultimate goal is to be able to run this Wine program to run some of my Windows applications.

---

### Post by oldmanstan on 2007-01-27
well... your windows drive should (should) automatically be available in the "places" menu in gnome.  however, that's not always the case, things go wrong.  go to your /mnt directory, type ```
ls -l
``` and paste the output here

i'm sort of confused, you were in the /mnt/windows directory when you ran mount right? but then you weren't when you tried to cd into it. what happened between?

---

### Post by taurus on 2007-01-27
```
cd ~
sudo umount /dev/hda1
sudo mount -t ntfs /dev/hda1 /mnt/windows -o nls=utf8,umask=0222
ls -la /mnt/windows
```

---

### Post by Kenaf on 2007-01-27
kevin@kevin-desktop:/mnt$ ls -l
total 8
dr-x------ 1 root root 8192 2007-01-26 20:01 windows

Yeah, with the whole being in the directory, I mounted it while in the directory.  typing ls returned nothing, and when I left the directory and tried to go back, it wouldn't let me in.

---

### Post by Kenaf on 2007-01-27
Wow, taurus, whatever the heck all that stuff just meant, I think it worked.  Thanks!

---

### Post by taurus on 2007-01-27
First command--change back to your $HOME directory, wherever you might have been before.

Second command--unmount your XP partition.

Third command--mount your XP partition with read permission for everybody.

Fourth command--see if you can read XP partition.

---

### Post by bootslap on 2007-02-13
Hi... When i tried to mount the windows partition I got the following error:

pradeep@pradeep-laptop:~$ cd ~
pradeep@pradeep-laptop:~$ sudo umount /dev/hda1
Password:
umount: /dev/hda1: not mounted
pradeep@pradeep-laptop:~$ sudo mount -t ntfs /dev/hda1 /mnt/windows -o nls=utf8,umask=0222
mount: mount point /mnt/windows does not exist
pradeep@pradeep-laptop:~$ ls -la /mnt/windows
ls: /mnt/windows: No such file or directory
pradeep@pradeep-laptop:~$

---


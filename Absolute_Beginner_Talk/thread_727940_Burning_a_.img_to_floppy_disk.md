---
title: "Burning a *.img to floppy disk"
date: 2008-03-18
forum: Absolute Beginner Talk
---

### Post by Ian-on-the-Trent on 2008-03-18
[I]Just to start with, I have referred to posts:
[http://ubuntuforums.org/showthread.php?t=452789](http://ubuntuforums.org/showthread.php?t=452789)
[http://ubuntuforums.org/showthread.php?t=477404](http://ubuntuforums.org/showthread.php?t=477404)

The other post I refer to: [http://ubuntuforums.org/showthread.php?p=4534764](http://ubuntuforums.org/showthread.php?p=4534764)[/I]
========================================================

I'm having problems getting my dual-boot XP/Ubuntu 7.10 to boot. In another post, I was told to boot up my computer with a Live CD (which I have done), download a copy of [SuperGrub]("http://sgd.benjamin-butschko.de/download/binaries/sgd/floppy/") (also done), and burn the *.img to a floppy.  Huh?

I've been trying but I can't seem to get it accomplished.  Thoughts and suggestions on this matter? I have tried this:

[FONT="Fixedsys"]ubuntu@ubuntu:~/Desktop$ sudo dd if=~/burn/super_grub_disk_english_floppy_0.9689.img of=/dev/fd0dd: opening `/home/ubuntu/burn/super_grub_disk_english_floppy_0.9689.img': No such file or directory
[/FONT]

---

### Post by Ian-on-the-Trent on 2008-03-18
Resolved.

These are the steps I used to burn an image to a floppy while using the Ubuntu 7.04 Live CD:

1. Open a terminal window.
2. Unmount floppy drive: 
[INDENT]*sudo umount /dev/fd0 *[/INDENT]
3. Change to the location of the needed image file (*.img):
[INDENT]*ubuntu@ubuntu:~$ cd Desktop*
*ubuntu@ubuntu:~/Desktop$ ls* (just to check that the file is there.)[/INDENT]
4. In the terminal enter:
[INDENT]*dd if=super_grub_disk_english_floppy_0.9689.img of=/dev/fd0 bs=1440k of=/media/fd0*[/INDENT]

The output should appear like:
[INDENT][I]1+0 records in
1+0 records out
1474560 bytes (1.5 MB) copied, 48.702 seconds, 30.3 kB/s
ubuntu@ubuntu:~/Desktop$ [/I][/INDENT]

And that's it.

---


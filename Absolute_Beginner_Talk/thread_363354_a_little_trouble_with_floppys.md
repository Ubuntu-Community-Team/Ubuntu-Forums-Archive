---
title: "a little trouble with floppys"
date: 2007-02-16
forum: Absolute Beginner Talk
---

### Post by Unlockitall on 2007-02-16
ok peeps, heres my problem, i have a copy of xubuntu, and when i got it, i had no idea why i couldnt get a floppy to mount. then i asked my computer teacher, and he told me that i had to edit fstab and put the location of fd0 there, so i did. now whenever i try 
> mount /media/floppy0
after something thats sounds like mounting (old pc), i get a response
> mount: must specify file system type
anyone know how to help?

---

### Post by Unlockitall on 2007-02-16
can anyone help me with my n00bish problem?

---

### Post by Unlockitall on 2007-02-16
can someone help me.....please:cry: 
aaaahhhhhhhhhhh!!!!!!!!!!!!!!!!!!!!!!!!!!](*,)

---

### Post by click4851 on 2007-02-16
I'll give it a shot but I'm probably just as newb as you. Lets eliminate the easy, has the disk been formatted? Then when I want to mount a floppy I seem to think it was:
 
 sudo mount /dev/fd0 /mnt/floppy

If I remember, when they started incorporating automount, mounting drives from the command line got a little weird.

---

### Post by Unlockitall on 2007-02-16
help........please.......

---

### Post by confused57 on 2007-02-16
Maybe this will help:
[http://www.alwanza.com/howto/linux/floppy.html](http://www.alwanza.com/howto/linux/floppy.html)

Here's my /etc/fstab entry:
```
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
```

---

### Post by dwblas on 2007-02-16
> mount: must specify file system type Either the floppy is not formatted for Linux, or it is a DOS disk.  Try "man fdformat" for formatting, or just "fdformat /dev/fd0".  Install MToolsFM for a DOS diskette.

---

### Post by Unlockitall on 2007-02-16
i think its formatted for windows, i have pengaol on there, thats what im trying to get on the pc

---

### Post by Unlockitall on 2007-02-16
ok i still get the 
mount: you must verify filesystem type
thing, but i also have a program on my windows machine that i need to get to the ubuntu machine

---

### Post by Unlockitall on 2007-02-16
i think i found the problem, i just need to know if anyone can tell me what kind of filesystem a floppy disk is

---

### Post by Quintin Riis on 2007-02-16
fdisk -l /dev/fd0 will tell you what the filesystem is.  Are you sure that the floppy is healthy?  They are incredibly unreliable.  The last time I needed one I went through 12 ( ! ) before I found one that I could write my disk image to without an I/O error.

Do you have another way of moving this file?  Network?  Flash media?  CD-R?

In the future, please do not bump posts repeatedly.  If someone can help you they will; be patient.  If you don't get an answer in perhaps a week, then you can consider bumping a post.

---

### Post by rccharles on 2007-02-16
> **Unlockitall said:**
> i think i found the problem, i just need to know if anyone can tell me what kind of filesystem a floppy disk is
The file types can be found in the write-up of the mount command.  See:

man mount
see the section on ...
    -t vfstype


vfat 
msdos
umsdos

See also:

[http://ubuntuforums.org/archive/index.php/t-3687.html](http://ubuntuforums.org/archive/index.php/t-3687.html)
[http://ubuntuforums.org/archive/index.php/t-24763.html%5B/t-78986.html](http://ubuntuforums.org/archive/index.php/t-24763.html%5B/t-78986.html)
  

One note, I was never able to get my floppy drive to work in 6.06.  It worked in Knoppix.

I am now using a USB flash drive.  They are cheap if you look for a sale.

Robert

---

### Post by rusty4r on 2007-02-17
my floppy drive does automount when I put in a good floppy.

I'm using edgy right now, next time I reboot I'll give it a try in dapper

---

### Post by Unlockitall on 2007-02-20
I figured it out! i just thought id post what i did in case anyone else has the same problem. i had to add /dev/fd0 to fstab across from floppy, and im not sure if that affects how i actually got it to work. i right clicked on the top toolbar and added the diskmounter

---

### Post by click4851 on 2007-02-20
there ya go man, a little floppy experience from time to time is a good thing.

---

### Post by dwblas on 2007-02-20
And in which way did you mean that?

---


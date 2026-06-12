---
title: "how do I save scripts to mount partitions on boot up?"
date: 2005-11-19
forum: Absolute Beginner Talk
---

### Post by zexoc on 2005-11-19
I have a fat32 partition that I would like to mount automatically when I boot up.

Following the Ubuntu guide I've made a fstab script and saved it on my desktop, how do I get Ubuntu to automatically execute it on start up?

Thanks for any replies.

---

### Post by jorn on 2005-11-19
Hallo!

I don't know if I am right, but have you tried this?
[http://www.ubuntuguide.org/#automountntfs](http://www.ubuntuguide.org/#automountntfs) 
and look how to mount fat32 on startup.

Jørn

---

### Post by gerbman on 2005-11-19
[QUOTE=zexoc]I have a fat32 partition that I would like to mount automatically when I boot up.

Following the Ubuntu guide I've made a fstab script and saved it on my desktop, how do I get Ubuntu to automatically execute it on start up?

Thanks for any replies.[/QUOTE]

Hi.  You already had an fstab on your system at /etc/fstab.  It might be easiest just to change that one.  All you should need to do is append a line like the following to the end of the file:```
/dev/hdb1       /mnt/hd2        vfat    defaults,uid=gerb       0       0
```Of course, you'll need to change this line to reflect your own system.  "/dev/hdb1" is the FAT32 partition I am mounting.  "/mnt/hd2" is where I am mounting it (mount point).  You can make yourself the owner of the files with the option "uid=<username>".  After you change the fstab file, you can mount the partition with the following command:```
sudo mount <mount point>
```Hope this helps!

---

### Post by zexoc on 2005-11-19
thanks for pointing to the faq Jorn, I followed the guide and on starting/bootup of Ubuntu, the checklist shows

mounting file systems   .........................................................................................                                                         [color=red]**failed**[/color]

but once running ubuntu, the partition is mounted and in the desktop.

Why the 'failed' error?

---

### Post by gerbman on 2005-11-19
[QUOTE=zexoc]thanks for pointing to the faq Jorn, I followed the guide and on starting/bootup of Ubuntu, the checklist shows

mounting file systems   .........................................................................................                                                         [color=red]**failed**[/color]

but once running ubuntu, the partition is mounted and in the desktop.

Why the 'failed' error?[/QUOTE]

What's your fstab look like?

---

### Post by zexoc on 2005-11-19
Like this

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdc3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdc6       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hdc5       /media/windows  vfat    iocharset=utf8,umask=000
0       0
```

---

### Post by gerbman on 2005-11-19
[QUOTE=zexoc]Like this

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdc3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdc6       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hdc5       /media/windows  vfat    iocharset=utf8,umask=000
0       0
```[/QUOTE]

Hmmm...looks okay to me.  Try remounting it from a terminal to check for error messages.  Unmount:```
sudo umount /media/windows
``` Mount:```
sudo mount /media/windows
```

If that works fine (and all you did was add that last line to your fstab) then I'm at a loss...sry

---

### Post by jorn on 2005-11-19
The two 0's at the end of the mounting path, are placed on a new line. I don't know if that can course tre error or if it is written correctly in your fstab.

Jørn

---

### Post by zexoc on 2005-11-19
It does work fine, the only thing is getting that failed message on startup

is there another file where boot sequence might be stored?

thanks anyways gerbman

---

### Post by gerbman on 2005-11-19
[QUOTE=jorn]The two 0's at the end of the mounting path, are placed on a new line. I don't know if that can course tre error or if it is written correctly in your fstab.

Jørn[/QUOTE]

I assumed that was the word-wrap...but good point.  They should definitely be on the same line.

---

### Post by zexoc on 2005-11-19
Jorn, I think thats the way its formatted in the text editor.

---

### Post by gerbman on 2005-11-19
[QUOTE=zexoc]It does work fine, the only thing is getting that failed message on startup

is there another file where boot sequence might be stored?

thanks anyways gerbman[/QUOTE]

As far as I know, that's it.  You might try different mounting options.  So instead of ```
iocharset=utf8,umask=000
``` you could do ```
defaults,uid=<your user name>
```If things work fine and you can live with the "failed" message then it'll probably be okay the way it is...but I wouldn't be able to live with it, heh ;-)

---

### Post by zexoc on 2005-11-19
check that, *it was because those 2 zeros where on a new line*. 

thanks very much for your help Jorn and gerbman!

---

### Post by gerbman on 2005-11-19
[QUOTE=zexoc]check that, *it was because those 2 zeros where on a new line*. 

thanks very much for your help Jorn and gerbman![/QUOTE]

No problem.  Glad to see you got it.

---


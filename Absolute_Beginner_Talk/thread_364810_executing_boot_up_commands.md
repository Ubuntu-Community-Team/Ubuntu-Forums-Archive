---
title: "executing boot up commands"
date: 2007-02-18
forum: Absolute Beginner Talk
---

### Post by MicheleZ on 2007-02-18
Hello,

I have installed ubuntu Edgy (on computer with windows), then windows again. 
I have now 6 partitions on my HD (don't be horrified... I know it is a mess):


[FONT="Courier New"]sda1  ntfs          (pure data)
sda2  extended
sda3  ext2          /home  
sda4  swap          linux swap
sda5  ntfs          windows
sda6  ext2          / (root)[/FONT]

Now my two problems (which should be related): 
a) before re-installing windows I could see sda1 and sda5, however now sda5 disappeared at start up and I have to manually mount it.

Brief explanation of the second issue
I want to have read+write access the first ntfs partition. At present after the system boots up I umount it (the mounting should be hidden somewhere in the start up procedures) then mount it using ntfs-3g.
Questions b) 
where is the start up script? 
can I write there commands as root?
is it the same file where sda1 gets mounted when the system starts up?

Apologies for the obvious questions. I searched the forum but did not have much luck.

Cheers,

Michele

---

### Post by po0f on 2007-02-18
MicheleZ,

I don't quite know what your problem is with your first question; can you not see the partition from Windows or Linux?

To answer your second one, you should be able to just put commands you want run at boot-up in /etc/rc.local.  For example, I have this in mine:
```
[FONT="Courier New"]#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

**/usr/local/sbin/g15daemon || exit 1**

exit 0[/FONT]
```

The bold part is my addition.  If a command fails, you should have it exit with non-zero status.  The way I have it set up usually works.

---

### Post by MicheleZ on 2007-02-19
Thanks po0f,

It works, I copied the following lines in the file and it did the trick:
```

umount /dev/sda1
mount -t ntfs-3g /dev/sda1 /mnt/driveC

```
I also get a link on my desktop!

However I would like to understnad a bit more why the link to sda1 (read only) was already on my desktop when I first started ubuntu. 

Question: Is there another startup file somewhere?

Apart from trying to understand how things work rather than copying and pasting instructions, if I can prevent sda1 to be mounted as read only I could avoid umounting it.

Also, what I get on the desktop is /mnt/driveC, but I would like to have a different name (such as drive C) is this possible?

Cheers,

Michele

---


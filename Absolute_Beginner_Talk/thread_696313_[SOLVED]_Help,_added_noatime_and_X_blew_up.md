---
title: "[SOLVED] Help, added noatime and X blew up"
date: 2008-02-13
forum: Absolute Beginner Talk
---

### Post by Mark_in_Hollywood on 2008-02-13
Following the article in Linux Format magazine (LXF98)

I added noatime,data=writeback

and now X won't start

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=4f75a181-c417-4e11-9073-6d27c34db623 /               ext3    defaults,noatime,data=writeback,errors=remount-ro 0       1

I'm running LiveCD, and I don't know how to get back into my harddrives /etc/fstab and unbreak the X

HELP!!!!

---

### Post by overdrank on 2008-02-13
> **Mark_in_Hollywood said:**
> Following the article in Linux Format magazine (LXF98)

I added noatime,data=writeback

and now X won't start

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=4f75a181-c417-4e11-9073-6d27c34db623 /               ext3    defaults,noatime,data=writeback,errors=remount-ro 0       1

I'm running LiveCD, and I don't know how to get back into my harddrives /etc/fstab and unbreak the X

HELP!!!!
Hi and could you not edit the kernel line from the grub. When the grub loads press esp and then e to edit the line.  Remove the noatime then hit enter and then  b to boot. This will hopefully continue to the GUI where you can edit the menu list.

---

### Post by emarkd on 2008-02-13
Those are IO settings, so I'm not sure what they'd have to do with X, but you can mount your root filesystem and edit the file:

1.  Make a directory

```
sudo mkdir /media/root
```

2.  Mount it

```
sudo mount -t ext3 /dev/whatever /media/root
```

Then edit your file and reboot.

---

### Post by Mark_in_Hollywood on 2008-02-13
> **overdrank said:**
> Hi and could you not edit the kernel line from the grub. When the grub loads press esp and then e to edit the line.  Remove the noatime then hit enter and then  b to boot. This will hopefully continue to the GUI where you can edit the menu list.

STRANGE, Grub's lines did not show the noatime,data=writeback

still won't boot, I'm in LiveCD

---

### Post by Mark_in_Hollywood on 2008-02-13
Is there no easy way to access the harddrive's /etc/fstab, change the line back from LiveCD?

Mounting per the 2nd responder leaves me confused as to what needs doing. He doesn't even say how to save that onto the harddrive, which as it isn't mounted (this is LiveCD) at the moment, I can't seem to write to, although I can read OK.

Thanks, #2, but I need another go at this.

---

### Post by emarkd on 2008-02-13
You can do all that from the Live CD.  Just give it a shot.  With your live CD booted, open a terminal and type those commands.  It'll work.

---

### Post by emarkd on 2008-02-13
I'm sorry if I was unclear.  I just reread your post and it seems you didn't understand me.  If you make a mountpoint (in the LiveCD environment) and mount your root partition (the real harddrive) to it, you can then just cd into /media/root/etc/ and edit your fstab file.  Remember that there's only one filesystem in Linux, whether they're on the same disk or not.

---

### Post by jordanmthomas on 2008-02-13
> **Mark_in_Hollywood said:**
> STRANGE, Grub's lines did not show the noatime,data=writeback


They shouldn't be on the grub line, but in your fstab, so don't worry.

---

### Post by Mark_in_Hollywood on 2008-02-13
Thanks, everyone.

From Places/Computer I mounted the disk. No Prob.

In LiveCD, I loaded a terminal. From it ran nano, removed the offending code and re-booted.

Things seem OK,

WHEW!

---

### Post by emarkd on 2008-02-13
Glad you got it worked out.

---


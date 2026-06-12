---
title: "Need help with grub"
date: 2006-12-05
forum: Absolute Beginner Talk
---

### Post by styfer on 2006-12-05
Hi can anyone tell me whats wrong with this grub config?
There are so many entries when i only have ubuntu/windows xp installed!

anyways whenever i choose ubuntu, why will i always boot to a terminal like prompt?
only when i type 'exit' in the prompt will my ubuntu continue to boot to GOME interface, why is this so?

and what do i do if i want my default choice become windows xp?
is there a GUI version of grub editor in ubuntu?

Heres part of my menu.lst file from grub

```

title		Ubuntu, kernel 2.6.15-27-amd64-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-27-amd64-generic root=/dev/sda3 ro quiet splash break=bottom
initrd		/boot/initrd.img-2.6.15-27-amd64-generic
savedefault
boot

title		Ubuntu, kernel 2.6.15-27-amd64-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-27-amd64-generic root=/dev/sda3 ro single
initrd		/boot/initrd.img-2.6.15-27-amd64-generic
boot

title		Ubuntu, kernel 2.6.15-23-amd64-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-23-amd64-generic root=/dev/sda3 ro quiet splash break=bottom
initrd		/boot/initrd.img-2.6.15-23-amd64-generic
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-amd64-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-23-amd64-generic root=/dev/sda3 ro single
initrd		/boot/initrd.img-2.6.15-23-amd64-generic
boot

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

---

### Post by pavel_kbc on 2006-12-05
```
title		Ubuntu, kernel 2.6.15-27-amd64-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-27-amd64-generic root=/dev/sda3 ro quiet splash break=bottom
initrd		/boot/initrd.img-2.6.15-27-amd64-generic
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-amd64-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-23-amd64-generic root=/dev/sda3 ro single
initrd		/boot/initrd.img-2.6.15-23-amd64-generic
boot

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```


have fun :D

---

### Post by bodhi.zazen on 2006-12-05
See this [Grub guide](http://users.bigpond.net.au/hermanzone/p15.htm)

As far as the number of entries, each time Ubuntu updates to a new kernel a new grub entry is added. You only need the latest, in your case **Ubuntu, kernel 2.6.15-27-amd64-generic**.

You can delete your old entries, in your case Ubuntu, kernel 2.6.15-23-amd64-generic.

You can remove the old kernels via synaptic.

IMO you can get rid of the line **savedefault**, that is up to you.

To change the default OS, there is a line
default 0

Change this to correspond to windows if you like. Note: grub counts starting with 0 so the first entry is 0.....

HTH

---

### Post by styfer on 2006-12-05
thanks but how am i suppose to edit it?
i try editing with the file editor but i cant save it??

---

### Post by yabbadabbadont on 2006-12-05
Make sure that you use "sudo" to run the editor command or you won't have permission to save your changes.

---

### Post by xyz on 2006-12-05
> **styfer said:**
> thanks but how am i suppose to edit it?
i try editing with the file editor but i cant save it??
You can open the file running:
```
sudo gedit /boot/grub/menu.lst

```
to be able to edit the file. Then click on "Save".
Simplest way. Good luck.

---

### Post by styfer on 2006-12-05
thanks all for the help!
will try it out now.. hehe..
yea was looking for this command 'gedit' hehe..

---

### Post by styfer on 2006-12-05
it seem that i am still experiencing problems booting to ubuntu
when i choose the first option "Ubuntu, kernel 2.6.15-27-amd64-generic"
i can see the splash boot screen but after like a few sec it will come to this prompt

```

/bin/sh:can't access tty; job control turned off
#
```

i can only continue booting after i type 'exit'
can anyone tell me what is happening?

here is my updated menu.lst

```

## ## End Default Options ##

title		Ubuntu, kernel 2.6.15-27-amd64-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-27-amd64-generic root=/dev/sda3 ro quiet splash break=bottom
initrd		/boot/initrd.img-2.6.15-27-amd64-generic
savedefault
boot

title		Ubuntu, kernel 2.6.15-27-amd64-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-27-amd64-generic root=/dev/sda3 ro single
initrd		/boot/initrd.img-2.6.15-27-amd64-generic
boot

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


```

---

### Post by styfer on 2006-12-05
anyone can help me with this?
i read the other similar forums and they are asked to change grub again..
but i think mine is pointing to the right partition rite?

---

### Post by bodhi.zazen on 2006-12-05
grub looks OK.

The problem is with your error message: 

> can't access tty; job control turned off

I do not know a solution, but this question has been in the forums.

Here is a listing:

[http://www.ubuntuforums.org/search.php?searchid=10708146](http://www.ubuntuforums.org/search.php?searchid=10708146)

I have not gone through the postings, perhaps there is a solution somewhere....

---


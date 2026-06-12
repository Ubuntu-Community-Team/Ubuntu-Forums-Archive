---
title: "[SOLVED] How to change OS order in Grub Loader?"
date: 2008-03-18
forum: Absolute Beginner Talk
---

### Post by udh on 2008-03-18
Hi all,
I have recently installed ubuntu. Before that I had XP. Now the MBR of XP is replaced by Grub loader which is fine with me as long as it allows me to switch between OS. 
But with Grub loader, it gives me lots of options to select.
I would like to know how can I change the order of these options so that I can have the most frequently used option as default choice.
Any help/link welcome, please keep in mind i'm 1 week familiar to ubuntu. :KS
thanks and regards,
Dh.

---

### Post by handydan918 on 2008-03-18
Easiest way to do this may be to post your /boot/grub/menu.lst and let us actually see it.Then someone can make the modification, and you don't end up with an unbootable system...

---

### Post by Hospadar on 2008-03-18
I'm pretty sure (make a backup first!) that you can just change the order that the entries appear in the /boot/grub/menu.lst file to get a different default boot order.

From gnome, Alt-F2->"gksu gedit /boot/grub/menu.list" and scroll aaaaall the way down to the bottom and find the boot entries, they will be distinct as they do _not_ start with '#' signs.  then cut and and paste.

NOTE: be suuure you have a good backup of this file, if you accidentally mess something up, you won't be able to boot without it.  It might be good to have a live cd on hand to to make changes if your system doesn't boot.

Also: mine looks like this, yours probably looks a lot alike, for simplicity I've ommitted all the comments from most of the file, this is just the last part which actually has the boot options, I've also added in a few comments for clarity.

```
## ## End Default Options ##
#Comments start with a pound sign

#this is one entry
title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=c2120c9b-38d3-4873-9b94-a35829fa51c9 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

#this is another
title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=c2120c9b-38d3-4873-9b94-a35829fa51c9 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

#this entry is a program to test your memory
title           Ubuntu 7.10, memtest86+
root            (hd0,2)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root

#this entry is for my windows installation
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1

```

So let's say I want to make windows first, I believe you can just copy the whole windows entry to the beginning of the list:

```
## ## End Default Options ##

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1


title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=c2120c9b-38d3-4873-9b94-a35829fa51c9 ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=c2120c9b-38d3-4873-9b94-a35829fa51c9 ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd0,2)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root

```

---

### Post by munkyeetr on 2008-03-18
Open /boot/grub/menu.lst
```

gksudo gedit /boot/grub/menu.lst

```

and at the bottom of the file you will see something like this:
```

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd1,2)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=3acd873f-1ab8-4f1a-8bbb-fb25e6f88a4e ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd1,2)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=3acd873f-1ab8-4f1a-8bbb-fb25e6f88a4e ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd1,2)
kernel          /boot/memtest86+.bin
quiet

```

Yours will be different if you dual boot. The order these are listed in this file are the order they appear in your boot menu. Move them how you want them, just keep the blocks (starting with title) together.

You can (and will probably want to) also change the option thats boots by default by going back near the top of the file and changing:

**default     0**

to

**default    *<whatever>***

! Just remember that the default variable counts from 0, so 0 boots the first option, 1 boots the seconds option, etc...

---

### Post by Duck2006 on 2008-03-18
In your menu.lst look for the line that looks like this

default         0

Count the number of entries to the one you want to be the default  and change the 0 to that number, the count start from 0 and not , so if i have 4 titles lines and i want the line four, i would use 3.

---

### Post by munkyeetr on 2008-03-18
> **Duck2006 said:**
> In your menu.lst look for the line that looks like this

default         0

Count the number of entries to the one you want to be the default  and change the 0 to that number, the count start from 0 and not , so if i have 4 titles lines and i want the line four, i would use 3.

Good call, he didn't care about changing the order, just the default boot option. I should have read it better.

---

### Post by udh on 2008-03-18
I found this on google::confused:
[https://answers.launchpad.net/ubuntu/+source/nautilus/+question/5048](https://answers.launchpad.net/ubuntu/+source/nautilus/+question/5048)

> You have to edit exactly /boot/grub/menu.lst as you said.

Find a line beginning with this:
timeout

The number after this command are the second grub will wait for, before starting the mains OS selected. Increase the number to have more time to choose.

Then, find the line beginning with:
default

The number after this is the default OS to launch. If Vista is the second OS in the list, then you should write 1. In any case, this number is the OS number in the list -1 (I mean, the fisrt is 0, the second is 1, and so on, as in an array :))

If you want to change the appearing order, at the end of the file there is something like:
title Ubuntu, kernel 2.6.17-11-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.17-11-generic root=/dev/hda1 ro quiet splash
initrd /boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

Changing the order of this set of text, will change the oreder of the boot options...

About the rebooting, its strange... Are you choosing reboot or end session? Since the second options, doesn't restarts the system... Grub shows up only when you completely restart your system...

To finish... I would suggest you to give up with Vista :)

Hope this helps,
Alessandro

---

### Post by udh on 2008-03-18
oops, thanks guys for quick replies, i would follow those instructions..:)

---

### Post by udh on 2008-03-18
> **munkyeetr said:**
> Open /boot/grub/menu.lst
```

gksudo gedit /boot/grub/menu.lst

```

and at the bottom of the file you will see something like this:
```

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd1,2)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=3acd873f-1ab8-4f1a-8bbb-fb25e6f88a4e ro quiet splash
initrd          /boot/initrd.img-2.6.22-14-generic
quiet

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root            (hd1,2)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=3acd873f-1ab8-4f1a-8bbb-fb25e6f88a4e ro single
initrd          /boot/initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, memtest86+
root            (hd1,2)
kernel          /boot/memtest86+.bin
quiet

```

Yours will be different if you dual boot. The order these are listed in this file are the order they appear in your boot menu. Move them how you want them, just keep the blocks (starting with title) together.

You can (and will probably want to) also change the option thats boots by default by going back near the top of the file and changing:

**default     0**

to

**default    *<whatever>***

! Just remember that the default variable counts from 0, so 0 boots the first option, 1 boots the seconds option, etc...

:guitar: worked! thanks a lot all :)

---


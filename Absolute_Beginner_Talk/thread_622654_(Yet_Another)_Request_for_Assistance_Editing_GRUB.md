---
title: "(Yet Another) Request for Assistance Editing GRUB"
date: 2007-11-25
forum: Absolute Beginner Talk
---

### Post by SBG on 2007-11-25
Hello all,

I'm not normally one to post asking for help with subjects that have been answered before, but this one is just too critical to the operation of the entire PC for me to futz around with.

The Setup:
 - A home-built PC with Ubuntu, Vista, and XP installed.  GRUB handles Linux and (I'd assume) NTLoader.  NTLoader offers up Vista and XP.

The Problem:
 - GRUB lists too many options.  I really only want the latest version of Ubuntu and its Recovery Mode and Vista listed as choices.  I'd like to add XP at this level if it's possible.
 - I want to make Vista the default OS.
 - I have no idea how to edit this file unless VI is an option. 
 - Also, given that nothing is likely to work if I hose GRUB, is there any way to recover without a reinstall?



Here's the output when GRUB is catted (is that a real word?):

## ## End Default Options ##

title           Ubuntu, kernel 2.6.20-16-generic
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=d469ee28-e7c3-40aa-b4f5-1dd5a1e090d5 ro quiet splash
initrd          /boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.20-16-generic root=UUID=d469ee28-e7c3-40aa-b4f5-1dd5a1e090d5 ro single
initrd          /boot/initrd.img-2.6.20-16-generic

title           Ubuntu, kernel 2.6.20-15-generic
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=d469ee28-e7c3-40aa-b4f5-1dd5a1e090d5 ro quiet splash
initrd          /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title           Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root            (hd0,2)
kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=d469ee28-e7c3-40aa-b4f5-1dd5a1e090d5 ro single
initrd          /boot/initrd.img-2.6.20-15-generic

title           Ubuntu, memtest86+
root            (hd0,2)
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title           Windows Vista/Longhorn (loader)
root            (hd0,0)
savedefault
makeactive
chainloader     +1





Thanks in advance,

Ben

---

### Post by rsambuca on 2007-11-25
You can't add XP to the grub menu since Vista's loader has taken over.  You are stuck going from grub to the Vista loader.

To make Vista the default, and not have to keep changing it in the future, move the Vista section above the line that says :```
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
```

Therefore it will look like this:
```


title Windows Vista/Longhorn (loader)
root (hd0,0)
savedefault
makeactive
chainloader +1
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
```

You edit your menu.lst using the text editor gedit.```
gksudo gedit /boot/grub/menu.lst
```

As for the old kernels, you can either comment them out (put a '#' number sign in front of them), delete the lines entirely (although they will reappear at the next kernel update), or use Synaptic Package Manager and uninstall them (look for 'linux-image')

---

### Post by SBG on 2007-11-25
Thanks, rsambuca!  I'll give it a shot tomorrow when I'm fresher.


Only one other question: 

Is there any safety net if I manage to mess up grub/menu.lst?  


Thanks again,

Ben

---

### Post by meierfra on 2007-11-25
> although they will reappear at the next kernel update),

Change 

#howmany=all" to "#howmany=1"  and they won't reappear.

---

### Post by meierfra on 2007-11-25
> Is there any safety net if I manage to mess up grub/menu.lst? 

Backup the file:

```
cd /boot/grub
sudo cp menu.lst menu.lst.backup
```

---

### Post by SBG on 2007-11-25
> **meierfra said:**
> Backup the file:

```
cd /boot/grub
sudo cp menu.lst menu.lst.backup
```



Good point, meierfra, but how would I rename the .backup?  Should I get a distro that can boot from cd or flash up and running first in case I need to take that step?

---

### Post by LaRoza on 2007-11-25
> **SBG said:**
> Good point, meierfra, but how would I rename the .backup?  Should I get a distro that can boot from cd or flash up and running first in case I need to take that step?

If you have the Ubuntu disk, you could use that. Also, don't change a working entry each time you edit it. So you always have something that works.

---

### Post by meierfra on 2007-11-25
(Edit: I was to slow but here is it anyway)

> Should I get a distro that can boot from cd or flash up and running first in case I need to take that step?

Three solutions:

1) The ubuntu LIve CD will allow  you to rename the file.

2)  if you select a title  at the grub-menu during boot up and press "e" (instead of "enter") you can edit "menu.lst"  (these changes are only temporarily, but will let you boot into ubuntu). 

3)   Get Supergrub: [Herman zone info]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html")

---


---
title: "How to make Windows default for GRUB?"
date: 2006-05-05
forum: Absolute Beginner Talk
---

### Post by 1002285 on 2006-05-05
How can I change, which OS Grub loads first and make Windows default, not Linux?

---

### Post by red_shrike on 2006-05-05
go to /boot/grub and open file called menu.lst Look around in the file (should be on the beginning somewhere) where it says 

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.           
default		2

Instead of 2 put whatever is good for you to start win automatically (probably 4)

---

### Post by red_shrike on 2006-05-05
Oh, yeah, you will need to start your text editor with root privileges. Why do you want win to start by default?

---

### Post by 1002285 on 2006-05-05
[QUOTE=red_shrike]go to /boot/grub and open file called menu.lst Look around in the file (should be on the beginning somewhere) where it says 

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.           
default		2

Instead of 2 put whatever is good for you to start win automatically (probably 4)[/QUOTE]

Sorry, I did not really understand what entry I have to change. Should I change number 0 after the word "default" to the number of Windows? I guess I should look up, what is the right number for windows then. The start of the file looks like this:
## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.           
default		0

And to answer the question in the last post,
I want Windows as the default because I do not use this computer as often as some other people who are just a little bit angry with me for messing around with Linux here. It would drive them nuts not to have the start button at the bottom left corner :). But I installed Ubuntu here for myself and for secure storage of important files on the secondary, smaller hard drive. Still, setting Windows as default would be polite towards them.

---

### Post by xyz on 2006-05-05
This is the way I did it to boot on Ubuntu:
```
sudo gedit /boot/grub/menu.lst

```

then find the line beginning with **title** and count "the titles" starting with **0.** When you get to windows, you'll have 'a number X' which you'll type next to 'default', for instance "default 4".
It's nice of you to install Ubuntu despite antagonism!Good luck.

---

### Post by 1002285 on 2006-05-05
[QUOTE=xyz]This is the way I did it to boot on Ubuntu:
```
sudo gedit /boot/grub/menu.lst

```

then find the line beginning with **title** and count "the titles" starting with **0.** When you get to windows, you'll have 'a number X' which you'll type next to 'default', for instance "default 4".
It's nice of you to install Ubuntu despite antagonism!Good luck.[/QUOTE]

Thank you,
but I will ask once more just tobe sure, because I'm afraid this will be afraid if not done right.
I don't see numbers next to titles. But there are
"
ubuntu kernel ...-10-386
ubuntu kernel ...-10-386 (recovery mode)
ubuntu kernel ...-9-386
ubuntu kernel ...-9-386 (recovery mode)
ubuntu memtest 86+
Microsoft Windows XP
"
does this mean that XP is number 5?

---

### Post by digen on 2006-05-05
Yes thats correct.Just to be sure you could paste the latter part of menu.lst file here in case to avoid any confusion.

---

### Post by xyz on 2006-05-05
Don't be afraid to ask! No problem at all. In a way, I didn't make it clear.
You won't find any number nex to title beause there aren't any!
What you need to do is count the number of times you see "title" starting with 0,1..until you get to "title......Windows" as you scroll down. At this time you'll have 'a number X' in mind. That's the number you want to type next to 'default'.
I hope this is a better explanation. Don't hesitate to ask again.

---

### Post by 1002285 on 2006-05-05
[QUOTE=digen]Yes thats correct.Just to be sure you could paste the latter part of menu.lst file here in case to avoid any confusion.[/QUOTE]
This is it.

## ## End Default Options ##

title		Ubuntu, kernel 2.6.12-10-386 
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hdb2 ro quiet splash
initrd		/boot/initrd.img-2.6.12-10-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-10-386 (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hdb2 ro single
initrd		/boot/initrd.img-2.6.12-10-386
boot

title		Ubuntu, kernel 2.6.12-9-386 
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hdb2 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root		(hd1,1)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hdb2 ro single
initrd		/boot/initrd.img-2.6.12-9-386
boot

title		Ubuntu, memtest86+
root		(hd1,1)
kernel		/boot/memtest86+.bin  
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by xyz on 2006-05-05
## ## End Default Options ##

title Ubuntu, kernel 2.6.12-10-386   **0**
root (hd1,1)
kernel /boot/vmlinuz-2.6.12-10-386 root=/dev/hdb2 ro quiet splash
initrd /boot/initrd.img-2.6.12-10-386
savedefault
boot

title Ubuntu, kernel 2.6.12-10-386 (recovery mode)**1**
root (hd1,1)
kernel /boot/vmlinuz-2.6.12-10-386 root=/dev/hdb2 ro single
initrd /boot/initrd.img-2.6.12-10-386
boot

title Ubuntu, kernel 2.6.12-9-386**2**
root (hd1,1)
kernel /boot/vmlinuz-2.6.12-9-386 root=/dev/hdb2 ro quiet splash
initrd /boot/initrd.img-2.6.12-9-386
savedefault
boot

title Ubuntu, kernel 2.6.12-9-386 (recovery mode)**3**
root (hd1,1)
kernel /boot/vmlinuz-2.6.12-9-386 root=/dev/hdb2 ro single
initrd /boot/initrd.img-2.6.12-9-386
boot

title Ubuntu, memtest86+**4**
root (hd1,1)
kernel /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title Microsoft Windows XP Professional**5**
root (hd0,0)
savedefault
makeactive
chainloader +1

so I guess it is 5 - if you make a mistake,it won't wreck your system! Just go back to menu.lst until you get the right number.
Let me know.

---

### Post by 1002285 on 2006-05-05
I guess "5" was a goog guess, but this just made Grub highlight the line "other operating systems" and nothing booted after 10 secs. I think "6" will do the trick.
Thank you.

---

### Post by xyz on 2006-05-05
OOPS! Sorry..I missed the "other operating systems" bit!
Glad it works now.

---

### Post by 1002285 on 2006-05-05
ok, and now I'm doing the same thing on another computer and here I don't succeed.
The line for the FAT32 system that I want to mount, in the list (fdisk -l) is

/dev/hdb5 1281 2495 9759487+ b  W95 FAT32

but after the mount command it says:
wrong fs type, bad option, bad superblock on /dev/hdb5, missing codepage or other error.
Mounting fails at the booting too (I have changed the /etc/fstab file, without typos).

So what next?

---

### Post by AndrewCaul on 2006-05-05
It's also important to note that you'll need to update menu.lst when you update your kernel. As you probably know already a kernel upgrade adds two new items to the GRUB menu, but it does not modify the default setting. That needs to be updated manually.

---

### Post by hanexar on 2006-05-05
[QUOTE=1002285]ok, and now I'm doing the same thing on another computer and here I don't succeed.
The line for the FAT32 system that I want to mount, in the list (fdisk -l) is

/dev/hdb5 1281 2495 9759487+ b  W95 FAT32

but after the mount command it says:
wrong fs type, bad option, bad superblock on /dev/hdb5, missing codepage or other error.
Mounting fails at the booting too (I have changed the /etc/fstab file, without typos).

So what next?[/QUOTE]

This is the line I am using in fstab to mount a Fat partition in Ubuntu.  Make sure you have created the /media/share/ folder before, or it won't mount.  

```

/dev/hdb5       /media/share  vfat    iocharset=utf8,umask=000   0       0

```

I hope it work for you as well.

---

### Post by red_shrike on 2006-05-06
Look at [http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html) about editing fstab and more. It is quite a good ressource of knowledge

---

### Post by 1002285 on 2006-05-06
[QUOTE=hanexar]This is the line I am using in fstab to mount a Fat partition in Ubuntu.  Make sure you have created the /media/share/ folder before, or it won't mount.  

```

/dev/hdb5       /media/share  vfat    iocharset=utf8,umask=000   0       0

```

I hope it work for you as well.[/QUOTE]

Thank you, but this did not work either at this moment.
And to red_shrike - I will look at the resource you offered, but I'm hurrying away now.
I'll still give some more info here about this.

The computer has 2 hard drives and the original and the older one was called C: in Windows and had the same name after installing a new hard drive that was named F: and was made the main Windows drive (Windows has always been used here). 
The point of this talk is that maybe Windows is somehow blocking formating a drive that is named C:? For example Windows could not format this drive - I tried making it a FAT32 drive (from Windows) before installing Ubuntu.
And now Windows is still not showing anything on this drive, although half of it has a Ubuntu partition and filesystem on and I made the other half to be FAT32 during Ubuntu install.
Now I can't mount it in Ubuntu and Windows does not see it either. Any guesses?

Thanks for help, and I will look further myself, too.

---


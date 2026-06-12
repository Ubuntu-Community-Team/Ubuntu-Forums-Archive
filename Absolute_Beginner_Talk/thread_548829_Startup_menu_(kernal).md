---
title: "Startup menu (kernal)"
date: 2007-09-11
forum: Absolute Beginner Talk
---

### Post by Yizi on 2007-09-11
When i power my PC up i get 5 options, but i used to get 3.

**what i get now is:**

Kernal 2.6.20-16 -Generic
Recovery for it
Kernal 2.6.20-15 -Generic
Recovery for it
Windows

**used to get**

Kernal 2.6.20-16 -Generic
Recovery for it
Windows

how can i remove it? is it natural or there is something wrong.

---

### Post by bmeyer on 2007-09-11
It's not a bad thing for sure.  But if you want to remove them, do it here:

```
sudo gedit /boot/grub/menu.lst
```

Comment out the ones you know longer want in the menu.

---

### Post by philinux on 2007-09-11
Its just the upgrade if you look at the numbers 15 16 etc.

does windows allow you to step back from one version to the previous in case of conflicts etc.

ENJOY

---

### Post by Yizi on 2007-09-11
> **bmeyer said:**
> It's not a bad thing for sure.  But if you want to remove them, do it here:

```
sudo gedit /boot/grub/menu.lst
```

Comment out the ones you know longer want in the menu.

What do you mean comment out :-s

---

### Post by Yizi on 2007-09-11
That's what i get can you take out or edit what is right and paste it for me please.

```

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=1ef082d4-b7fd-4632-ac9c-178ef77d0896 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=1ef082d4-b7fd-4632-ac9c-178ef77d0896 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=1ef082d4-b7fd-4632-ac9c-178ef77d0896 ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=1ef082d4-b7fd-4632-ac9c-178ef77d0896 ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

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
```

---

### Post by sumguy231 on 2007-09-11
If you want to just uninstall the old kernel version, then just remove the 'linux-image-2.6.20-15-generic' package (if you're using the generic kernel image - if you don't know what that means, you're probably using generic) Uninstalling it will also obviously remove it from the boot menu. If you just comment the entry out, it will probably get uncommented by the system later when you update the kernel again.

---

### Post by Snoopyowns on 2007-09-11
To comment it out, just add a # to the start of the line that you want commented out. Once it's commented out, it will no longer show on the GRUB.

---

### Post by Yizi on 2007-09-11
> **sumguy231 said:**
> If you want to just uninstall the old kernel version, then just remove the 'linux-image-2.6.20-15-generic' package (if you're using the generic kernel image - if you don't know what that means, you're probably using generic) Uninstalling it will also obviously remove it from the boot menu. If you just comment the entry out, it will probably get uncommented by the system later when you update the kernel again.

How do i unistall it because i use the new version :confused:

---

### Post by sumguy231 on 2007-09-11
To uninstall it, you can open Synaptic, search for 'linux-image-2.6.20-15-generic', select it, and click 'remove' or whatever, then apply. Or, if you want to do it fromt the command line just use ```
sudo apt-get remove linux-image-2.6.20-15-generic
```

---

### Post by bmeyer on 2007-09-11
> **Yizi said:**
> That's what i get can you take out or edit what is right and paste it for me please.



Here's what I mean:

```

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=1ef082d4-b7fd-4632-ac9c-178ef77d0896 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=1ef082d4-b7fd-4632-ac9c-178ef77d0896 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

#title		Ubuntu, kernel 2.6.20-15-generic
#root		(hd1,0)
#kernel		/boot/vmlinuz-2.6.20-15-generic #root=UUID=1ef082d4-b7fd-4632-ac9c-178ef77d0896 ro quiet splash
#initrd		/boot/initrd.img-2.6.20-15-generic
#quiet
#savedefault

#title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
#root		(hd1,0)
#kernel		/boot/vmlinuz-2.6.20-15-generic #root=UUID=1ef082d4-b7fd-4632-ac9c-178ef77d0896 ro single
#initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

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
```

Note the new #'s in front of lines dealing with 2.6.20-15.  This will no longer allow those options to appear at boot.  It's better to comment them out than to delete them completely in case the need arises down the road to reimplement them into your list.

---

### Post by sumguy231 on 2007-09-12
It is a good idea to leave the old kernel alone until you know the new one works fine, though after that you should be able to uninstall it without hesitation.

---

### Post by Yizi on 2007-09-12
> **sumguy231 said:**
> To uninstall it, you can open Synaptic, search for 'linux-image-2.6.20-15-generic', select it, and click 'remove' or whatever, then apply. Or, if you want to do it fromt the command line just use ```
sudo apt-get remove linux-image-2.6.20-15-generic
```

I removed it, worked perfectly :KS

---

### Post by Yizi on 2007-09-12
Now something else just added to the option menu:

```
Ubuntu Memtest 86+
```

What is that? how do i remove it?

---

### Post by sumguy231 on 2007-09-12
That's the memory test option, it should have been there the whole time. It tests your RAM to see if it is working properly - it might come in handy, I'd say leave it alone. If it does bother you, you can comment it out as explained above.

---

### Post by Yizi on 2007-09-12
No i just leave it there :)

---


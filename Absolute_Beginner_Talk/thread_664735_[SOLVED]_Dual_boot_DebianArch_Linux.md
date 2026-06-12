---
title: "[SOLVED] Dual boot Debian/Arch Linux"
date: 2008-01-11
forum: Absolute Beginner Talk
---

### Post by 2017-Z on 2008-01-11
Currently I have Debian installed on machine and have spent the last week setting it up just the way I want it, but today decide I'd like to try out ArchLinux.

I have never done a dual boot before and after looking around on the internet decided I'd ask for a little help.

How do I install arch as a dual boot - Debain already has partitions for /boot /usr /home /swap /var etc an d.. well...I don't know

I'm just not sure what I should be doing - I'd dive right in and have a go but I really don't want to have to spend forever setting up Debian again.

Any help would be great - a short step-by-step guide would be amazing :P

Thanks in advance :]

---

### Post by Pevichaey5 on 2008-01-11
you might be lucky in the installation that it will give you the option of shrinking your existing partitions to make room for arch linux

---

### Post by floke on 2008-01-11
Everything you need to know is on the wiki

[http://wiki.archlinux.org/index.php/Beginners_Guide](http://wiki.archlinux.org/index.php/Beginners_Guide)

I boot Arch and Debian and its no trouble at all - personally I would leave the MBR Grub alone and add the Arch grub stanza to it (via debian, once you have Arch installed), rather than have Arch install grub on the mbr - there's nothing wrong with this, but when you update kernels in Debian you will have to add them to your grub (if you let Arch - or any other distro - create it) - whereas the Arch grub entries work slightly differently - ie you can add the Arch stanza (the grub entry to boot Arch) to your Debian (mbr) grub and won't need to change them when you get kernel updates in Arch.

Hopefully this hasn't confused you - anyway, read the wiki, take your time, expect frustration and a learning curve - and enjoy!

---

### Post by 2017-Z on 2008-01-13
Thank you both for your replies. My biggest concern is at the paritioning point of the arch install. Do I need to create 3 partitions for root home and swap? Do I need another primary for creating arch's root? How should my partition table look?

Eek I am quite confused and the arch wiki isn't helping :[

---

### Post by mali2297 on 2008-01-13
A simple setup would be to create a single root partition for Arch and let it share the swap partition with Debian.

---

### Post by 2017-Z on 2008-01-13
OK I've installed it but unsure how to boot it. I didn't write it to the GRUB menu as Floke suggested but confused as to what I should be writing in the menu.lst file.

I just copied and pasted the Debian entry for the kernel and I get 'Error 15: file not found'

Here's the end of my menu.lst
```
## ## End Default Options ##

title		Debian GNU/Linux, kernel 2.6.18-5-686
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.18-5-686 root=/dev/hda1 ro 
initrd		/boot/initrd.img-2.6.18-5-686
savedefault

title		Debian GNU/Linux, kernel 2.6.18-5-686 (single-user mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.18-5-686 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.18-5-686
savedefault

### END DEBIAN AUTOMAGIC KERNELS LIST

title		Arch
root		(hd0,2)
kernel          /boot/vmlinuz-2.6.18-5-686 root=/dev/hda1 ro
```

---

### Post by mali2297 on 2008-01-14
> **2017-Z said:**
> OK I've installed it but unsure how to boot it. I didn't write it to the GRUB menu as Floke suggested but confused as to what I should be writing in the menu.lst file.

I just copied and pasted the Debian entry for the kernel and I get 'Error 15: file not found'

Here's the end of my menu.lst
```
## ## End Default Options ##

title		Debian GNU/Linux, kernel 2.6.18-5-686
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.18-5-686 root=/dev/hda1 ro 
initrd		/boot/initrd.img-2.6.18-5-686
savedefault

title		Debian GNU/Linux, kernel 2.6.18-5-686 (single-user mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.18-5-686 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.18-5-686
savedefault

### END DEBIAN AUTOMAGIC KERNELS LIST

title		Arch
root		(hd0,2)
kernel          /boot/vmlinuz-2.6.18-5-686 root=/dev/hda1 ro
```

Check where Arch is located. Say that it is hda3, then (from Debian) look for the kernel name in
```

ls /media/hda3/boot/

```
If the partition is not mounted, do first
```

mount /dev/hda3 /media/hda3

```
Say that you find vmlinuz26 and  kernel26.img, then you add the following lines to menu.lst:
```

title	      Arch
root          (hd0,2)
kernel        /boot/vmlinuz26 root=/dev/hda3 ro
initrd	      /boot/kernel26.img

```
Note that if Arch is on hda3, then the root line should say (hd0,2) since 3-1=2.

---

### Post by 2017-Z on 2008-01-14
Thank you! It's now working - It won't let me run the rank mirrors script though, something about bad interpreter and usr/bin/python doesn't exist. Not terribly important however and I'm sure I can fix that a bit later.

Thank you for your help :]

---


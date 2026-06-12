---
title: "Ubuntu Kernel shows twice on GRUB"
date: 2006-07-21
forum: Absolute Beginner Talk
---

### Post by GStubbs43 on 2006-07-21
Hi all, this has happened since I have dual-booted Ubuntu and XP, when the GRUB menu shows, it lists 
[LIST]
[*]Ubuntu Kernel - blah blah blah
[*]Ubuntu Kernel - Recovery Mode
[*]Ubuntu Kernel - blah blah blah
[*]Ubuntu Kernel - Recovery Mode
[/LIST]
**Other OS**
[LIST]
[*]Widnows XP
[/LIST]

*Or something like that.*;)
Anyway, does anyone else have this problem, how can I fix it so it only shows once? It is only installed once and they both boot to the exact same Ubuntu. :-k  

Thanks, Gino

---

### Post by mattisking on 2006-07-21
Are you sure they aren't 2 differet kernel versions? If you are SURE you don't have 2 kernels installed, then simply:
sudo gedit /boot/grub/menu.lst

Look towards the bottom and remove the offending block. This is pretty obvious what to remove once you look or I'd be more descriptive.

---

### Post by mcduck on 2006-07-21
I there indeed are two different kernel versions installed, I'd rather uninstall the older one with Synaptic instead of just removing it from Grub menu.

---

### Post by GStubbs43 on 2006-07-21
Hey, I just looked at /boot/grub/menu.lst and apparently they are different kernel versions:
```

## ## End Default Options ##

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, kernel 2.6.15-23-386
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST
```

What should I do?:confused:

---

### Post by GStubbs43 on 2006-07-21
Should I just remove linux-image-2.6.15-23-386 and linux-restricted-modules-2.6.15-23-386 from snaptic, or is there more to it?

---

### Post by 5-HT on 2006-07-21
> **GStubbs43 said:**
> Should I just remove linux-image-2.6.15-23-386 and linux-restricted-modules-2.6.15-23-386 from snaptic, or is there more to it?

That's all there is to it. GRUB will be automagically updated.

---

### Post by GStubbs43 on 2006-07-21
I should be in the newer one when I remove the old one correct? How do I know which one I booted into, I can't remember. :p

---

### Post by 5-HT on 2006-07-21
> **GStubbs43 said:**
> I should be in the newer one correct? How do I know which one I booted into, I can't remember. :p
Yup. Not a good idea to remove the kernel you're currently using...
To check: ```
 uname -r 
```

*edit: yeah, my bad - forgot the space.

---

### Post by GStubbs43 on 2006-07-21
Of course, I am in the old one! I'll restart into the new one and remove the old one. Oh and by the way, it is uname -r with a space. ;)

EDIT: Looks like you found the space already! :rolleyes:

---

### Post by GStubbs43 on 2006-07-21
Thanks everyone! This has been bugging me for quite a while now!
The only reason I am dual-booting is so I can use my Dell printer with my laptop, other than that  I can do everything else with Ubuntu!
But, oh well, Lexmark and Dell need to realize their customers don't always use Windows. I'll live with it though! Thanks again!

---

### Post by Skia_42 on 2006-07-21
So were they giving any real trouble since they both booted to the same Ubuntu or was it just iritating?

---

### Post by GStubbs43 on 2006-07-21
Nah, no problems, it was just irritating seeing two ubuntu kernels on the GRUB menu. But I really didn't notice any problems with having them both installed, at least not that I knew of. ;)

---

### Post by Malac on 2006-07-24
> [[IMG]http://www.ubuntuforums.org/customavatars/avatar134051_1.gif[/IMG]]("http://www.ubuntuforums.org/member.php?u=134051") 			 			 				 					 					[GStubbs43]("http://www.ubuntuforums.org/member.php?u=134051") Thanks everyone! This has been bugging me for quite a while now!
The only reason I am dual-booting is so I can use my Dell printer with my laptop, other than that I can do everything else with Ubuntu!
But, oh well, Lexmark and Dell need to realize their customers don't always use Windows. I'll live with it though! Thanks again!

THIS IS IMPORTANT.
E-mail Lexmark and Dell and let them know that you would like future products to have Linux support/drivers.
The more people do this the easier it will be to get Linux working without relying on some kind soul coding a driver from scratch in their spare time.

---


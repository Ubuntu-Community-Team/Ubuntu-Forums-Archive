---
title: "How to add other Linux to Grub?"
date: 2005-07-01
forum: Absolute Beginner Talk
---

### Post by davidgypsy on 2005-07-01
.

---

### Post by dgantony on 2005-07-01
[QUOTE=davidgypsy]I am dual booting Ubuntu & XP, and Grub finds XP without problem and adds it to the options to boot. I have installed Mepis (to try it out) and installed the boot record to it's root partition (hda5). But Grub doesn't seem to be able to find it. How do I add it to Grub so that it gives me the option to boot Mepis?[/QUOTE]

I have Mepis installed along with Ubuntu. Here is the entry for Mepis in my menu.lst:

```
title MEPIS at hda5, kernel 2.6.10
kernel (hd0,4)/boot/vmlinuz-2.6.10 root=/dev/hda5 nomce psmouse.proto=imps quiet splash=verbose vga=791 
initrd (hd0,4)/boot/initrd.splash
```

I have it installed in /dev/hda5. Change them to fit your needs,

---

### Post by acascianelli on 2005-07-01
Try changing (hd0,4) to (hd0,5).

---

### Post by dgantony on 2005-07-01
[QUOTE=acascianelli]Try changing (hd0,4) to (hd0,5).[/QUOTE]

I think you misunderstood. /dev/hda5 is (hd0,4). It works fine for me. I was answering David's question.

---

### Post by jadugarr on 2005-07-01
[QUOTE=davidgypsy]I am dual booting Ubuntu & XP, and Grub finds XP without problem and adds it to the options to boot. I have installed Mepis (to try it out) and installed the boot record to it's root partition (hda5). But Grub doesn't seem to be able to find it. How do I add it to Grub so that it gives me the option to boot Mepis?[/QUOTE]

Edit your menu.list file in /boot/grub and add Mepis information under your ubuntu info.
Ex:
```
title Mepis 
root	       (hd0,4)
kernel	      /boot/vmlinuz-2.6.10-5-386 root=/dev/hda5 ro quiet splash
initrd		/boot/initrd.img-2.6.10-5-386
boot
```

Replace '/boot/vmlinuz-2.6.10-5-386' and '/boot/initrd.img-2.6.10-5-386' with whatever the 'vmlinuz' and 'initrd' files are on your mepis partition.  To check them just mount your mepis partition (/dev/hda5) and check it's /boot dir.  Both of the file names that you need will be in there, and make sure you type them exactly or it won't work.  

Hope that was specific enough.  Good Luck.  :)

---

### Post by davidgypsy on 2005-07-01
[QUOTE=dgantony]I have Mepis installed along with Ubuntu. Here is the entry for Mepis in my menu.lst:

```
title MEPIS at hda5, kernel 2.6.10
kernel (hd0,4)/boot/vmlinuz-2.6.10 root=/dev/hda5 nomce psmouse.proto=imps quiet splash=verbose vga=791 
initrd (hd0,4)/boot/initrd.splash
```

I have it installed in /dev/hda5. Change them to fit your needs,[/QUOTE]

WOW!! That was fast! And worked GREAT! Thank you so very much!

Ubuntu forums lead the way! :)

---

### Post by dgantony on 2005-07-02
[QUOTE=davidgypsy]WOW!! That was fast! And worked GREAT! Thank you so very much!

Ubuntu forums lead the way! :)[/QUOTE]

You are welcome. 

These forums are wonderful, aren't they. Saved my behind a bunch of times.  :smile:

---


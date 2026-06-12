---
title: "Where is &quot;ubuntu&quot;??"
date: 2006-07-22
forum: Absolute Beginner Talk
---

### Post by kitt on 2006-07-22
I have just installed ubuntu on my acer laptop without any problems.
One thing i noticed: During boot-up..my screen is blank. No "Ubuntu" written, and no status of the boot-up process! 
On my previous Laptop, i got a nice "what is happening" during boot-up and shut-down..but now i have to look at a blank screen (which makes me a bit nervous).
What is happening here?
Another thing: my boot-up time is incredibly fast for a machine with only 256 mb ram! Ive always heard linux is a bit slow in booting, but my system is up and running in less than a minute.

---

### Post by Ziox on 2006-07-22
before the screen goes blank, after it the screen says grub loads, and then a bunch of lines come up including kernel version, does anywhere there say usplash?

EDIT: better yet, go to terminal and type: 

sudo gedit /boot/grub/menu.lst

now look at the part without any of the hash marks, which should be after a line called: 

## ## End Default Options ##

look at the first "section" does it have a line similar to this: 

"kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda1 ro quiet splash" 

i think maybe the "splash" is missing from yours.

You can help by providing the content of this file: /boot/grub/menu.lst

---

### Post by robins_web on 2006-07-22
*my boot-up time is incredibly fast for a machine with only 256 mb ram*!

Yeah. Don't you miss those 5-minute Windows reboots? :mrgreen:

---

### Post by Ziox on 2006-07-22
> **robins_web said:**
> 
Yeah. Don't you miss those 5-minute Windows reboots? :mrgreen:

ahhh....the good old days :p

---

### Post by kitt on 2006-07-22
> **Ziox said:**
> before the screen goes blank, after it the screen says grub loads, and then a bunch of lines come up including kernel version, does anywhere there say usplash?

EDIT: better yet, go to terminal and type: 

sudo gedit /boot/grub/menu.lst

now look at the part without any of the hash marks, which should be after a line called: 

## ## End Default Options ##

look at the first "section" does it have a line similar to this: 

"kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda1 ro quiet splash" 

i think maybe the "splash" is missing from yours.

You can help by providing the content of this file: /boot/grub/menu.lst

Ok..here it is:
title           Ubuntu, kernel 2.6.15-23-386
root            (hd0,4)
kernel          /boot/vmlinuz-2.6.15-23-386 root=/dev/hda5 ro quiet splash
initrd          /boot/initrd.img-2.6.15-23-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root            (hd0,4)
kernel          /boot/vmlinuz-2.6.15-23-386 root=/dev/hda5 ro single
initrd          /boot/initrd.img-2.6.15-23-386
boot

title           Ubuntu, memtest86+
root            (hd0,4)
kernel          /boot/memtest86+.bin
boot
Other Operating Systems:
title           Linpus (2.6.15.4) (on /dev/hda1)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15.4 ro pci=noacpi root=/dev/hda1
savedefault
boot

---


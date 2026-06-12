---
title: "Dual Boot my Vista Home Basic with Ubuntu"
date: 2008-03-08
forum: Absolute Beginner Talk
---

### Post by ryshi12 on 2008-03-08
I'm very interested to learn more about Ubuntu..the problem is I do not have any experience making partitions and reformat..I need help in how to dual boot my Home Basic with Ubuntu..I have 160Gb HDD. Is there any step by step for idiots like me?

---

### Post by ODF on 2008-03-08
It's called the Grub, its the boot menu. You have to edit your /boot/grub/menu.lst

I'm running it with 2 différent HD ... so it looks like that.

## ## End Default Options ##

```
title		Ubuntu hardy (development branch), kernel 2.6.24-10-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-10-generic root=UUID=3e918fa6-f91d-43b2-b7d9-abb8e36b6b8c ro quiet splash
initrd		/boot/initrd.img-2.6.24-10-generic
quiet

title		Ubuntu hardy (development branch), kernel 2.6.24-10-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-10-generic root=UUID=3e918fa6-f91d-43b2-b7d9-abb8e36b6b8c ro single
initrd		/boot/initrd.img-2.6.24-10-generic

title		Ubuntu hardy (development branch), kernel 2.6.24-8-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-8-generic root=UUID=3e918fa6-f91d-43b2-b7d9-abb8e36b6b8c ro quiet splash
initrd		/boot/initrd.img-2.6.24-8-generic
quiet

title		Ubuntu hardy (development branch), kernel 2.6.24-8-generic (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-8-generic root=UUID=3e918fa6-f91d-43b2-b7d9-abb8e36b6b8c ro single
initrd		/boot/initrd.img-2.6.24-8-generic

title		Ubuntu hardy (development branch), memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (on /dev/hda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=43b5d164-ca8f-4457-a7e2-aeffe3af6283 ro quiet splash 
initrd		/boot/initrd.img-2.6.22-14-generic
savedefault
boot

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode) (on /dev/hda1)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=43b5d164-ca8f-4457-a7e2-aeffe3af6283 ro single 
initrd		/boot/initrd.img-2.6.22-14-generic
savedefault
boot

title		Ubuntu 7.10, memtest86+ (on /dev/hda1)
root		(hd0,0)
kernel		/boot/memtest86+.bin  
savedefault
boot

title		Windows Vista
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

```

You're looking for this. (hd1,0) means it's my second HD on the first partition. As you can see in my HARDY HERON its (hd0,2) as first HD, third partition ... and first hd and first partition for my GUTSY (hd0,0).

```
title		Windows Vista
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1
```

Its pretty much it. I hope it helps =)

Edit : since you're new to ubuntu and probably linux ... you need to act as the super user to modify your file system. To do so you have to use the 'sudo' command. In order to edit your menu.lst you need to open it in your text editor with the super user command wich will do : 'sudo gedit /boot/grub/menu.lst'

Ps : Carefull while editing your file system, for your grub editing always keep your gutsy settings ... just add the windows thing. If anything is wrong at least you'll have access to your ubuntu.

=)

---


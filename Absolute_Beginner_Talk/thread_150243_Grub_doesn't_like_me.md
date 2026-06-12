---
title: "Grub doesn't like me"
date: 2006-03-25
forum: Absolute Beginner Talk
---

### Post by mc4 on 2006-03-25
I am attempting to dual boot a system using grub.
I have Windows on the 1st hard drive and Linux on the 2nd.  
I used the Ubuntu settings for grub and I have tried a bunch of different partition methods.

The problem is when I select Ubuntu from the grub menu it runs through a script:
root (hd1,1)
Filesystem type is ext2fs, partition type 0x83
<snip>
savedefault
boot

Then nothing happens. The hard drive does not spin and nothing is loaded.

---

### Post by Bishop Hill on 2006-03-25
This kinda sounds like my computer when I had an xserver problem, but I dont think that is it.

Have you tried reinstalling grub?

---

### Post by sn123 on 2006-03-25
[QUOTE=mc4]
root (hd1,1)
Filesystem type is ext2fs, partition type 0x83
<snip>
savedefault
boot

Then nothing happens. The hard drive does not spin and nothing is loaded.[/QUOTE]
not too sure why that would happen but does it boot other OS properly (windows, ubuntu recovery mode etc.)? Also, you might want to post the content of your grub's menu.lst file.
```

$ cat /boot/grub/menu.lst

```

S

---

### Post by mc4 on 2006-03-25
[QUOTE=sn123]not too sure why that would happen but does it boot other OS properly (windows, ubuntu recovery mode etc.)? Also, you might want to post the content of your grub's menu.lst file.
```

$ cat /boot/grub/menu.lst

```

S[/QUOTE]

Windows XP boots fine.

I wont type out the whole thing but this seems like the important bits.

Default 0
timeout 10

title Ubuntu, kernel 2.6.12-9-386
root (hd1,1)
kernel /boot/vmlinux-2.6.12-9-386 root=/dev/hdb2 ro quiet splash
initrd /boot/initrd.img-2.6.12-9-386
savedefault
boot

<snip ubuntu recovery mode and memtest>

title Microsoft Window XP Professional
root (hd0,0)
savedefault
makeactive
chainloader +1

---

### Post by mc4 on 2006-03-26
So no ideas?

---

### Post by Sutekh on 2006-03-26
[QUOTE=mc4]
...

title Ubuntu, kernel 2.6.12-9-386
root (hd1,1)
kernel /boot/vmlinux-2.6.12-9-386 root=/dev/hdb2 ro quiet splash
initrd /boot/initrd.img-2.6.12-9-386
savedefault
boot

...

So no ideas?[/QUOTE]
Sure, you need to verify the location of Ubuntu's root filesystem.  

You know its on the second disc so 
```
root  (hd1,#)
```is okay. 
 
What we need to determine is the value of #, the partition number.

It's probably
```
root   (hd1,**0**)
```
(you start counting from 0, which is why Windows is hd0,0 - the first disc, first partition), but to be sure can you post the output of ```
sudo fdisk -l
```
That will show the location of Ubuntu's root filesystem (/)

---

### Post by mc4 on 2006-04-03
h1,1 is correct.  I tried reinstalling on h1,0 and still no dice.  I'm starting to wonder if it's a bios issue.  Maybe grub can't see the hard drive properly?

---


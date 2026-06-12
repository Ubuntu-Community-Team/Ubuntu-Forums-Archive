---
title: "Install freezes"
date: 2007-01-08
forum: Absolute Beginner Talk
---

### Post by noenter1 on 2007-01-08
I had to use the noapic command to get the disk to load cause of the noapic error. That fixed that problem, however when I try to install Ubuntu 6.06 or 6.10(amd64 versions of each) on a secondary 500gb hard drive(sata) and it freexes at 15% and I have to restart my computer ](*,) . I have a AMD Athlon 64 X2 4600+ Windsor 2.4GHz , ASUS M2N32-SLI Deluxe Wireless Edition Socket AM2 NVIDIA nForce 590 SLI, ASUS EN7900GT/2DHT/256M GeForce 7900GT, CORSAIR XMS2 2GB 800mhz, 16X DVD±R DL. Any fixes would be apperieated

---

### Post by hal10000 on 2007-01-08
Add the **noapic** option to the **kernel** line of your /boot/grub/menu.lst file: e.g.:
```

title           Ubuntu, kernel 2.6.17-10-generic
root            (hd0,4)
[COLOR="Red"]**kernel**[/COLOR]          /boot/vmlinuz-2.6.17-10-generic root=UUID=7f744eca-334e-431b-8c51-48febd70103b ro elevator=cfq [COLOR="Red"]**noapic**[/COLOR]
initrd          /boot/initrd.img-2.6.17-10-generic
savedefault
boot

```

---

### Post by noenter1 on 2007-01-08
Sorry but can you give me a general idea as how to get to the file. Its been way too long since I messed with linux. Help always appreciated.

---

### Post by hal10000 on 2007-01-09
Can you tell me at which point exactly it freezes?
To get more information about the boot process you can delete the [COLOR="Red"]quiet [/COLOR]option on the boot prompt (the boot prompt is the line with the cursor).

---

### Post by noenter1 on 2007-01-09
I am at work right now so I cant check it out but I will try it as soon as I get home. I know that the install creates all the partitions and it freezes at 15% install progress and the computer goes unresponsive and I have to restart.

---

### Post by noenter1 on 2007-01-09
Ok i didnt realize that part of my problem might be my bios. I saw alot of other people with 64bit systems have similar problems and the cause seems to be the bios. So when I get back home im going to update my bios and hopefully that will fix everything. if not then i wil continue researching it.

---

### Post by noenter1 on 2007-01-10
The bios was the problem. After I updated the bios I no longer needed to use the noapic command to start the live cd. I installed Ubuntu and it is now working perfectly. :D Thank for all the help guys

---


---
title: "manually adding gutsy to grub"
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by mortuk on 2008-01-16
Hey all

I have been using fesity for a while now and am upgrading to gutsy, but wanted to keep my old setup so decided to dual boot the two

Anyways in the gutsy install, right before the install proceeds theres the advanced button, where i told it to not install grub as I didnt want it to overwrite the old one so i wouldnt be able to get into my working OS

So now I am back in fesity but cannot figure out how to get to my vanilla gutsy install, could someone help me out? Have spent a couple of hours looking at grub and the update-grub commands with no joy, I also tried to manually add gutsy to my menu.lst but when i goto it the loading bar gets stuck on 1px

Here is my fdisk -l
```

/dev/sda1               1        1824    14651248+  83  Linux
/dev/sda2            1825        2322     4000185   82  Linux swap / Solaris
/dev/sda3            2323       27818   204796620   83  Linux
/dev/sda4           27819       60801   264935947+   5  Extended
/dev/sda5           27819       29603    14337981   83  Linux
/dev/sda6           29604       60801   250597903+  83  Linux
```

sda1 is my feisty /, sda4 is my gutsy /. does it matter that my gutsy install is on an extended partition?

any ideas?

---

### Post by jd65pl on 2008-01-16
See grub-install

---

### Post by mortuk on 2008-01-16
i am impressed at how vague that answer is ;)

especially seeing as i posted in absolute beginner talk. i am ok with linux and ubuntu in general but have v little experience with grub, so could someone please give me a little more to go on?

tried it and this is all i get, dont know if thats good or not :P

```

chris@machater:~$ sudo grub-install hd0
Installation finished. No error reported.
This is the contents of the device map /boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(hd0)   /dev/sda
```

---

### Post by dstew on 2008-01-16
Actually, your gutsy is sda5. sda4 is the base extended partition that contains the logical partitions sda5 and sda6.

To boot gutsy, you need to add the commands to whatever /boot/grub/menu.lst file that grub is using. I suspect it is in your sda1 partition (Feisty). You will need to add something like this:```
title Ubuntu Gutsy
root (hd0,4)
kernel /vmlinuz-2.6.22-14-generic root=/dev/sda5 quiet splash
initrd /initrd.img-2.6.22-14-generic
quiet
savedefault
```You will need to look in the /boot directory on /dev/sda5 to see what the kernel names are. Did you install the 32 or 64-bit gutsy?

---

### Post by mortuk on 2008-01-16
ahh yes good point on sda5 not sda4

32bit, so the menu.lst entry you have put above should work fine

though i get grub error 15, file not found, which is wierd as the file names are correct

any ideas?

---

### Post by mali2297 on 2008-01-16
I think it should be
```

title Ubuntu Gutsy
root (hd0,4)
kernel [COLOR="Red"]/boot[/COLOR]/vmlinuz-2.6.22-14-generic root=/dev/sda5 quiet splash
initrd [COLOR="Red"]/boot[/COLOR]/initrd.img-2.6.22-14-generic
quiet
savedefault

```
or alternatively
```

title Ubuntu Gutsy
root (hd0,4)
kernel /vmlinuz root=/dev/sda5 quiet splash
initrd /initrd.img
quiet
savedefault

```

---

### Post by dstew on 2008-01-16
Mali, I think you are right. The directory containing the kernel should be **/boot**, as you posted.

---

### Post by mortuk on 2008-01-17
yup perfect, cheers mali :D much appreciated!!

also thanks to everyone else who gave me answers totalling more than 2 words :P

---


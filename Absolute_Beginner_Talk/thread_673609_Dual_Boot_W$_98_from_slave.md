---
title: "Dual Boot W$ 98 from slave"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by Semong on 2008-01-20
Ok I have Xubuntu 7.10 installed on my main hard-drive and Windows 98 is installed on my slave. How would I go about putting the option to boot windows 98 into my grub menu? Or better yet to copy windows from my second hard-drive onto a partition of my primary disk and then adding it to my grub. All help would be tremendously appreciated.

---

### Post by Squizz on 2008-01-20
If you want to put it into your grub menu:

Edit your grub menu by using

```
gksudo gedit /boot/grub/menu.lst

```
(or sudo nano /boot/grub/menu.lst if that doesnt work)

add the following to the bottom

```

title Windows 98
rootnoverify (hd1,0)
savedefault
chainloader +1

```

If Windows 98 is the only OS on your 2nd HDD then that should work I believe.

You may also want to change 

timeout 3

to a higher number to give you more time to choose an option.

---

### Post by Semong on 2008-01-20
hrm that didn't work. When I select W$ 98 it just says starting up. Would it have anything to do with the fact that in bios>system information its reading my second hdd as primary #2 instead of slave? I took off the little black plastic thing on the back of the hard-drive and was under the impression that that should turn it into a slave drive but apparently not. I don't see any options in my bios to change it to slave either.

So how would I go about copying windows into a partition on my primary hard-drive? Im thinking i can run the live CD, resize my Ubuntu partition, create an fts partition, then copy the second hard-drive and paste it into the new partition however I'm unaware of what to put into my grub. Would it be:

title Windows 98
rootnoverify (hd0,0)
savedefault
chainloader +1

? Also should I put this line below ### END DEBIAN AUTOMAGIC KERNELS LIST or just above it?

---

### Post by Squizz on 2008-01-20
To make it into a slave drive, you have to reposition the jumper (little black plastic thing) - on most hard drives it gives a diagram of where you should put it, although I don't think that would be your problem.

If you run 
```

sudo fdisk -l

```

It should give some indication what order your hard drives are in.

I have no idea if copying your Windows install over to an existing partition would work or not - but if you wanted to point it there, then you would use rootnoverify (hd0,1) as it would be your primary hard drive, but the second partition.

---

### Post by torgrot on 2008-01-21
Actually the code would look like this ```

title Windows 98
root            (hd1,0)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1

```

Windows has to be fooled into believing it is being booted off the first partition on the first hard drive.

torgrot

---


---
title: "Resize partion"
date: 2007-11-13
forum: Absolute Beginner Talk
---

### Post by Andrew123 on 2007-11-13
Can you resize the windows partion because I gave too much Space to ubuntu and only have 40gb for windows and 100 for ubnuntu can i change this?

---

### Post by skymera on 2007-11-13
deja vu :)

i got 100gb ubuntu lol
and 45gb windows.

i dont care as im gettin new HD.

you can try and use gparted,but for safety, i would use something in windows, partitionmagic for example.

---

### Post by Andrew123 on 2007-11-13
Thanks i was going to backup everthing . How safe is it to do it in windows?

---

### Post by tech9 on 2007-11-13
> **skymera said:**
> deja vu :)

i got 100gb ubuntu lol
and 45gb windows.

i dont care as im gettin new HD.

you can try and use gparted,but for safety, i would use something in windows, partitionmagic for example.

if you are resizing your partition in windows, then partition magic works well... other I agree with using gparted from Ubuntu

---

### Post by Tux.Ice on 2007-11-13
use qtparted

sudo apt-get install qtparted should install it then just terminal qtparted

---

### Post by Inxsible on 2007-11-13
you can use Gparted which is on the Live CD. I did that a month back without any problems.

Altho, I did it the other way round, I had given 25 GB to windows...which was way too much. Reduced it to 15 GB, and i still think it's too much ;)

Maybe I will reduce it to 10 :D

---

### Post by tech9 on 2007-11-13
> **Andrew123 said:**
> Thanks i was going to backup everthing . How safe is it to do it in windows?

surprisingly.... it's safe :)

---

### Post by Andrew123 on 2007-11-13
I'm trying to do it with the live cd ... what do i do?? to a just make ubuntu smaller ? because when i click on the windows partion i can't increase it

---

### Post by tech9 on 2007-11-13
> **Andrew123 said:**
> I'm trying to do it with the live cd ... what do i do?? to a just make ubuntu smaller ? because when i click on the windows partion i can't increase it

you want to unmount the partition, then choose the resize option

---

### Post by bumanie on 2007-11-13
When I have used g-parted live cd, I found it safe and easy. Boot from live cd, click on the partition you want to resize, then click on the resize/move icon. A box comes up that allows you to resize with a slider or to nominate size in mb. (I use the slider). Do your resize, double check that it is the size you and click on the apply icon. G-parted double checks with you whether you want to apply the changes. If all is OK click yes and let it do its thing. Has never mucked up any info when I have used it. Good luck. It is not hard to do.

---

### Post by CatKiller on 2007-11-13
> **Andrew123 said:**
> I'm trying to do it with the live cd ... what do i do?? to a just make ubuntu smaller ? because when i click on the windows partion i can't increase it

It's been a while since I did it, but you may need to move the start of your Ubuntu partition, if it's the partition that comes after your Windows one. If they're right next to each other then there's nothing to extend the Windows partition into. You should be able to resize the right-hand partition, then slide it to the right, and then increase the size of the left-hand partition.

I hope that makes sense.

---

### Post by Inxsible on 2007-11-13
A screenshot, of how your partitions are laid out would be helpful in determining whether or not you can move/resize them.

---


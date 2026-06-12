---
title: "Resize  ubuntu partition"
date: 2008-06-12
forum: Apple Hardware Users
---

### Post by the walking dude on 2008-06-12
I recentley installed Ubuntu 8.04 on my iMac using boot camp, but now i want to try wine and some other stuff out, but I don´t have enough space on my partition.
Is there any way I can resize the partition without losing anything on it?

---

### Post by snowpine on 2008-06-12
Hi Dude, I would recommend using a Live CD. Maybe you still have one lying around from when you did your install? Once you have the Live CD started up, you can find the Partition tool in the System menu. If you do everything right, you will not lose any data, however, backing up first is always recommended! Are you familiar with how partitions work, or do you need a basic tutorial?

---

### Post by the walking dude on 2008-06-12
I didn´t write this clearly in my first post i don´t want to lose anything on my Mac os x partition either.
Does the live cd keep me from losing any data on my Mac partition, becouse my usb hard drive doesn´t have room for everything I need to take a back up.

---

### Post by cyberdork33 on 2008-06-12
> **the walking dude said:**
> I didn´t write this clearly in my first post i don´t want to lose anything on my Mac os x partition either.
Does the live cd keep me from losing any data on my Mac partition, becouse my usb hard drive doesn´t have room for everything I need to take a back up.gparted can resize (shrink) your OSX partition, but I would still backup my data if i were you.

---

### Post by snowpine on 2008-06-12
> **cyberdork33 said:**
> gparted can resize (shrink) your OSX partition, but I would still backup my data if i were you.

+1... gparted is really easy to use... each partition is a colored bar, and you simply use the mouse to make the bars bigger or smaller... it is tough to actually delete any data if you are careful... that being said, I would not do it without backing up essential data!

---

### Post by the walking dude on 2008-06-13
I tried, but all the partitions is locked how can I unlock them.

I didn´t use the live cd. Now everything works.

---

### Post by snowpine on 2008-06-13
> **the walking dude said:**
> I tried, but all the partitions is locked how can I unlock them.

I didn´t use the live cd. Now everything works.

Right on Dude, as you discovered, you need to boot from the Live CD because you can't repartition a partition on your hard drive while it's in use. :)

---

### Post by cyberdork33 on 2008-06-13
> **snowpine said:**
> Right on Dude, as you discovered, you need to boot from the Live CD because you can't repartition the hard drive while you're using it. :)
Actually, you just can't adjust partitions that are in use (mounted).

---

### Post by rifak on 2008-06-29
i am trying to do this. i installed gparted then booted from Ubuntu 8.04 cd. when i open gparted, it won't let me do anything. I attached a screenshot. please help. i only allowed myself 10gigs for 'buntu when i orginally installed, and i liked it so much i need to give myself like 4 times that haha

---

### Post by lisati on 2008-06-29
> **switham said:**
> i am trying to do this. i installed gparted then booted from Ubuntu 8.04 cd. when i open gparted, it won't let me do anything. I attached a screenshot. please help. i only allowed myself 10gigs for 'buntu when i orginally installed, and i liked it so much i need to give myself like 4 times that haha
You might still have to unmount the partitions, even when you are using the Live CD. Select the partition, and right-click on it. If an unmount option is available, you're in with a chance (it won't delete your data if you're careful)

---

### Post by rifak on 2008-06-29
i tried that. the only one i could have the chance to unmount was the ext3 partition, but it would just say it was unable to do that, and refresh itself. the other ones don't give me an option to unmount.

---

### Post by cyberdork33 on 2008-06-29
unmount the ext3 partition:
```
sudo umount /dev/sda3
```

umount (quit using) the swap:
```
sudo swapoff /dev/sda5
```

Then try gparted...

---

### Post by rifak on 2008-06-30
that would not work..here's what i did though:

i logged into ubuntu, and resized my macbook hard drive through gparted. then i booted into the gparted live cd, and filled in the free space i just created with the ext3. after that. i got more space, but i had to reinstall ubuntu into the newly created free space. it wasn't too bad, considering i just started using this the other day, so i didnt have to many things to get back up and running. thanks though.

---


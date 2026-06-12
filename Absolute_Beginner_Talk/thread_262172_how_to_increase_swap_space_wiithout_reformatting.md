---
title: "how to increase swap space wiithout reformatting"
date: 2006-09-21
forum: Absolute Beginner Talk
---

### Post by navneet.net on 2006-09-21
hello everyone...
i want to increase the swap space without reformatting the root or boot partitions....
is it possible....how?

---

### Post by kidders on 2006-09-21
Hi there,

It sounds like your swap partition is sitting between two others, that you'd rather not have to mess around with. There is no reason why all your swap *has* to be in the same place on your disk. If you'd like to, simply create another and add it to your /etc/fstab.

[LIST=1]
[*]Use, say, cfdisk to create a new swap partition, maybe at /dev/sdb5
[*]Run **sudo mkswap /dev/sdb5** to format it
[*]Run **sudo swapon /dev/sdb5** to get your system using it
[*]Add a line to /etc/fstab to make the change permanent
[/LIST]

If you feel like it, take a look at swap priority. This lets you choose the order in which each swap partition gets used. One possible configuration might be to create 3 of them, each on a different physical disk. Giving them all a priority of, say, zero, would instruct your system to use them in parallel, increasing the performance of large paging operations.

---

### Post by hw-tph on 2006-09-21
You can add a second swap partition. Just create the new partition, set it to type 82 (Linux swap), run **mkswap** on it, followed by **swapon** (with the device name as a parameter, say /dev/hdb1 if your new swap is the first partition on your second IDE HDD. Then add an entry for it in /etc/fstab. If the new swap partition is called /dev/hdb1 it could look like this:
```
/dev/hdb1       none            swap    sw              0       0
```

That's it.

Håkan

*Edit:*I missed the bus. :)

---

### Post by b_martinez on 2006-09-21
Or you can install gparted and increase the swap size. You do this by resiing an existing partition, if all your hard drive(s) is(are) formatted.
 Gparted is graphical and easy to use. Re-boot after you are set up , and the changes will take effect.
hth
Bill

---

### Post by lha on 2006-09-21
If you don't want to mess around with partitions, take a look at this [Red Hat Manual page on adding swap space]("http://www.redhat.com/docs/manuals/linux/RHL-8.0-Manual/custom-guide/s1-swap-adding.html"). Look for 'To add a swap file:' in the bottom of that page. Easy and safe. :)

---


---
title: "Delete Partition"
date: 2007-11-23
forum: Absolute Beginner Talk
---

### Post by bern1939 on 2007-11-23
Hello again,

ok so I've got to the point where I only now have Ubuntu on the computer and it is really great.

From a previous posting someone asked why I had 2 swaps!!
I don't know is the answer but would like to get rid of one of them. It seems that the swap on [COLOR="Red"]/dev/SDA5[/COLOR] is inactive and could be got rid of but when I try to delete I get the msg. as shown on the attached .png.

What could I do at this stage......not critical but would like to learn!

Thanks so much


Bern

---

### Post by mellowd on 2007-11-23
unmount that partition using this command:

```
sudo unmount -k /dev/sda5
```

---

### Post by taurus on 2007-11-23
You cannot delete a partition, even a swap, when it's in use.  You need to unmount it first.  So, run

```
swapoff /dev/sda5
```
Now, open gparted again and you can delete /dev/sda5.  

You also need to edit /etc/fstab to remove an entry for /dev/sda5 in there.

```
gksudo gedit /etc/fstab
```

---

### Post by mikewhatever on 2007-11-23
Use gparted live cd. While running from the cd, no partition is mounted so you'll have no such errors.

---

### Post by mellowd on 2007-11-23
If the partition is already inactive you wouldn't need to take the swap off or edit your /etc/fstab. But it might be a good idea just to look anyway

---

### Post by dips_xe on 2007-11-23
mikewhatever is right, use the gparted live cd.

---

### Post by bern1939 on 2007-11-23
Afraid nothing works ..... same response as before.

Must say do not understand the mention of using "gparted live cd".
What is that?

Thanks

Bern

---

### Post by bluepowder7 on 2007-11-23
is it possible that you need to unmount the extended partition as a whole before being able to blow away a logical partition that's part of the extended partition?  see if you can highlight all of /dev/sda4.  if that doesn't work, grab that CD that you used to install ubuntu and run a live session (in other words, boot into that CD).  from there, you can likely unmount a lot of stuff and blow away partitions that you don't need.

---

### Post by StephUb on 2007-11-23
G parted is asking you to unmount all partitions after the swap you want to delete.
The thing is you are on ubuntu which is on the sda6.

So you have to use a live CD. (Linux which run from the CD)
You can use ubuntu live cd or go for Gparted live CD ([http://gpartedclonz.tuxfamily.org/download.php](http://gpartedclonz.tuxfamily.org/download.php))
From there you can delete pretty much everything so you're warned..
You should be able to remove the partition and move the others.

---

### Post by bern1939 on 2007-11-23
Thanks to all ..... got it sorted

Bern

---


---
title: "GNOME partition editor"
date: 2007-06-29
forum: Absolute Beginner Talk
---

### Post by Matthyis on 2007-06-29
I deleted my fat 32 partition with GNOME partition editor but it still shows up in the grub do I have to do anything or what do I have to do for grub not to show the xp/fat32 partition?
also I just want to add I wanted to delete xp :)

---

### Post by dptxp on 2007-06-29
You deleted XP ?
Now you will have to format the partition and mount it.
Edit the Grub too.

---

### Post by KIAaze on 2007-06-29
To change the Grub entries, just edit your /boot/grub/menu.lst file.
```
sudo nano /boot/grub/menu.lst
```

---

### Post by starcraft.man on 2007-06-29
Ok, this an easy one...

[Page detailing how to edit GRUB entries (best to understand it).]("http://users.bigpond.net.au/hermanzone/p15.htm") The operating system entries is the important section you wanna read.

I assume you formatted the now empty space with GParted and reclaimed it as Ext3. [So to mount it separately read this.]("http://www.psychocats.net/ubuntu/mountlinux") Just a basic guide to mounting.
[URL="http://doc.gwos.org/index.php/Understanding_fstab"]
More complete info on Fstab and mounting here.[/URL]

---

### Post by skymera on 2007-06-29
you had xp installed on a fat32?

---

### Post by Matthyis on 2007-06-29
> **dptxp said:**
> You deleted XP ?
Now you will have to format the partition and mount it.
Edit the Grub too.
yes my 30 days are up and I wanted to have more disk space
> **KIAaze said:**
> To change the Grub entries, just edit your /boot/grub/menu.lst file.
```
sudo nano /boot/grub/menu.lst
```
thank you that looks use full I guess I'll just edit the Microsoft XP entry
> **starcraft.man said:**
> Ok, this an easy one...

[Page detailing how to edit GRUB entries (best to understand it).]("http://users.bigpond.net.au/hermanzone/p15.htm") The operating system entries is the important section you wanna read.

I assume you formatted the now empty space with GParted and reclaimed it as Ext3. [So to mount it separately read this.]("http://www.psychocats.net/ubuntu/mountlinux") Just a basic guide to mounting.
[URL="http://doc.gwos.org/index.php/Understanding_fstab"]
More complete info on Fstab and mounting here.[/URL]

hey thanks this looks good it is a better understanding I just wanted to add more space thank you I wish their was a  How To

---

### Post by dptxp on 2007-06-30
If you are going for Only Ubuntu, best is to backup data, repartition and reinstall. If that suits you.

---


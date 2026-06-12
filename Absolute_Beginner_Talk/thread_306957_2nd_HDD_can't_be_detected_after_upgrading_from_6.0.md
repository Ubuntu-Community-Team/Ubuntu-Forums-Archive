---
title: "2nd HDD can't be detected after upgrading from 6.06 to 6.1"
date: 2006-11-25
forum: Absolute Beginner Talk
---

### Post by oliviacond on 2006-11-25
Before this, I use 6.06 . It can detect the NTFS HDD and I can mount it. But since I upgraded to 6.10 , the HDD no more detected. The device manager can detect it. But I can't see the drive at Places>Computer. The BIOS has no problem detecting it.

---

### Post by phidia on 2006-11-25
You may need to edit /etc/fstab to include that drive-why it isn't automounting I don't know. 
Perhaps you want to post the output from > sudo fstab -l and then someone can help you with editing fstab.

---

### Post by oliviacond on 2006-11-25
why there's no output? It just display
> > _

---

### Post by confused57 on 2006-11-25
Here's an excellent link for mounting Windows and editing your /etc/fstab:

[http://users.bigpond.net.au/hermanzone/p10.htm](http://users.bigpond.net.au/hermanzone/p10.htm)

---

### Post by oliviacond on 2006-11-25
But I think my problem is not mount. Is the detection of the hard drive. How can I mount the drive if OS can't detect the hdd?

---

### Post by CatKiller on 2006-11-25
> **oliviacond said:**
> But I think my problem is not mount. Is the detection of the hard drive. How can I mount the drive if OS can't detect the hdd?

I'm confused. You already said that it could:

> **oliviacond said:**
> The device manager can detect it. But I can't see the drive at Places>Computer. The BIOS has no problem detecting it.

Which suggests that you just haven't successfully mounted it.

Perhaps if you gave some more information about what is happening, people would be more able to help you. For example, what does this > why there's no output? It just display
[QUOTE]> _ [/QUOTE] mean? Where do you get that output? Are you able to log in? What does your /etc/fstab look like? And so on...

---

### Post by confused57 on 2006-11-25
> **oliviacond said:**
> But I think my problem is not mount. Is the detection of the hard drive. How can I mount the drive if OS can't detect the hdd?
To determine if Ubuntu detects your Windows drive, open a terminal, enter:
```
sudo fdisk -l
```
The -l is a small "L".

If it does, just follow the directions in the link I gave for mounting.

---

### Post by oliviacond on 2006-11-25
ok, problem solved. Sorry for making you all confuse.

---

### Post by confused57 on 2006-11-25
> **oliviacond said:**
> ok, problem solved. Sorry for making you all confuse.
No problem, glad you were able to work things out.

---


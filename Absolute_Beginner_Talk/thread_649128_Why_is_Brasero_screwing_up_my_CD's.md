---
title: "Why is Brasero screwing up my CD's?"
date: 2007-12-24
forum: Absolute Beginner Talk
---

### Post by Pogeymanz on 2007-12-24
I use the Gnome app, brasero to try burn a Linux iso to a CD-R. And when I pop it back in and run the "intergrity test", it fails. I've wasted three CD's on it now. What is up with it?

---

### Post by p_quarles on 2007-12-24
Try burning the disk at the slowest possible speed. Also, make sure you check the MD5sum on the image before you burn it -- the problem may also be due to download errors.

---

### Post by Pogeymanz on 2007-12-24
How does one check the MD5sum? Sorry if it's obvious; I would try to figure it out myself, but I'm not on my computer right now.

---

### Post by p_quarles on 2007-12-24
There's a how-to on MD5s here:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Note the link at the bottom of the third paragraph: that will take you to a list of all sums for Ubuntu .ISOs. You just need to get the number for your version, and then run the checksum on the image you downloaded. If they match, all is well.

---

### Post by Majorix on 2007-12-24
Do other CD writer software work? K3B? Gnomebaker?

My laptop DVD writer is out of order and it does exactly what you say.

---

### Post by Lord DarkPat on 2007-12-24
Maybe you have a bad iso? Happens sometimes. Or else, try with K3b and check. Might do th trick :)

---

### Post by Pogeymanz on 2008-01-17
So, to revisit my problem: I download an .iso and burn it with brasero or xfburn at the slowest possible speed and it always fails the integrity test. I check md5sums and they are fine. They are mostly LiveCD's (to spread the word) and sometimes it only screws up something unimportant, but sometimes it screws up the main system files on the install stuff.

I dual-boot with XP and it always burned CD's fine and it will burn the same .iso and it will work when the disk from Ubuntu wont.

I guess I'll try a third burner program; gnomebaker. But can anybody think of what is going wrong?

---


---
title: "Wiping partition of hard drive"
date: 2007-07-09
forum: Absolute Beginner Talk
---

### Post by djhworld on 2007-07-09
Hi there, I'm wanting to wipe a partition on my hard drive with just zeros.

Now I've heard you can use this command

```
dd if=/dev/zero of=/dev/hda
```

But this wipes your entire hard drive! 

I just want to wipe 1 partition!

---

### Post by overdrank on 2007-07-09
> **djhworld said:**
> Hi there, I'm wanting to wipe a partition on my hard drive with just zeros.

Now I've heard you can use this command

```
dd if=/dev/zero of=/dev/hda
```

But this wipes your entire hard drive! 

I just want to wipe 1 partition!

HI would it not be easier and safer with gparted?:guitar:

---

### Post by ageilers on 2007-07-09
Are you looking to clear the partition or you definitely want the data on that partition unrecoverable?

---

### Post by niteshifter on 2007-07-09
First thing: Identify the partition number:

```
sudo fdisk -l
```

Study the output **carefully** and locate the desired partion number. Write it down. 

Then use dd:

```
sudo dd if=/dev/zero of=/dev/hdaN
```

where N is the desired partition number.

Another bit of advice: Before doing stuff like this: **perform a full backup!**
I use partimage from the SystemRescueCD [http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page) - a handy tool to have around.

---

### Post by djhworld on 2007-07-09
Excellent thanks 'niteshifter', it worked a treat.

Edit: to tell you the truth, I was reinstalling Ubuntu and just wanted a "clean" partition to install it to.

---

### Post by az on 2007-07-09
> **djhworld said:**
> 
Edit: to tell you the truth, I was reinstalling Ubuntu and just wanted a "clean" partition to install it to.

You really don't need to do that, unless you want to try to remove some data that is still on the disk.

---

### Post by hyper_ch on 2007-07-10
I would use if=/dev/urandom but that will take a loooong time

---


---
title: "FSCK dies"
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by skymera on 2007-06-12
when i boot up
fsck died with exit status 8?
i push ctrl-d to continue

but it says to enter root pass for Maintenance..
i enter the pass and it says
sudo is not installed - it is
apt-get is not nistalled - it is

weird.
is this normal?
my machine runs perfect apart from every boot i have to push ctrl-d

is there a way to scrrenshot boot-up to make it clearer for you?

---

### Post by skymera on 2007-06-12
no one knows?

---

### Post by Inxsible on 2007-06-12
Put in your liveCD and perform a fsck on the drive that it fails on boot. Or mebbe do it on all the drives one by one.

My drive kept failing and I did the fsck via LiveCD and it said there was some error and asked if i wanted to fix it. I said "Hell Yeah" !

Well it did what it said it would, and i have had no complaints since then.

---

### Post by skymera on 2007-06-12
how odi perform that fsck?

this rele ticks me off....

i got plent of LiveCD's.....6

---

### Post by Inxsible on 2007-06-12
> **skymera said:**
> how odi perform that fsck?

this rele ticks me off....

i got plent of LiveCD's.....6 ummm..you open up a terminal by going to  Applications --> Accessories --> Terminal
and then type in ```
sudo fsck /dev/DEVICE_NAME
``` I am not sure, if you have to do a sudo on it. Replace DEVICE_NAME by the name of the drive for eg. hda1 or sda1 or sda2 etc.

---

### Post by skymera on 2007-06-12
right cheers!!!

---


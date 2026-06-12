---
title: "Can't boot into Kubuntu"
date: 2007-04-11
forum: Absolute Beginner Talk
---

### Post by boogachamp on 2007-04-11
Hey all.  I have dual booted between windows and kubuntu on a couple other machines, but am having trouble this time.

Using the live CD I installed Kubuntu so that my '/' partition was 15 gigs on my Master SATA drive and that '/home' and 'SWAP' would be on a slave ATA Drive.  When the install completed I restarted the computer and expected the grub screen to come up so I could select what I wanted to start up in.  To my surprise, windows just loaded.

I am using Windows XP 64-bit, don't know if that matters.

---

### Post by mand0 on 2007-04-11
Hrmmm, try entering into Kubuntu with the liveCD and then post the outputs of:

```
sudo fdisk -l
```
and
```
sudo gedit /boot/grub/menu.lst
```

Not sure if that will work.

---

### Post by boogachamp on 2007-04-11
will do, i will give it a try when I get home from work.

---

### Post by boogachamp on 2007-04-12
Apparently Updating my ASUS P5N-E SLI bios was all that I needed.  Very peculiar.

---


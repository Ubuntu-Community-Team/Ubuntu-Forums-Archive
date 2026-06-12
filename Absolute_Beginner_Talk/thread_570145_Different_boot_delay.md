---
title: "Different boot delay"
date: 2007-10-07
forum: Absolute Beginner Talk
---

### Post by elmo541992 on 2007-10-07
OK, so I have 64-bit feisty, and you know the Ubuntu splash screen that comes up during boot that looks like this:

[http://news.softpedia.com/images/reviews/large/installfeistyfawn-large_003.png](http://news.softpedia.com/images/reviews/large/installfeistyfawn-large_003.png)

Well, about 4/5 of the time, it hangs at 0% for around 2.5 minutes, then it boots like normal.  Aparently, this is occuring before the system log starts to record.  Could it be something wronge with the system log loading??? Its been doing this since a little after I got Ubuntu, and it's really annoying. How can i fix this???

---

### Post by Pumalite on 2007-10-07
Ubuntu is having trouble recognizing some of your hardware. It's everything working OK:?

---

### Post by wormser on 2007-10-07
You could remove the splash screen to get the details of the booting process.  This would let you see what is slowing it up.

```
sudo nano /boot/grub/menu.lst
```

Find the line of the kernel you are booting into and remove [COLOR="Red"]quiet splash[/COLOR] from the end.  This will remove the splash screen and let you see everything starting up.

> kernel /boot/vmlinuz-2.6.22-13-generic root=UUID=4d263fdd-a95b-4a8a-84c9-87f5bd71debd ro [COLOR="Red"]quiet splash[/COLOR]

---

### Post by elmo541992 on 2007-10-08
Wormser, that for some reason didn't work. However, I was able to boot in recovery mode
, and found where about it was freezing. So there was a bunch of code, then I get something kind of like the following (I did it a couple of times a wrote it down, so its not super accurate

ata1.01 qc timeout ...
ata1.01 Failed to set xfermove..
ata1.01 limiting speed to udma/3:pi03...
ata failed to recover some devices retry in 5 sec...
ata1.00 ata ... resize1:(random #s) sectors:(random #s)
ata1.00 ata ... resize1:(random #s) sectors:(random #s)

It repeated ^that^ whole thing about 3 or 4 times. Then, it said something like

ata disabled.

Then it boots normally. However, whenever it does this, I just noticed, My cd-rw drive doesn't work. I know there is nothing wrong with the drive; it works fine in windows, but only sometimes works in linux. Is there a way I can automatically disable ata or turn on an alternative? Also, my hard drive and cd-rw drive are on a single ide cable. Does this help any???

---

### Post by Pumalite on 2007-10-08
Make your CD-RW drive 2nd Master and set to 'Auto' in BIOS

---

### Post by elmo541992 on 2007-10-08
Can't, I only have one ide port; otherwise they would be on separate ports already.

---

### Post by om1 on 2007-10-08
it doesnt make since because it worked to install ubuntu
its probably something to do with your disk drive not being supported by 64 bit os

---

### Post by elmo541992 on 2007-10-08
I might be switching over to 32-bit soon anyway.

---

### Post by om1 on 2007-10-08
all 64 bit os's have issues at this time with hardware and software ..... at least from my experence and all the people i know anyway... i may be wrong though

---

### Post by elmo541992 on 2007-10-09
om1, you are not mistaken.

---


---
title: "How do I check free space on a drive?"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by grs on 2007-04-19
How do I check what free space I have on my hard drive?

---

### Post by Bachstelze on 2007-04-19
```
df -h
```

---

### Post by tenn on 2007-04-19
Nautilus (if you are using it) has in the bottom left corner a display of how much free space there is.

---

### Post by NicoleM on 2007-04-19
df -h if you're a command line person

also i'm sure there's an equivalent command to check disk space used (same info, different format) but the "file systems" tab of the system monitor is a nice visual for that as well

---

### Post by grs on 2007-04-19
Thanks, I found it in System Monitor and I got the command line as well.
When I did

df -h

I got 7 lines of information, only the first is what I was after, what are the other lines about?

---

### Post by Bachstelze on 2007-04-19
Could you paste what you get ? It depends very much on how your partitions are setup.

---

### Post by Rinzwind on 2007-04-19
> **grs said:**
> Thanks, I found it in System Monitor and I got the command line as well.
When I did

df -h

I got 7 lines of information, only the first is what I was after, what are the other lines about?
Those are your mounted directory's and discs (see the column 'mounted on')

---

### Post by Bachstelze on 2007-04-19
Not only. All the virtual filesystems linke devfs, tmpfs, shm and friends are also listed there.

---

### Post by grs on 2007-04-19
I got the following:

Filesystem            Size     Used    Avail     Use%   Mounted on

/dev/hda1            3.8G    2.3G    1.4G      63%    /

varrun                  252M   80K      252M      1%     /var/run

varlock                 252M       0      252M      0%      /var/lock

procbususb          10M      88K      10M       1%      /proc/bus/usb

udev                    10M      88K       10M      1%      /dev

devshm                252M       0       252M     0%      /dev/shm

lrm                        252M   18M      235M     7%      /lib/modules/2.6.17-11-generic/volatile


I kind of thought it may be to do with partitions

---

### Post by nickpaton on 2007-04-19
Applications>Accessories>Disk Usage Analyser

---

### Post by Bachstelze on 2007-04-19
grs > Nope, it has nothing to do with partitions. Those are virtual filesystems genereted by the kernel, they have nothing to do with partitions.

---


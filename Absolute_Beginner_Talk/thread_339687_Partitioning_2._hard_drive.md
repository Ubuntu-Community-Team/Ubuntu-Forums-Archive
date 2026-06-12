---
title: "Partitioning 2. hard drive"
date: 2007-01-16
forum: Absolute Beginner Talk
---

### Post by cmol on 2007-01-16
Hey

Just installed ubuntu for the first time on my computer.
I run my pc with 2 hard drives. A 10gb and a 30gb (master and slave).
So the ubuntu is on the 10gb.

But the 30gb runs NTFS, so how do I repartition the hard drive in to something linux can read?

ps. this is my first time on linux, so be easy on me ay? ;) 

Grats
Claus :-)

---

### Post by mikewhatever on 2007-01-16
Linux can read NTFS just fine. It can not write to it natively.

To repartition, you'd need Ubuntu LiveCD to run GParted partition manager, or you can download and burn GParted LiveCD from here: [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php). That in case you do not have Ubuntu LiveCD.

---

### Post by xyz on 2007-01-16
Some people, like me, user this HowTo. Back up your important data even your whole system even though I nerver ran into problems. Some people have though.
[HOWTO: NTFS with read/write support using the ntfs-3g (easy & safe method)]("http://www.ubuntuforums.org/showthread.php?t=217009")

---

### Post by cmol on 2007-01-18
What should i partition it in to?..

ext2?..

---

### Post by taurus on 2007-01-18
> **cmol said:**
> What should i partition it in to?..

ext2?..

ext3 would be better.

---

### Post by cmol on 2007-01-18
> **taurus said:**
> ext3 would be better.

What's the differens?

---

### Post by taurus on 2007-01-18
[http://iew3.technion.ac.il/CC/Comp_news/Mandrake_CMD_line/ch09s01.html](http://iew3.technion.ac.il/CC/Comp_news/Mandrake_CMD_line/ch09s01.html)

---

### Post by cmol on 2007-01-18
> **taurus said:**
> [http://iew3.technion.ac.il/CC/Comp_news/Mandrake_CMD_line/ch09s01.html](http://iew3.technion.ac.il/CC/Comp_news/Mandrake_CMD_line/ch09s01.html)

Thanks :)

Hmm.. It seams like i have run into a dead end..
I have repartitiond the hard drive (hdb) into ext3, and i pressed "Eject and reboot"..
But now nothing happens. The gparted program is closed. Can i force the computer into reboot from terminal?

---

### Post by taurus on 2007-01-18
```
shutdown -r now
(or sudo shutdown -r now)
```

---

### Post by cmol on 2007-01-18
> **taurus said:**
> ```
shutdown -r now
(or sudo shutdown -r now)
```

Great..

Ok.. I'll noob on.. Where can i se the drive?
As I wrote, i have a 10gb (the master), and a 30gb (the slave, and the one i just repartitioned).. I think I'm just looking the wrong place, but what to do?

---

### Post by taurus on 2007-01-18
What's the output of this command from a terminal?

```
sudo fdisk -l
```

---

### Post by cmol on 2007-01-18
> **taurus said:**
> What's the output of this command from a terminal?

```
sudo fdisk -l
```

It lists the 2 hard drives.

hda with the 3 system partitions, and hdb with one partition (linux).
The sizes matches the real.

Is there a way i graficly can access it?

---

### Post by cmol on 2007-01-19
> **taurus said:**
> What's the output of this command from a terminal?

```
sudo fdisk -l
```

Ok.. Found out i need to mount it.....
How to do that?

---

### Post by dak-AD on 2007-01-19
it might be a little late for this, but if you have two hdds, and you're using one for linux and one for windows, would it not make sence to partition a small area of the windows hdd as linux-swap, and a small area of the linux hdd as fat32 and set windows to use it as a page file?

that way, if you run out of ram, your computer will use the hdd that it's not allready accessing for paging.

---

### Post by cmol on 2007-01-19
> **dak-AD said:**
> it might be a little late for this, but if you have two hdds, and you're using one for linux and one for windows, would it not make sence to partition a small area of the windows hdd as linux-swap, and a small area of the linux hdd as fat32 and set windows to use it as a page file?

that way, if you run out of ram, your computer will use the hdd that it's not allready accessing for paging.

Think i would, but the machine ain't running windows.. Only Linux :-)

---


---
title: "Sudden Low Space"
date: 2007-09-27
forum: Absolute Beginner Talk
---

### Post by ralvynl on 2007-09-27
I dedicated my entire 40GB HDD to ubuntu fiesty fawn when I was installing, and all of a sudden - i have 181MB remaining. Please what is the problem?

---

### Post by ddrichardson on 2007-09-27
Can you post the output from a terminal of:```
sudo fdisk -l
```

---

### Post by ajgreeny on 2007-09-27
You could also install **filelight** and see what is taking up all the space in graphical mode.  It can be quite revealing!
There could be a load of stuff in root wastebasket if you have deleted anything from system files using **gksudo nautilus** as a graphical way of getting rid of anything.

---

### Post by Mr.Beast on 2007-09-27
> **ralvynl said:**
> I dedicated my entire 40GB HDD to ubuntu fiesty fawn when I was installing, and all of a sudden - i have 181MB remaining. Please what is the problem?

How much ram do you have, and are you sure you are looking at the right disk.
Ubuntu will kindly partition your disk for you and create swap partitions, and other lovely things for you.
you could be looking at space left on one of those, like maybe the boot volume?

---

### Post by P235 on 2007-09-27
```
df -Th
```

Enter the above command into a terminal to see how you have partitioned your hard drive and how much space has been used in each partition.

---

### Post by vinnn on 2007-09-30
See the size of each directory with...
```
du -sh /*
```

Or you could have a look for any files on your system over 1GB...
```
find / -size +1G
```

Or maybe any files in your home directory created within the last 2 days over 10MB...
```
find /home -ctime -2 -size +10M
```

---


---
title: "permanently mounting a second hard drive"
date: 2008-04-15
forum: Absolute Beginner Talk
---

### Post by rockerphil on 2008-04-15
ok, i have been running Fluxbuntu Gutsy Gibosn for about 6 months now and am loving it. my  problem is this. i have a 2nd hard drive on my system, i know how to temporarily mount it to my file system, but i don't know how to permanently mount it. it's an NTFS file system and i really don't want to repartition it to an ext2 partition since it has all my family photos on it and i don't currently have a CD burner. i can temp mount it by running sudo mount /dev/sdb2 /home/phil/Media in terminal, but like i said, i don't know how to permanently mount it and i have done some extensive reading on the web and have not found what i'm looking for. so if someone could please post the terminal command to permanently mount the hard drive it would be much appreciated. thanx

---

### Post by cm.squared on 2008-04-15
Type the following into your terminal:
```
gksudo gedit /etc/fstab
```
Then paste the following line at the end of the file:
```
/dev/sdb2 /home/phil/Media auto defaults 0 0
```
And then save.

That should do the trick.  You might consider copying the pictures onto the first harddrive and then reformatting the second drive since linux deals with ext2/3 filesystems better than ntfs, but if this work fine then it's up to you.

---

### Post by joshrobinson on 2008-04-15
if your new at editing config files, you should make a backup before you make changes

```
sudo cp /etc/fstab /etc/fstab.backup
```

---

### Post by cm.squared on 2008-04-15
Good call joshrobinson.

---

### Post by rockerphil on 2008-04-15
joshrobinson, i'm not new to editing config files, and mc.squared, thanx, it worked perfect;y, i just rebooted and it auto mounts

---


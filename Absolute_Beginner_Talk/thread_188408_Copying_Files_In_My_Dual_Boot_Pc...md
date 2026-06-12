---
title: "Copying Files In My Dual Boot Pc.."
date: 2006-06-04
forum: Absolute Beginner Talk
---

### Post by berong on 2006-06-04
my Ubuntu installation is a success on my Pc with a win XP. Now i have a dual boot PC. im excited to use the different apps on this new OS. but  i can't access my files on my win XP.. is there any way to acces my files on my XP?? 



___________________
NewBie isMe

---

### Post by TrendyDark on 2006-06-04
For one, if you're going to try installing windows applications on Ubuntu, it won't work, without Wine or something else.

As for accessing your windows files, you can't really do much with them from Ubuntu unless you have a FAT32 partition for Windows.

---

### Post by aysiu on 2006-06-04
You can access NTFS, but it'll be read-only:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by [S|G] on 2006-06-04
Hello, you can access your files, even if your drive is NTFS. However, if it is, you'll only be able to read them (not change them).  In order to help you, we need to know what is the partition that you have windows installed on. If you don't know, do this:
```

sudo fdisk /dev/hda -l

```

This will list your partitions on your primary master hard drive. Copy and paste the output here so we can help :)

Edit: Follow aysiu's guide, that should be pretty complete. If you run into any problems, just tell us.

---

### Post by berong on 2006-06-04
[QUOTE=TrendyDark]For one, if you're going to try installing windows applications on Ubuntu, it won't work, without Wine or something else.

As for accessing your windows files, you can't really do much with them from Ubuntu unless you have a FAT32 partition for Windows.[/QUOTE]

i juz wanna move my pictures and Mp3 music from Win XP partition to Ubuntu partition.. my Win Xp is fat 32 partition.. i don't have a removable storage device so that  ill just gonna copy my files in xp and boot to Ubuntu then paste it..



______________________
neWbie isMe

---

### Post by berong on 2006-06-04
[QUOTE=aysiu]You can access NTFS, but it'll be read-only:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)[/QUOTE]


oh geez.. thanks.. what a big help... i'll do it right away.. thank you again




__________________
neWbie isMe

---


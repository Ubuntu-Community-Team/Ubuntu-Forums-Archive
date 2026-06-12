---
title: "Partition mount points"
date: 2008-03-25
forum: Absolute Beginner Talk
---

### Post by hungryOrb on 2008-03-25
Hello Ppl!
SOrry for the fact that I dont have much time to search for this answer, but i'd be happy if someone could help ;D
Just wondering what the exact names including special characters are of each needed partition?
I know currently /home, and /, for root. What about swap? and is there another partition I need?

THanks if any help ;D

---

### Post by Diabolis on 2008-03-25
What are you trying to do exactly?

you can see all your disks information with: sudo fdisk -ul

---

### Post by mali2297 on 2008-03-25
You need / and swap, that's all. (/home etc are optional.)

---

### Post by forrestcupp on 2008-03-25
root '/', /home, and a swap should be sufficient.  Some people go crazy with partitions, but I don't see the point.  You shouldn't need more than 512 megs for swap.

And you don't even have to have /home.  It's just useful if you want to reinstall your OS and keep your personal files and settings.

---

### Post by Paqman on 2008-03-25
The only partition you *really* need is root.

However, almost all Linux installs also have a swap partition. Swap functions as virtual memory (like the Windows page file). If you have more RAM than can use, swap won't be touched. It's also used to suspend, which is why it's recommended for your swap to be at least as big as your RAM.

A separate /home partition isn't required, but is very handy. The advantage of mounting /home on a separate partition is that it allows you to format / and reinstall without touching all your preferences and settings that are stored in /home.

---


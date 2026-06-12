---
title: "Partition"
date: 2007-11-10
forum: Absolute Beginner Talk
---

### Post by BlueEight on 2007-11-10
I need to make an XP partition on my computer, since I can't find any drivers for my printer. How would I make 3 partitions, one for Ubuntu(the minimum it currently requires), one for XP(minimum it requires), and one for both ubuntu to share? Does anyone know how much XP requires? Thanks.

---

### Post by creeco on 2007-11-10
What printer do you have?

---

### Post by rsambuca on 2007-11-10
What printer do you have?

---

### Post by Botondus on 2007-11-10
You need to give a bit more info to get some useful feedback. First of all what's your current partition configuration?
Type in terminal:

```
sudo fdisk -l
```

And post here the output of that.

---

### Post by Bartender on 2007-11-10
Generally speaking, it's easier (at least it was several months ago, last time I tried to do this sort of thing) to install XP first.  Then toss in the LiveCD or alternate install CD and let Ubuntu create the partitions you need.  hermanzone and psychocats websites give ideas for partitioning plans.  If I were making room for XP, I'd probly set aside at least 15GB or so.  XP only NEEDS a coupla GB's for a basic install but you know how the thing grows and mutates.

---


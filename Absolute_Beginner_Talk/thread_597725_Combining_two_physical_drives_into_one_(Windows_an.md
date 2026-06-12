---
title: "Combining two physical drives into one (Windows and Ubuntu)"
date: 2007-10-30
forum: Absolute Beginner Talk
---

### Post by jdrysdale on 2007-10-30
Its a long story but bear with me,,,Dell inspiron, intially loaded with windows on a nice travelstar 20g drive bought on buyandsell works lovely. To avoid pain while playing with ubuntu,I swapped HD with a 20g from a portable unit and installed 7.04 from the alternate disk (live disk wont do). Happy days. 
Bought 120g HD and tried to install 7.10 from scratch from the live then the alt disk no good, installed 7.04 from alt OK and upgraded from live 7.10 no good. 
Using the dd function overwrote all the stuff on ext1 with 0 but stopped it at 6g then did a full format. Using dd again I copied my 20g ubuntu drive over to the 120g and happy days,,except:
Partition manager sees a 120 g drive 70% full and map drive sees a 13g drive 3/4 full. But never mind it works.
What I want to do is this,, I still use windows for php development work and as a result end up physically swapping drives, not good. Can I just dd my windows HD onto a partition that I'll make on the 120g harddrive using ubuntu partition manager???
Thanks for reading my long story and your help.

---

### Post by scrooge_74 on 2007-10-30
I kind of got lost in the process, but  any way I will give it a shot.

You can use Gparted to make another partition on that drive and have both Ubuntu and windows in the same drive, then you can use ntfs-3g to read the Windows side of the disk from inside Ubuntu.  Stay with 7.04 until you get things sorted out to avoid further troubles since Gutsy have been difficult to some. 

I for myself only have one PC with Dapper and the rest went to Etch to avoid further headaches.

---


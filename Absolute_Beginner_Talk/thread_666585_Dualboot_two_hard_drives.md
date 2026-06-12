---
title: "Dualboot two hard drives"
date: 2008-01-13
forum: Absolute Beginner Talk
---

### Post by Mark_in_Hollywood on 2008-01-13
I've looked over Tips & Tutorials for booting with two hard drives, read:

[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902) and the info at:

[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

I'm ready to do this on a neighbor's computer. I'm donating a 20 gig drive for Ubuntu. He has a 40gig drive with Windows ME (that's Millenium Edition for those of you who have forgotten this).

My question is this:

Where I use gedit to edit menu.lst, do I MERELY substitute at the title: Windows ME? Or does it get called Millenium Edition or WHAT?

I really can't afford to get this guy angry when his old hard disk won't work. He's in his 70s and kinda stubborn.

title              Windows XP
root               (hd1,0)
savedefault
makeactive
map                (hd0) (hd1)
map                (hd1) (hd0)
chainloader        +1


anybody out there got practical experience with ME?

---

### Post by EXCiD3 on 2008-01-13
Doesnt matter actually. The "title" is just the text that is displayed in Grub's boot menu for you to know which OS its going to boot.

If you have Windows still installed, Grub may automatically detect and add the option itself. This worked with dual booting Xp and Ubuntu on my laptop that has 2 hdd's.

---


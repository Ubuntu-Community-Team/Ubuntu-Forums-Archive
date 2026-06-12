---
title: "Major blooper. Really need help now."
date: 2007-07-10
forum: Absolute Beginner Talk
---

### Post by czepluch on 2007-07-10
Hi guys. I jsut found out that i've done a major blooper. I'm dual booting and using both XP and ubuntu. Mostly ubuntu though, but then (here comes the big blooper) i needed space on my ubuntu drive, and dum as i am i thought i could make a new partition in ext3 format and then i took some disk space from my NTFS drive, that i was using to view my documents in both ubuntu and xp, and made it into a ext3 partition and set it as /home. And now i cant use the new /home drive and i found out after thinking it through that i could just had used the ntfs drive for the files that there were no space for in the ubuntu drive. ( I know it really dumm, and a major blooper) So now I've got 40gb og free unused space that i would like to make back into ntfs so that i can use it in both xp and ubuntu. Can anyone please tell me how to do that. I would really apreciate the help cause now im all torn up after realizing my blooper. :(

Thanks for helping.

-Jacob

---

### Post by orb9220 on 2007-07-10
> So now I've got 40gb og free unused space that i would like to make back into ntfs so that i can use it in both xp and ubuntu.

If it is just free space you can boot into xp and run Disk management in admin tools. There you can just right-click free partition and create partition and format.

---

### Post by macogw on 2007-07-10
Actually ext3 might be a better plan since it doesn't get fragmented.  No more defragging....yay!  There are drivers for ext2/ext3 for XP (though not for Vista) here: [http://fs-driver.org](http://fs-driver.org)

---


---
title: "What files system to format in?"
date: 2006-12-11
forum: Absolute Beginner Talk
---

### Post by Cabldevil on 2006-12-11
I have just deleted my MS partitions and OS!!!!! Now I have to repartition and format my non OS drives. ](*,) It have been 5 years since I had to do this on a file server.   I know there is at least 3 new file systems that go past the ext3. 
What is the best file system to use. I have about 800 gigs to format and it will be used for larger files. I would also like to keep it compatible with LVM.

Thank you in advance.

---

### Post by taurus on 2006-12-11
ext3.

---

### Post by Cabldevil on 2006-12-11
Im surprised you would not sudjest the other 2 filesystems  are they not stable or slower?

---

### Post by taurus on 2006-12-11
What other 2 filesystems?  Are you talking about reiserfs & xjf (or whatever it's called)?

---

### Post by Bachstelze on 2006-12-11
What will be the use of all that diskspace ?

---

### Post by thomashauk on 2006-12-11
reiserfs i best for lots of small files, like config files since it can pack more than one file into a block.

But you want big files so...

---

### Post by Cabldevil on 2006-12-11
Yea I ment xjf and reiserf.  Buit yes the majority of the harddrives with be used for larg files over 10meg each.  So it sould like good old ext3 it is.

---

### Post by Bachstelze on 2006-12-11
If it's just for data storage, you could even go with ext2. I don't think you'll need the journaling anyway.

---


---
title: "resizing ext 3"
date: 2007-08-08
forum: Absolute Beginner Talk
---

### Post by dhani99 on 2007-08-08
SO some ppl may know that i have left some space for Windows partittion and now i do not want windows... so i want to add that space to linux, how do i do that !!

---

### Post by oilchangeguy on 2007-08-08
> **dhani99 said:**
> SO some ppl may know that i have left some space for Windows partittion and now i do not want windows... so i want to add that space to linux, how do i do that !!

you can run the live cd, and use gparted to resize the linux partition.

---

### Post by dhani99 on 2007-08-08
i installed gparted from add remove but resizing is disabled.. i can't do ... that...

---

### Post by bashologist on 2007-08-08
In some cases like if you remove a windows recovery partition it's might not be possible to restore windows back to a working state, so make sure you'll never need it again.

Do you really need the extra space? Resizing isn't really a good idea unless you're willing to risk losing all your data on that partition; maybe creating a new ext3 partition would be better?

---

### Post by dhani99 on 2007-08-08
like locked sign beside ext 3 and swap partition..


> Do you really need the extra space? Resizing isn't really a good idea unless you're willing to risk losing all your data on that partition; maybe creating a new ext3 partition would be better?

okay so i create new ext3 partition but i also have swap partition about 1.gb  but i don't see that in a home folder how does it work, where it is !! 
and why to create Swap partition !

---

### Post by Pronco on 2007-08-08
You've created a new ext3 partition.

did you mount the new partition into the appropriate mount point ?

Creating a swap partition would definietly be benefitical for your system performance.

Thank you.

---


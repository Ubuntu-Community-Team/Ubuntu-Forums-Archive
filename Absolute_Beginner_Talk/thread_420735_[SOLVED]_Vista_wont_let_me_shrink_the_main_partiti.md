---
title: "[SOLVED] Vista wont let me shrink the main partition below 24GB"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by Inxsible on 2007-04-23
i was trying to shrink the partition in Vista and it wouldn't let me shrink below 24 GB !!!
 
Does Vista take and need all that friggin' space ?
 
HP has reserved another 7GB of space for recovery. Also, I have to keep some space for installing Windows stuff. So effectively it reduces the space I had planned for Ubuntu  ](*,)

---

### Post by LaurelLynn on 2007-04-23
Dear Inxsible,

Two problems with shrinking Windows partitions.  

First resizing the partition will only work with unused space at the end of the partition. So you have to defragment it first to get the most possible space.

Second,  Window keeps a second copy of its file directory at the center of the partition. So, you will probably not be able to resize it to less than half its original size.

You might try defragging again AFTER the first resize.  Then you might be able to resize again.

---

### Post by Inxsible on 2007-04-23
I did defrag it before the resize. I guess i will now defrag the C: drive again and try a resize yet again

---

### Post by LaurelLynn on 2007-04-23
Good luck, I´ll keep my fingers crossed.

The fundamental problem is that windows always puts the two copies of the filesystem at places physically far apart so that damage to one track doesn´t loose all files. It will never defrag everything to the bottom of the partition.

---

### Post by Inxsible on 2007-04-24
Windows doesnt wanna play ball !!
 
the 24GB partition that i made for windows still shows 7.7GB as free space but wont let me shrink it any further. i have defragged it a couple of times now. Also i cannot resize the HP recovery partition that HP has put in.
 
Crappy Windows !!

---


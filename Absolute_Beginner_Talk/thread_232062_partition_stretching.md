---
title: "partition stretching"
date: 2006-08-08
forum: Absolute Beginner Talk
---

### Post by carverj on 2006-08-08
Hi everyone,
             Just wondering if it is possible to increase the size
of my primary ntfs XP partition to fit visual studio. So were talking extending the first 10 G partition to 15 G, thereby squashing the remaining
4 or so reamaining logical Ubuntu partitions from the current size of 30 G
to 25 G.
 I tried to do this with the Dapper CD I d/led but I couldn't seem to accomplish this task!!?
Which tool will accomplish this?
Thanks team
____________
Imagine the entire universe was just one microscopic cell in a 
greater organism.... hmmm hehe [-o<

---

### Post by em3raldxiii on 2006-08-08
I am not entirely certain that Linux utilities have the capability of increasing the size of an NTFS partition ...... though I don't know this for sure.
 
On the other hand, I DO know that Partition Magic knows how to handle EXT3 as well as NTFS, so you could use it.  Unfortunately, Part Magic was developed by Symantec, and Symantec is ALMOST as evil as Microsoft haha.
 
If I come across any fixes for ya, I'll let you know.

---

### Post by louistan3 on 2006-08-08
maybe you could try gparted.. i think it supports ntfs too..

---

### Post by em3raldxiii on 2006-08-08
supports, yes ... but *increase*?  I know it can shrink it ... if I was at home I could check :/ (I suppose there's probably a man page for it)

---

### Post by carverj on 2006-08-08
hmm this page [http://gparted.sourceforge.net/screenshots.php](http://gparted.sourceforge.net/screenshots.php)
seems to be saying that gparted will "grow" and ntfs
partition, but as I said, I couldn't do this with my 
Dapper install disk.... the resize widget would only resize to 
a smaller size, not any larger.
Has anyone grown an XP partition before or is formatting and 
reinstalling both XP and Ubuntu from scratch my only option
this is highly undesirable as I have no Office 2003 CD to reinstall.

---

### Post by Hillbilly Tilley on 2006-08-08
I am having the same problem, and tried the same solution as you did with the same results.

---

### Post by carverj on 2006-08-08
Well, tried to use partition magic to grow my XP partition to no avail
It (partition magic) complained with a 106 (or something) error, stating that it cuoldn't find the first partition (basically it just failed to load because of some configuration I have or a bug)
Any help?

---


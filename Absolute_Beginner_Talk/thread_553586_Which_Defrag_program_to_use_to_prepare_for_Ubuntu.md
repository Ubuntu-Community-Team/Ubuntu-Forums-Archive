---
title: "Which Defrag program to use to prepare for Ubuntu?"
date: 2007-09-17
forum: Absolute Beginner Talk
---

### Post by mshadow818@msn.com on 2007-09-17
I guess this might technically be a Windows XP question but I had heard that before installing Ubuntu it was a good idea to run a diskcheck and to defrag your hard drive.  
My question is this: 
What is the best defrag program to use before installing Ubuntu? 
It considered common knowledge that the built in defrag program with Windows XP is not the best but I am not sure which of the alternatives, if any, would benefit a subsequent Linux installation.

---

### Post by atbnet on 2007-09-17
The XP defrag program is good enough for this purpose. The previous versions of the defrag program weren't as good, but XP's is a lite version of Disk Keeper.

---

### Post by misfitpierce on 2007-09-18
XP's is fine... only need defrag if keeping windows on partition as well as ubuntu. You must also keep defragged or it can cause problems to ubuntu partition. If just installing 100% ubuntu defrag is not really necessary.

---

### Post by mshadow818@msn.com on 2007-09-18
> **misfitpierce said:**
> XP's is fine... only need defrag if keeping windows on partition as well as ubuntu. You must also keep defragged or it can cause problems to ubuntu partition. If just installing 100% ubuntu defrag is not really necessary.
This is the first I've heard of this.  What type of problems can it cause?  

Also, everyone so far thinks that the XP version of defrag will work just fine.  Is there any reason NOT to use another program if I already have it?

---

### Post by splintercellguy on 2007-09-18
I don't believe there is any issue with NTFS fragmentation interfering with Ubuntu. Whatever defrag program works I suppose.

---

### Post by curiousnoob on 2007-09-18
> **misfitpierce said:**
> XP's is fine... only need defrag if keeping windows on partition as well as ubuntu. You must also keep defragged or it can cause problems to ubuntu partition. If just installing 100% ubuntu defrag is not really necessary.
Do you run into problems if the partition with Windows fills up?  If so how much free space should you leave on the Windows partition?

---

### Post by Daveth on 2007-09-18
my understanding is that to re-partition a windows partition then the files it contains should be defragged. Otherwise it is trying to move over space where bits of files reside and the partitioner cannot move them them out of the way. I used to use a free and old demo version of Diskeeper, which I still pass onto friends as it was heaps faster than the XP one. What happens in adjacent partitions is largely irrelevant to the partition next door to it.

---

### Post by splintercellguy on 2007-09-18
Defragging is not required anymore, according to the ntfsresize man page: [http://man.linux-ntfs.org/ntfsresize.8.html](http://man.linux-ntfs.org/ntfsresize.8.html)

---

### Post by Daveth on 2007-09-18
that's useful info but only applies if your partitioning takes place outside of XP; [email]mshadow818@msn.com[/email] may do what I did and partition from inside XP in preparation for an Ubuntu install. But now he knows all the options:)

---


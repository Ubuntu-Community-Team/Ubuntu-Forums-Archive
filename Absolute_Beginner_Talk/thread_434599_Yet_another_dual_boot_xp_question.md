---
title: "Yet another dual boot xp question"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by the lemming on 2007-05-06
Hello

I was just about to take the plunge and install 7.04 when I got the screen about formatting the drives and paniced.

My computer has two hard drives.  The first one will be for the operating systems and the second drive will be for storage.  Both drives are 112gb and all of them are NTFS.

My first drive, which is where my Umbutu will hopefully go, has three partitions:

the first partition is XP  16.5gb
The second partition is for umbutu 10gb
The third is storage at 54gb

Should I re-join the second and third partitions and start my install from there or can I install into the 10gb partition?
I have to admit that I was completely confused by the whole process and would greatly appreciate an Idiot's Guide in how to proceed.

Cheers

---

### Post by the lemming on 2007-05-06
Got my sums wrong

Partition 1         16.5gb
Partition 2         9.99gb (Can be changed)
Partition 3         85.2gb (can be changed)

---

### Post by overdrank on 2007-05-06
> **the lemming said:**
> Hello

I was just about to take the plunge and install 7.04 when I got the screen about formatting the drives and paniced.

My computer has two hard drives.  The first one will be for the operating systems and the second drive will be for storage.  Both drives are 112gb and all of them are NTFS.

My first drive, which is where my Umbutu will hopefully go, has three partitions:

the first partition is XP  16.5gb
The second partition is for umbutu 10gb
The third is storage at 54gb

Should I re-join the second and third partitions and start my install from there or can I install into the 10gb partition?
I have to admit that I was completely confused by the whole process and would greatly appreciate an Idiot's Guide in how to proceed.

Cheers

Hi you can choose the 10gb partition, you just select manual partition and choose it. But you will have to make a swap partition also form your storage partition. Good luck! :)

---

### Post by Cappy on 2007-05-06
There is also a ubuntu "windows installer" if you decide to give up on the partitioning.
[http://www.cutlersoftware.com/ubuntusetup/wubi/en-US/index.html](http://www.cutlersoftware.com/ubuntusetup/wubi/en-US/index.html)

---

### Post by the lemming on 2007-05-06
> **paul capps said:**
> Hi you can choose the 10gb partition, you just select manual partition and choose it. But you will have to make a swap partition also form your storage partition. Good luck! :)


And that is where I got confused.  I did not understand what I was looking at.  And as a result I got some error messages.

Any suggestions would be most appreciated

---

### Post by overdrank on 2007-05-06
> **the lemming said:**
> And that is where I got confused.  I did not understand what I was looking at.  And as a result I got some error messages.

Any suggestions would be most appreciated

Do you recall the error message? If all else fails use gparted to delete the partitions already in place except for your windows and then create the partitions that you like. But you will have to create a swap partition for linux and windows. This link may help.
[http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)
Hope this helps good luck.

---


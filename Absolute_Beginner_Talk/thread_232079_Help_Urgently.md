---
title: "Help Urgently"
date: 2006-08-08
forum: Absolute Beginner Talk
---

### Post by jesus of suburbia on 2006-08-08
hello ubuntu people, i am new to the system, in fact i have only just heard about linux being free a week ago. I have 3 hard drives, one has windows on it. I want to install linux to a different hard drive(meaning i wont need to partition it off from windows) how do i do this without affecting windows????Thanks in advance!!!!:KS

---

### Post by jesus of suburbia on 2006-08-08
Please reply

---

### Post by Tomosaur on 2006-08-08
During the installation procedure, a program called gparted will start which will allow you to edit your hard drives/partitions/filesysems. You'll need to format your chosen hard drive to either ext2 or ext3 (your choice), but leave a small amount of space (traditionally, double your RAM) to format as 'swap'. After this, you will be asked where you want to install to. Normally it should guess automatically, but double check that it's installing onto the correct hard drive (it should do, if that's the only one with ext2 or ext3 filesystem).

---

### Post by xpod on 2006-08-08
When i installed on slave dh it done all the partitioning (and formatting)automatically.

All i had to chose was which disk  i.e /dev/hda OR dev/hdb.

If i remember correctly once you click the install icon you chose what disk on section 5(?) of the install procedure after youve entered all your persoanal details and country etc in stages 1-4.

Stage 6 finally installs after you chose where you want to install to plus it`s all set up to dualboot automatically as well if it`s a slave hd your putting it on.

---

### Post by jesus of suburbia on 2006-08-08
thank you very much

---

### Post by MetalMusicAddict on 2006-08-08
> **jesus of suburbia said:**
> Please reply
Please dont bump a thread 10 mins later. Please, instead, try searching the forum. There are many threads like yours with a wealth of knowlege in them.

---


---
title: "Configure disk utility failure"
date: 2006-07-31
forum: Absolute Beginner Talk
---

### Post by PaulFXH on 2006-07-31
Hi
I have tried to use System->Administration->Disk a number of times without success.
I always get the following error:"The Application "disks-admin" has quit unexpectedly."
Does this work for anybody and, if so, what do I have to do to get it to function here?

Thanks 
Paul

---

### Post by OU812 on 2006-08-01
Sorry, I did not get that error. I opened it, clicked every drive and every tab, but no crashes.

john

---

### Post by PaulFXH on 2006-08-01
Hi John
Thanks for the reply.
OK, so it looks like I've got a problem.
Perhaps my copy of disks-admin is either corrupted or is not there at all.
So, I tried to downoad it in Synaptic but a search does not find any package with this name.
Make any sense to anybody?

Paul

---

### Post by OU812 on 2006-08-04
Is there perhaps a problem with your fstab?

john

---

### Post by eXisor on 2006-08-04
It sounds like 'disks-admin' is finding something it can't handle.
Post the contents of your /etc/fstab, and maybe try force a check of your disks on the next boot. Type 'man e2fsck' or 'man fsck' to see which command will do that. (Sorry I can't remember and am on a xp box at the moment.

---

### Post by PaulFXH on 2006-08-04
Thanks for the replies.

However, I have the impression that the package disks-admin just is not present on my computer.
This thread confirms that:
[http://www.ubuntuforums.org/showthread.php?t=224276&highlight=disks-admin](http://www.ubuntuforums.org/showthread.php?t=224276&highlight=disks-admin)

Nevertheless, I use System Monitor to keep a check on how much of my various disks (partitions) are actually being used. The only thing I'm missing is the possibility to one-click mount a disk.
But there are many ways to skin a cat............

Paul

---


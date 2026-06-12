---
title: "Delete partition using Qtparted"
date: 2007-04-07
forum: Absolute Beginner Talk
---

### Post by Jubufreak on 2007-04-07
Hi everyone...
 I have a small problem...because i m using ubuntu on VMware, and i managed to increase virtual disk space for ubuntu...but when i run ubuntu i only see space that i alocated when i installed it...

So to try to change this...i installed Qtparted to add this new free space to existing disk...but i dont know...i only manged to sort of do a new partition out of that free space...but i really wanted to add that free space to an existing partition...damn how can i repair that...
And when i run Qtparted in terminal window i get the following message and althought it startes the program i cannot do nothing with it(?)

root@myUbuntu-desktop:/home/myUbuntu# X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
Error: File system was not cleanly unmounted!  You should run e2fsck.  Modifying an unclean file system could cause severe corruption.

---

### Post by siciliancasanova on 2007-04-07
Download the live disk for [Gparted]("gparted.sourceforge.net/livecd.php"), and try using it.

---

### Post by siciliancasanova on 2007-04-07
Wait a second.  Your virtualizing ubuntu?  You might want to go into exactly how you have this working unless a lot of other people use this.  I went to their website and hmm yeah I haven't worked with it before so nevermind my above statement.

---

### Post by antoz on 2007-04-07
You should be able to resize your partition by using the live Ubuntu CD it has Gparted on it. Provided there is free space at the end of the partition You simply right click on the partition you want to enlarge and then rezise. I am not sure but I think you can only add at the end not at the beginning.

---

### Post by siciliancasanova on 2007-04-07
> **antoz said:**
> You should be able to resize your partition by using the live Ubuntu CD it has Gparted on it. Provided there is free space at the end of the partition You simply right click on the partition you want to enlarge and then rezise. I am not sure but I think you can only add at the end not at the beginning.

I would still recommend not using the gparted version that comes inside of ubuntu.  Unless you are in a hurry, you have much more control by using the live disk of gparted.

---

### Post by Jubufreak on 2007-04-07
Thnx that did the trick...great tool by the way :-D well thnx again

---

### Post by siciliancasanova on 2007-04-07
Glad to see it worked for you.  :)

---


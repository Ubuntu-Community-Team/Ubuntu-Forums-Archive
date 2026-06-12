---
title: "Transferring Data from Mac to Ubuntu"
date: 2011-04-29
forum: Apple Hardware Users
---

### Post by ron177 on 2011-04-29
Dear all,

I have been trying to transfer a large amount of data from an external HD formated for Mac OS X to another external formated ext4. While more than half of the material has been quite easily transferred, there are folders for which the system tells me I do not have "permissions" for the transfer. These are the folders that I cannot even view them from a Linux platform. 

This is really a strange problem because I created all the folders myself and I had never changed the permissions of any. I cannot understand why some are viewed and transferred in Ubuntu and others not. Is there anyway I can resolve this problem? The data is quite large (around 1 TB) and I want to transfer everything to an ext4 HD in order to sell my iMac. Please do respond if you know of a way -- preferably an easy way -- to address this problem.

Appreciatively,

Ron

---

### Post by JohnAtilano on 2011-05-01
Hi Ron.

Do the permissions differ between the directories/files that transferred ok and those that didn't?  I suspect that may be the problem.

You could try changing the permissions to the problem directories and files.

[chmod]("http://developer.apple.com/library/mac/#documentation/Darwin/Reference/ManPages/man1/chmod.1.html") in Terminal could be used to do this.

---

### Post by ron177 on 2011-05-01
This problem has been resolved by a response I received from another forum:

How are you attempting to perform the copy? You may want to try  running the application you're using for copying the files as root. So,  if it's the regular file browser, you can do this by pressing Alt+F2 and  running:
 gksu nautilus
 Then try doing the copy. The files might have the wrong permissions  when they arrive on the destination ext4 drive, but you can always  change that.

---


---
title: "duplicat of bad block in use"
date: 2007-08-22
forum: Absolute Beginner Talk
---

### Post by llzero1337 on 2007-08-22
when i load up the computer lubuntu gives me this errors here a pics 
my HDD specs
200gb maxtor with XP 
120gb Ubuntu

---

### Post by PacketCollision on 2007-08-22
Like the error message says, your disk has errors.  If startup drops you to a command prompt, or if you can get to one, try:
```
fsck -r /dev/hdb1
```

Note that fsck could mess with your data if used incorrectly, so standard disclaimer applies.

---

### Post by llzero1337 on 2007-08-22
does it matter if the linux is the 2nd or first hdd cos im not to sure should i just unplug my windows one then?

---

### Post by llzero1337 on 2007-08-22
help

---

### Post by splintercellguy on 2007-08-22
Boot to a LiveCD then post the output of fdisk -l. You would do fsck /dev/<the device containing Linux>.

---

### Post by llzero1337 on 2007-08-22
how do i tell what device the linux one is?

---

### Post by &lt;&lt;joe&gt;&gt; on 2007-08-22
> **llzero1337 said:**
> how do i tell what device the linux one is?

after you boot the live cd 
one way to tell would be 
click install  Dont worry were not going to install
when you get to the part asking how you would like to partion say manualy
then you Ubuntu should be installed on the partion that is ext3 then caccle the install

i am shur there is a better way but i dont know it

---

### Post by expatCM on 2007-08-22
Yes but did this error message not appear as a result of an automatic check being forced on one of your drives when you booted?

If it did, the error message is because a problem was found which could not be automatically fixed. 

If you leave the process alone it will terminate with a detailed message on screen and a command prompt.  There is not a lot you can do at the command prompt here but the message tells you to enter fsck manually and then follow through the prompts on screen.  This in effect manually fixes the problem for you ....   There is no need to select a drive since the system knows already which drive has the problem...

---

### Post by llzero1337 on 2007-08-23
so i just type on fsck then

---

### Post by llzero1337 on 2007-08-23
> ubuntu@ubuntu:~$ fsck -r /dev/hdb1
fsck 1.40-WIP (14-Nov-2006)
e2fsck 1.40-WIP (14-Nov-2006)
fsck.ext2: Permission denied while trying to open /dev/hdb1
You must have r/w access to the filesystem or be root
ubuntu@ubuntu:~$ 



this is what i get

---

### Post by expatCM on 2007-08-23
You may want to read what the instructions on screen ask you to do.   I am surprised that you got the message since that suggests that you are not root but I thought that the prompt was root.

However, sudo fsck may help you out.

---


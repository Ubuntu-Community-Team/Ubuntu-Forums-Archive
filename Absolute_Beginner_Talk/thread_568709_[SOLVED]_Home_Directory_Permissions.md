---
title: "[SOLVED] Home Directory Permissions"
date: 2007-10-06
forum: Absolute Beginner Talk
---

### Post by AlanRogers on 2007-10-06
Chaps

I try not to come cap in hand too often but I'm stumped by this one. Here's the story:

I have a machine that I play with Linux on, various distros over the last few months. It has two physical hard drives, my retained data being on the second.

I've just installed 7.04 to hda1, mounting hda2 as /home. Up til now, I've mounted hdb1 as /home but this time I made it a little different; I mounted hdb1 as ~/home and hdb2 as ~/work

I can access ~/work just fine but I can't access ~/home/apr, where all my previous customisations are. I get permission denied.

So far, I've tried
```
sudo chown -vfR apr:apr ~/home/apr/
```and
```
sudo chmod -vfR 0771 /home/apr/home/apr/*
```but no dice.

I know I'm missing something very basic but I can't see for the life of me what it is. Assistance for the blind and stupid very much appreciated.

---

### Post by ronocdh on 2007-10-06
If CLI permissions changes don't seem to be doing the trick, you could always run *sudo nautilus*, navigate to the directory in question, then modify the permissions there via the GUI. It's a clumsy way of doing it, but I've been in this position many times. Probably a simple syntax slip-up or something... Good luck!

---

### Post by philinux on 2007-10-06
After chown it needs your userid before anything else

e.g. sudo chown kennyg - etc etc

good guide here saved my bacon [http://www.linuxcommand.org/learning_the_shell.php](http://www.linuxcommand.org/learning_the_shell.php)

---

### Post by AlanRogers on 2007-10-06
Unfortunately, neither solution worked, although ```
sudo nautilus
``` did enable me to copy the files into the ~ folder. Exploration continues ...

---

### Post by steve.horsley on 2007-10-06
I can see that if your user ID is different between the two systems then your old home stuff might not be readable in the new system. But I would expect chown to work. Is is possible that the partition has been mounted read-only? Check with the **mount** command. IF the partition is mounted readonly, it will have "ro" against it.

---

### Post by AlanRogers on 2007-10-07
Nope, they're definitely listed as rw. Both chmod and chown commands reported as successful, and Nautilus shows the owner and group to be correct. However, the file permissions (as opposed to folder) are blank and any changes I make there don't stick.

---

### Post by AlanRogers on 2007-11-21
Thanks to all those who posted suggestions. I think this problem was caused by having too many distros on a multi-boot system, all referencing the same /home on a separate drive. 
 
The solution in the end was to follow [Ayisu's instructions to separate /home]("http://www.psychocats.net/ubuntu/separatehome") to create a new one,  move all the files in it and delete the old one. Messy but lesson learned and it works.
 
I'm now down to just 7.10 and playing with other stuff. Interestingly, it's still got my Debian theme!

---


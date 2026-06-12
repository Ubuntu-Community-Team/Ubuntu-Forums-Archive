---
title: "Update Clam ??"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by Milt888 on 2007-04-30
When I start Clam, I get a warning that "your virus signatures are 18 days old".
Also, when I click on Help>> update signatures, I get a box saying "you must be root to install updates".
Could someone please advise on how to get these updates.

---

### Post by compiledkernel on 2007-04-30
sudo apt-get install freshclam 

sudo freshclam 

=)

---

### Post by Milt888 on 2007-04-30
That did it.
Thanks a lot.

---

### Post by compiledkernel on 2007-04-30
yw. We try our best.

---

### Post by The Pinny Parlour on 2007-05-18
-desktop:~$ sudo apt-get install freshclam
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package freshclam


DOH!!!

---

### Post by stmiller on 2007-05-19
Or just don't use A/V in Linux.... :)

---

### Post by poe503 on 2007-06-02
The graphical interface for Clam appears to have a glitch in Ubuntu 7.04

 When it boots up, it informs that the virus signatures are out of date.  If you click on the update link, it informs you that you need to be root to update.

Resolve this by opening the terminal and type "gksudo", a graphical interface pops up and type in "clamtk". 

You are now root in the Clam interface.  If you now click on the update link, it informs you that you are up-to-date.

If you close Clam and open it again, it again informs you that your virus signatures are out of date.

I suspect that the preferred way to update Clam is through the automated update system of 7.04

---

### Post by poe503 on 2007-06-05
Go here:   [http://sourceforge.net/project/showfiles.php?group_id=131278]("http://sourceforge.net/project/showfiles.php?group_id=131278") to get the latest update of Clam TK. (v. 2.32)

Use the first download, the one that ends with "all deb".  It will install itself (which is just fine with this lazy boob). 
 
No more virus signature alert.  

Use "sudo clamtk" to enable the download function in the graphical interface.

---


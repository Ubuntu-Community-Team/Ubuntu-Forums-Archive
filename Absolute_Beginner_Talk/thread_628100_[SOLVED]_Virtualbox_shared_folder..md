---
title: "[SOLVED] Virtualbox shared folder."
date: 2007-11-30
forum: Absolute Beginner Talk
---

### Post by piratesmack on 2007-11-30
My host system is Gutsy, the virtual machine is XP. I had to do this to get my printer working. How do I transfer files between the 2?
I set up a shared folder in /home/steven/ but I don't know how to access it from the virtual machine

---

### Post by parm289 on 2007-11-30
go to network places in xp and navigate to a network place called "vbox" or something similar (it should be something like vbox//home/steven).  when you've found the folder, single-click it and select "map network drive" in the panel on the left side of the window. this will make the folder appear as a drive in my computer for future use.

---

### Post by piratesmack on 2007-11-30
brilliant, thanks

---

### Post by phoenix910 on 2008-04-03
I'm having a similar trouble, however, mine is due to it asking me for a password. I don't know the syntax of username/domains and passwords to use. The host is a Ubuntu 7.10 system with username "stephen", and pc name "stephen-desktop", with domain "MSHOME". The virtual system is XP SP2, name "Test-1", with user "Test". I've tried every possible combination of my users and passwords that I can think of, but nothing seems to work. What is the standard syntax, and which user name do I use (the Ubuntu or the Windows?), or is there a default Innotek one to use? Thanks,

-Stephen

Edit: Never mind, just install the guest add-ons and the command prompt command (net use x: \\vboxsvr\folder) works perfectly.

---


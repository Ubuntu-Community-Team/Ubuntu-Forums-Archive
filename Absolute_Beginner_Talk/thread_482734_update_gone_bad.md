---
title: "update gone bad"
date: 2007-06-24
forum: Absolute Beginner Talk
---

### Post by pascalosti on 2007-06-24
I was following a tutorial ( 13 things to do after installing ubuntu) there was some codec installs.
Now the update shows these three are available to update.

libacodec0d
libavformat0d
libpostproc0d

I recieve this error  message when i try to update.

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

when i try this in terminal i recieve this
requires:  superuser privledge

How can i get rid of these updates I dont care for the codec.

---

### Post by FleetAdmiral74 on 2007-06-24
just type sudo before the command, like

$ sudo normal_command_here

---

### Post by kevdog on 2007-06-24
Try this:
sudo aptitude update
sudo aptitude upgrade

---

### Post by pascalosti on 2007-06-24
I get the same error


E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

---

### Post by kevdog on 2007-06-24
Ok do what it says:

sudo dpkg --configure -a

---

### Post by pascalosti on 2007-06-24
"thanks that worked " I say sheepishly


:-)

---


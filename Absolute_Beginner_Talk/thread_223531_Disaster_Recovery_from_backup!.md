---
title: "Disaster Recovery from backup?!"
date: 2006-07-26
forum: Absolute Beginner Talk
---

### Post by pjonesworld on 2006-07-26
Hi, I am (obvioulsy) very new to this forum and ubuntu as well.  Here's my situation.  I'm the IT Director for a nonprofit and we had someone donate some code for us.  The developer asked very few questions and basically just wrote what he wanted and handed it over when he was "done".  It was a MySQL database interfacing with Ruby on Rails all running on unbuntu--not sure which version.  He also donated the hardware on which to run this software, but then decided AFTER the fact that it wasn't a donation but merely a long-term lend.  Because of the horrible communication as the database was being developed, we had lots of problems and the relationship quickly soured.  Eventually he took his hardware back and left us high and dry.  All I have is the full backup of the machine.

The backup was done using a program called Retrospect (formerly by Dantz, now EMC/Insignia.)  It looks like it backed up three volumes (if that is the correct term): '/', 'volatile' and 'dev'.  How would I go about restoring this setup to working order on another computer?  My initial thoughts were to install ubuntu, MySQL and Ruby and then do a restore of relevant directories.  That, however, is a lot of work and I'm sure there will be problems in the end that I'm just not capable of solving.  I'm hoping someone might have a better idea.  Any help would be greatly appreciated by myself as well as the hundreds of kids this affects!

---

### Post by chalex on 2006-07-26
From first glance, you probably don't need the "volatile" and "dev" partitions.  Here's what you should try first:
1) Get a machine, install Ubuntu.  You should install the same version that the developer used or you will run into problems.
2) Install your Retrospect client on the new Ubuntu machine.
3) Restore the '/' partition on top of the fresh install.

---

### Post by pjonesworld on 2006-07-26
Sounds good.  One question, however: how do I know what version of ubuntu he used?  I can restore the backup files to a windows machine and have a peek at them for some indication.  I'm just not sure where to look and what to look at.  While on the subject, I had lots of problems getting Retrospect Client installed on ubuntu, is there a compiled installer for it out there somewhere?  EMC/Insignia only *offically* supports RedHat (I think.)

---

### Post by pjonesworld on 2006-07-27
No one can tell me how I determine what version was used?

---

### Post by CarlAndrews on 2006-10-02
If you can restore the data to a windows computer, look at the file "/etc/issue" or "/etc/issue.net" That will tell you the version.

---


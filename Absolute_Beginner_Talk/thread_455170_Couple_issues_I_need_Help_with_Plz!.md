---
title: "Couple issues I need Help with Plz!"
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by gsruizvtec on 2007-05-26
First off I must say im loving ubuntu ive been using it as my primary OS for a couple weeks now and its just awesome.  Anyway I have a couple issues I cant seem to fix even tho ive read and searched some guides on here.  First issue is my cd burner isnt working when I look at properties it says read only?  When I try to change it to read and write it wont work.  Also when I go to shut down the pc the screen flashes and stays stuck on an empty bar ubuntu splash screen.  Any help here would be great.  I'd love to get my burner working so I can burn edubuntu for my kids pc and try out a few different distros as well.  If not ill just have to install ubuntu and put the edubuntu programs and desktop on it?  Hmm anyway thanks in advance for the help.

Gsruizvtec/Dan

---

### Post by Kobalt on 2007-05-26
You don't need to change such a setting in order to get your CD burner working (the read/write permission is something else actually). Check [this]("https://help.ubuntu.com/7.04/user-guide/C/nautilus-cdwriter.html") out to learn a few things about CD/DVD burning in Ubuntu.

---

### Post by eoghanmurray on 2007-05-26
I have had **exactly** those problems two weeks ago!

My shutdown procedure does that too (flashes, hangs), but after a few seconds, the PC turns off normally. Especially, on my Pocket PC, which is only 500MHz CPU frequency, it takes up to 5 minutes to shut down.

**What is your processor?**

The other issue, read-only permissions.
Go to Main Menu > Accessories > Terminal.
Type:
```
gksudo nautilus
```
This will start super-user mode, without restrictions. A ROOT/root window will open. 
Navigate to filesystem > media\cdrom (or your requested drive).
Right click and select 'Properties'.
Open 'Permissions' tab, and select 'read and write' for all parameters.
[IMG]http://img502.imageshack.us/img502/2735/screenshotcdrompropertisb9.png[/IMG]

*These procedures worked for my computer, but I can't ensure they do on yours, and I trust you will back up before editing your system in ANY way.*

---


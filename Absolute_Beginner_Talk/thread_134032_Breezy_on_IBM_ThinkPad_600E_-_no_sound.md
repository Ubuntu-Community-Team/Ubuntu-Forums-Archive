---
title: "Breezy on IBM ThinkPad 600E - no sound"
date: 2006-02-21
forum: Absolute Beginner Talk
---

### Post by halruua on 2006-02-21
Hi All,

This is my first post on these boards so please be gentle with me. I have installed Breezy on said ThinkPad today and surprise surprise - no sound.

I have searched other posts and found this:

[http://www.ubuntuforums.org/showthread.php?t=94414](http://www.ubuntuforums.org/showthread.php?t=94414)

However, I am a complete n00b when it comes to Ubunutu and Linux in general (although I am fairly experienced with M$). The first problem I have is that I can't edit the 'blacklist' file as suggested in the above thread, because the file belongs to the root user and other users only have read access to it.

I have heard a lot about the command line and 'sudo' but I can't see how to get this fired up.

I'm not even sure if I'm asking the right questions here.

Hope someone can help.

Halruua

---

### Post by florizs on 2006-02-21
ease, relax,
your on the right track.

the problem that you can't edit the file is because it is a root file.
it belongs to the user: Root (the superAdministrator in Linux)
because for safety reasons logging in as root is disabled by default in Linux.
so to execute something as root you must type sudo command before it.

for example: sudo gedit blacklist_file
edits the file as root.

more about this here [http://www.ubuntuguide.org/#usersadministration](http://www.ubuntuguide.org/#usersadministration)

---

### Post by halruua on 2006-02-21
Thanks for the quick reply.

This is my first problem:

The Unofficial Guide talks about typing commands in Terminal mode. When I navigate to Applications > System Tools > I have no 'Terminal' (it jumps from System Monitor to Ubuntu Device Db. I am using v.5.10

Any suggestions?

---

### Post by Deaf_Head on 2006-02-21
Terminal is under accessories for me,

---

### Post by ajgreeny on 2006-02-21
For Gnome press alt+F2 and type "gnome-terminal" in the box that appears.  That will open the terminal for you.  Or if you use KDE type "konsole" instead, which will get you the KDE version.  All without quotation marks, of course.

---


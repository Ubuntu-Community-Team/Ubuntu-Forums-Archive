---
title: "Tranferring files from Ubuntu to Windows XP using an external drive"
date: 2007-11-19
forum: Absolute Beginner Talk
---

### Post by osibisa on 2007-11-19
Hello all:

I am trying to move some files from one computer to another using an external drive. The computer with the files I would like to move is running Ubuntu, while the other computer is running Windows XP. The problem is every time I try to copy the files to the external drive, it tells me I don't have permission. My external drive is set for Fat32, and I'm almost positive that's where the problem lies, but I need some help and guidance, it would be much appreciated!!!

---

### Post by Orbital75 on 2007-11-19
humm..... Well, Fat32 as you know isn't a permissions based file system so I would just
try to gksudo Nautilus and see if that will Kill those permission restrictions.

---

### Post by osibisa on 2007-11-20
Here's what I get when I try gksudo Nautilus:

"Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed. Initializing gnome-mount extension."

And then it opens a window at the root directory....??

---

### Post by lintoon on 2007-11-20
I'm not booted into Ubuntu at the minute so I can't check, but I seem to remember there is an option to add your user to a group for external disks.  I think it's in the User settings (It may be called "Users and groups") option in the Administration sub menu.  Click on your user and select properties, click on the user privileges tab and you should be able to put a tick in the necessary box.  

Sorry for the vagueness but as I say I can't check.

I've just been to good old google and found this link.  It will act as a pointer for you.

[http://www.techotopia.com/index.php/Managing_Ubuntu_Linux_Users_and_Groups](http://www.techotopia.com/index.php/Managing_Ubuntu_Linux_Users_and_Groups)

Good luck.

---


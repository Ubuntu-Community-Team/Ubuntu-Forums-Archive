---
title: "Settings Transfer"
date: 2008-01-01
forum: Absolute Beginner Talk
---

### Post by scopo on 2008-01-01
Hi all,

I once heard of a program on a Ubuntu podcast that would transfer all of the settings from one Ubuntu computer to another Ubuntu computer.
I can't for the life of me remember what it was called though ! Does anyone else know ???

---

### Post by aysiu on 2008-01-01
I don't know what program you're talking about, but you can certainly copy the relevant folders in /home/scopo in order to transfer your settings. Just make sure to change ownership of them as well.

---

### Post by scopo on 2008-01-02
Hi,
Thanks for the help !

Is is as easy as...
1)  signing in as root,
2)  changing permissions for the files to - all users read & write,
 and then...
3)  copying the entire home/user folder to the new computer.

Don't suppose this transfers programs as well ???

---

### Post by aysiu on 2008-01-02
> **scopo said:**
> Hi,
Thanks for the help !

Is is as easy as...
1)  signing in as root,
2)  changing permissions for the files to - all users read & write,
 and then...
3)  copying the entire home/user folder to the new computer.

Don't suppose this transfers programs as well ???
No--don't change the permissions on the files.

Copy the entire /home/*username1*/* from one computer to /home/*username2*/* on the other computer and then change ownership of the files on the new computer to *username2*

I repeat: do not change permissions on any files--just change **ownership** of them once they are copied.

And, no, this doesn't transfer programs as well. It just transfers your settings for those programs.

---

### Post by beercz on 2008-01-02
In terminal on the second machine try something like:

> sudo chown -R username2 /home/username2/*

See:

> man chown

---


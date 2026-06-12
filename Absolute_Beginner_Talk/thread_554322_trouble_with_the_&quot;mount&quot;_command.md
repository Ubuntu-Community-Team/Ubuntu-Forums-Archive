---
title: "trouble with the &quot;mount&quot; command"
date: 2007-09-18
forum: Absolute Beginner Talk
---

### Post by volgatha on 2007-09-18
I'm running Feisty and trying to follow [these]("http://itc.virginia.edu/homedir/loginlinux.html") instructions involving the mount command. However, when I enter the mount command, the terminal simply spits the help file back out at me. No error message, just the help file. Any ideas? Your help would be much appreciated.

---

### Post by alienexplorers on 2007-09-18
Try reading this:
> [http://users.bigpond.net.au/hermanzone/p10.htm](http://users.bigpond.net.au/hermanzone/p10.htm)

---

### Post by measekite on 2007-09-18
> **volgatha said:**
> I'm running Feisty and trying to follow [these]("http://itc.virginia.edu/homedir/loginlinux.html") instructions involving the mount command. However, when I enter the mount command, the terminal simply spits the help file back out at me. No error message, just the help file. Any ideas? Your help would be much appreciated.
I solved that problem.  The solution could be many different things.  Your description usually happens when the mount command does not completely finnish so you get no return code or an actual error message but a short version of help.

For me the parser in the mount command did not like spaces in a folder name.  I tried to mount Public Vol 2 and had the same problem.  The quick solution was to put quotes around it like:

"Public Vol 2".  That worked but when the command was inside the fstab file the parser in fstab did not like it.  I just went to my server and changed the share folder name to one without spaces.  public_vol1.

I use an underscore to separate the words for readability and use all lowercase since Linux is case sensistive.

You may have a different problem that is causing the mount command to not complete.

---

### Post by volgatha on 2007-09-18
Thanks. That worked.

---


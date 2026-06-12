---
title: "terminal issue: am I a 'root'?"
date: 2008-02-14
forum: Absolute Beginner Talk
---

### Post by nashphyl on 2008-02-14
Ok so i have streaming issues with the internet and went to some thread called "complete streaming and multimedia how to" or something like that. I pasted the recommended lines into the terminal and then i got this message:

"E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?"

I have no idea what to do next. Any ideas? Much appreciated.
-phil

---

### Post by Presto123 on 2008-02-14
Try typing sudo before you execute the operation. Like this: sudo whatever /file/blah

---

### Post by Linux_Man on 2008-02-14
No you are not root, if you want to run a simple command as root, type in sudo before it, if you have a string of commands, type in sudo bash if you do the latter make sure do not mess anything up and as soon as you are done type exit to return as a normal user as you can screw up just about anything as root.

---

### Post by taurus on 2008-02-14
Actually, you are not root but you have a root privilege.  Therefore, you need to include the sudo in front of the command if you want to run something as root.  When it asks for a password, use the same password that you log in with.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---


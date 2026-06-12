---
title: "Change to Root???"
date: 2006-09-10
forum: Absolute Beginner Talk
---

### Post by Emasters on 2006-09-10
Did an install of Ubunta off of an ISO image downloaded from somewhere.  Tried to switch to root "su -" and was asked for password?  I didn't give any root password when I set up the system ony one for my user name, so>>>>what is the password for root which is "default"  Thanks in advance

---

### Post by Chickencha on 2006-09-10
It's actually asking for the non-privileged user's password, not root's.  Try putting in your password.

---

### Post by ramcosca on 2006-09-10
Perhaps leave it blank, see what happens?

---

### Post by NetworkGuy on 2006-09-10
Don't use su.  Use sudo instead.  When it asks for a password, use your user password.

---

### Post by Emasters on 2006-09-10
Here is screen shot

eric@eric-laptop:~$ su -
Password:
su: Authentication failure
Sorry.
eric@eric-laptop:~$

That what I get when I type my password or try to leave it blank.  

What is the sudo command?
That does work but I don't know what I have.

Just trying to update synaptic with new location for video codecs etc.

---

### Post by NetworkGuy on 2006-09-10
root is disabled by default.  su wil not work.   Running sudo and then the command will allow the command to be run with root privleges.

---

### Post by Emasters on 2006-09-10
thanks.

---


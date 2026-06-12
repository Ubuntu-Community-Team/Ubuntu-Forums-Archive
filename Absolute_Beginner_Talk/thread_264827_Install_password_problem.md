---
title: "Install password problem"
date: 2006-09-25
forum: Absolute Beginner Talk
---

### Post by pohmann on 2006-09-25
Hi,
I've just installed the work station option on a clean HD.
It loads and gets me to the login point, and asks me to login.
The problem is that I do not recall any point during the install that I chose any type of password. Anything I try says "incorrect" :confused:

---

### Post by Iowan on 2006-09-25
There was (or *should have been*) a point during the install where you were asked for a username and password (typed twice for verification).  It's possible to boot into recovery mode (I don't have that info available at the moment) and edit the password for your user.
... Or, you could reinstall.

---

### Post by deadgobby on 2006-09-25
How to set/change/enable root user password

    * Read #General Notes 

sudo passwd root

---

### Post by davebgimp on 2006-09-25
When you boot and get to the Grub screen, choose the option right below the top one, it's called Single User Mode.

That will boot you as root and give you a command line.

Type **passwd "username"**, substituting "username" with your whatever account you created for yourself during install. You will be prompted for a password and again to confirm it. Just make sure you remember it and once done, type **reboot** and let your computer restart normally. You should now be able to log in with your username and new password.

---

### Post by collgra on 2007-11-25
I am having the same problem and it seems to be a bug. I can't find how to make a bug report. This thread appears repeatedly on this forum. **It is not a user problem. The system boots off the CD asks for a user name and password (which of course doesn't exist because you haven't installed yet.)** Where is that wonderful Linux support that is supposed to exist this question has been asked over and over. This problem doesn't exist in the 32 bit version of ubuntu only in the 64 bit. Can anyone help????!!!!!

Gary

---


---
title: "user permissions/groups problem"
date: 2007-07-13
forum: Absolute Beginner Talk
---

### Post by paradoxni on 2007-07-13
I installed virutualbox which required my user to be added to the vboxusers group, I did what I thought was the correct command, and virtualbox then worked after a logout, however now my user name seems to have lost all permissions:

My "System > Administration" menu now only has a few entries when it used to have loads!
My sound no longer works saying no devices are found
After a reboot X no longer works.
I cannot run any admin commands as when i do "sudo <command>" it no longer asks me for a password and nothing happens.

Im guessing I need to add my user to its original private group of the same name, but I cannot do this with usermod command as i dont have permission and as i said before sudo no longer works...

Currently using the liveCD to get online, can I do anything from here?

Help :)

---

### Post by Vajra Vrtti on 2007-07-13
I think this may work:

Boot in recovery mode. When you get the command prompt, enter these commands:
```
**adduser** *your-new-user*
**addgroup** *your-new-user your-old-group*
```
The **adduser** command will prompt for default setup information, including the user's full name and an initial password to use.

---

### Post by paradoxni on 2007-07-13
cheers for the reply.. got it sorted myself by using the livecd SU account to copy /etc/group- to /etc/group restoring my permissions..phew! steep learning curve :)

---

### Post by Cappy on 2007-07-13
The problem is that by default when you use addgroup it gets rid of all other groups you are in so you lose admin, sound, etc.

```
usermod -aG virtualbox $USER
```
If you use anything other than "-aG" you run into the problem you had. I messed up helping someone once with this and I felt really bad =(

---

### Post by Cappy on 2007-07-18
I just installed virtual box and it's actually 
```
sudo usermod -aG vboxusers $USER
```
and then Alt+Control+Backspace to log out so that the change will take effect.

---


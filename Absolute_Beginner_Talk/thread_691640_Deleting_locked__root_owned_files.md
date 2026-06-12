---
title: "Deleting locked  root owned files"
date: 2008-02-08
forum: Absolute Beginner Talk
---

### Post by chip_123 on 2008-02-08
I have some files that i moved to my trash bin. They were created by a system backup program and they are locked and  owned by root. Is there any way to delete them? Thanks, Chip

---

### Post by nynoah on 2008-02-08
Alt+F2    then type  Gksudo Nautilus.   The delete it using nautilus.  But once you are done doing that get out of nautilus so you don't delete the wrong thing.  When you do that, you are root/super user and you can do anything, including delete files needed to run the computer.

---

### Post by Rocket2DMn on 2008-02-08
First off, ALWAYS be careful when executing the "rm" command, esp. with root privileges - if you run it incorrectly, you can cause irreversable damage to your system.  First we will change directory to the root's home folder, then delete everything in the trash.
The command would be
```
cd /root
sudo rm .Trash/*
```

---

### Post by chip_123 on 2008-02-08
Thank You, I'll give it a try. Chip

---

### Post by emarkd on 2008-02-08
Rocket3DM is correct about being careful with sudo rm commands, but be equally careful with mynoah's advice.  While using a root Nautilus session may make things very easy to accomplish, one errant mouse drag or hitting <del> while you've got the wrong folder highlighted could be disastrous.  Be very careful anytime you have root priviliges because your computer will do whatever you tell it to whether it's a good idea or not.

---

### Post by nynoah on 2008-02-08
I bring up the Nautilus thing because I find I use it a lot when moving files to mounted slave hard drives or to my extern HD.  I also found I can not delete from those drives unless I am signed in as Gksudo Nautilus.  I wonder if I am doing something wrong or if that is just the way it has to be done?

---

### Post by Rocket2DMn on 2008-02-08
> **nynoah said:**
> I bring up the Nautilus thing because I find I use it a lot when moving files to mounted slave hard drives or to my extern HD.  I also found I can not delete from those drives unless I am signed in as Gksudo Nautilus.  I wonder if I am doing something wrong or if that is just the way it has to be done?

It sounds like you don't have your mount options set correctly.  If you start a new thread, we can help you with that (so we don't do thread hijacking)

---

### Post by nynoah on 2008-02-08
will do thanks

---


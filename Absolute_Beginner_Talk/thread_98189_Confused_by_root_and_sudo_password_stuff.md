---
title: "Confused by root and sudo password stuff"
date: 2005-12-02
forum: Absolute Beginner Talk
---

### Post by Scrufdog on 2005-12-02
Ive read a few posts and they didnt help at all. 

After I installed ubuntu 5.10 on this G3 iBook, it had the updates available thing on the taskbar. I clicked it and it asked me for a password. I entered what i thought was the root password and it said no, i then entered my used password, no. So i just opened a terminal, su ... password and apt'd the updates.

I then went to install Automatix, clicked to run it, was asked for a password again, entered both passwords, no..no...

What I am supposed to do with these prompts for passwords?

---

### Post by linbetwin on 2005-12-02
Enter your user passwd. I don't understand why it didn't work.

---

### Post by Scrufdog on 2005-12-02
ok, automatix seemed to work that time, but its not in the Applications - System Tools menu, so i dont know if it worked or not

---

### Post by juicybananahead on 2005-12-02
You didn't do an expert install by any chance, did you? If you did, the likelihood is that you're not able to sudo. Check out the post near the bottom of [http://www.ubuntuforums.org/showthread.php?t=77614](http://www.ubuntuforums.org/showthread.php?t=77614) for instructions to add yourself into the sudoers file.

Good luck!

---


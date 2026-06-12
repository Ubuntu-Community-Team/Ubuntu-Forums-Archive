---
title: "Cannot logon. No memory left. Any thoughts please?"
date: 2007-06-17
forum: Absolute Beginner Talk
---

### Post by ROUBOS on 2007-06-17
Hi,
I just installed Ubuntu 7.04 onto an old Compaq Armada e500 laptop.
The laptop has only got a 5G HDD.

Ubuntu worked fine. The thing is that I copied over 2.8G of mp3s from another PC, and did the system updates. Then did a system restart, and the login screen appeared as normal. The problem is that it will not let me login because there is not enough space left on the disk :(

LOL I should have looked at that. Now I would like to login in safe mode or something and delete some mp3s to free up some space.

How do I do that?

My friend uses the laptop just to play music, and he wants all those mp3s on it. So I guess that if I get a chance to login the system I'll remove some application like Gimp, and Open Office.

Any thoughts in order to login without the GUI or something?

P.S: Tried installing Xubuntu but it was dead slow. Ubuntu installed faster and better but there's not enough disk space.

---

### Post by Gimpy_Rob on 2007-06-17
push escape at boot (when it says that grub is loading) and pick the boot option for recovery.  it will log you in as root.  Be carefull, as root can do pretty much anything, including deleting something you want.

Then just delete the mp3 files you put on there through the command line interface.

---

### Post by ROUBOS on 2007-06-17
cool
and then just type "exit" and it will restart the system?

---

### Post by jasmuz on 2007-06-17
My recommendation is installing a "lite" Ubuntu derivative.. Xubuntu or somewhat, if not install normal Ubuntu, and later on install fluxbox, and start trimming the distro as much as needed.

If you cant make it work properly, then try researching about Damm Small Linux, or Puppy Linux, wich are made specially for these kind of situations.

Best of luck
Mail me if you need any more ideas

---

### Post by Gimpy_Rob on 2007-06-17
not sure... it might.  but```
 shutdown -r now
``` will work for sure.

(the -r is restart, now is when to do it)

---

### Post by ROUBOS on 2007-06-17
Thanks people. Will try all these ideas and see how I go.
Will get some sleep first though it's 9am here and I'm still up from last night :)

LOL felt like an all -nighter.... I miss them good old UNI days.


Thanks again

---


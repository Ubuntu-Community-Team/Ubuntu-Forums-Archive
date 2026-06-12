---
title: "Admin Programs Wont Run"
date: 2006-10-25
forum: Absolute Beginner Talk
---

### Post by Yelolemon on 2006-10-25
Hi everyone, im new to Linux and installed it fine and was going well for first couple of days but now when i login and try running 'Networking' from the administrator menu it opens the tab for 10 seconds then it closes without running the program.

This applies to most of the programs in there, also gaining access to the home folder and other programs takes time as well and it shoudln't. It seems very slow and i have very good hardware which is more than capable of running Linux without any problems.

If anyone has any ideas i'd be very grateful to hear them.

Cheers

---

### Post by tzulberti on 2006-10-25
you could try to run that program from console with "sudo nameOfTheProgram", and see if any message appears.

---

### Post by Yelolemon on 2006-10-25
It says:

sudo: unable to lookup (none) via gethostbyname()



I forgot to mention that when i try login now on bottom right corner of screen it shows (none)// where it used to have the computer name.

---

### Post by CatKiller on 2006-10-26
It sounds like your /etc/hosts and /etc/hostname files aren't quite as well-formed as they should be. Have a look around for what they should look like, and how to fix them.

---


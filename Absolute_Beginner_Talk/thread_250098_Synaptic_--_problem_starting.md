---
title: "Synaptic -- problem starting"
date: 2006-09-03
forum: Absolute Beginner Talk
---

### Post by SCHagin on 2006-09-03
I added a new repository to Synaptic and after I started the program up again  I can no longer get a list of any of the repositories and cannot do anything in the program. When the program starts I get the following error message.

--ERROR MESSAGE BELOW --

E: Type 'http://archive.canonical.com/ubuntu' is not known on line 33 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.

-- END OF ERROR MESSAGE --

When I click "OK" at the end of the message I go into the program but none of the categories show up and none of the programs are listed.

What can I do? Show I use apt-get to uninstall Synaptic and then reinstall it? This is only my second day with Linux and I have no idea what to do!

---

### Post by Miademora on 2006-09-03
You could post your sources.list here. Seems theres something wrong with it.

---

### Post by greyash99 on 2006-09-03
If you recently added a reposistory to your sources.list try deleting that new entry and then type
```
sudo apt-get update
```
or hit refresh in synaptic.

---

### Post by SCHagin on 2006-09-03
How can I edit sources.list. It says it is a read.only file.

---

### Post by greyash99 on 2006-09-03
type
```
sudo gedit /etc/apt/sources.list
```
in the terminal

---

### Post by SCHagin on 2006-09-03
Thanks - all - I edited the sources.list file and its back to normal. :)

---


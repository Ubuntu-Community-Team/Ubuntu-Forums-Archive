---
title: "Moving file problems (with screen shot)"
date: 2005-10-05
forum: Absolute Beginner Talk
---

### Post by edurm on 2005-10-05
I created a Directory in /


now I'm trying to move some files there but an error occur



Why?



[img]http://upl.silentwhisper.net/uplfolders/upload5/moving_file_perm.png[/img]


Thks 'n advanced

---

### Post by matthewv on 2005-10-05
[QUOTE=edurm]I created a Directory in /
now I'm trying to move some files there but an error occur
Why?
Thks 'n advanced[/QUOTE]
Go to your terminal and type
```

sudo chmod -R 777 /install
```
You should then be able to copy to that folder

---

### Post by edurm on 2005-10-05
Great, thks, first I try -r  but only -R  works

Linux is so case sentitive :D

---

### Post by matthewv on 2005-10-05
the -R just makes the command act recursively, and yes, linux is very case sensitive. just got to get used to it

---

### Post by dcraven on 2005-10-05
I don't know why you are making directories and moving files there, and it doesn't really matter. I just thought it was a good idea to mention that you don't want to run the "chmod -R 777 *" command **in general**. If you do this in the wrong place, then bad things can happen; at best you open your system to severe security vulnerabilities, and at worst your system stops working.

The idea is that users keep their data and relevant files in their home directory. This is different than Windows to my knowledge, so it's understandable if you didn't know this. I strongly suggest you try to adhere to this, or at least be very mindful when running commands as root in other areas of the filesystem.

Nobody says you can't put files wherever you want on your system. I'm just giving you a friendly heads up in case something bad might have happened :). I know of users that ran the "sudo chmod -R 777 /" and the solution was to reinstall.

Cheers, and have fun,
~djc

---

### Post by edurm on 2005-10-05
Thank You very much **dcraven** ;)

---


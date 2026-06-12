---
title: "Weird external HD problem . . ."
date: 2006-04-29
forum: Absolute Beginner Talk
---

### Post by ZelasMetallium on 2006-04-29
I have an 80 GB Seagate external HD.  It worked fine when my computer had Windows.  I then formatted it before installing Ubuntu (Though I did not install it on the external, that was on my internal.) and upon plugging it into my computer now it does read a drive there but it reads it as 7.4 GB and it contains one folder, "lost+found," which I can't access.  Help!

Oh, and on an unrelated note, I can't for the life of me figure out how to use gtkPod.  Any help on that issue?

---

### Post by ncappel1 on 2006-04-29
I've never used gtkpod, but maybe you problem with the external harddrive is that when you partitioned, you did not partition as ext3. In order to use it as extra space it has to be ext3.

edit: the reason you can't access the lost and found (well, im guessing you can view it, but not write to it) is because that is part of the restricted file system. you have to have administrator priviliges to modify it. use the "sudo nautilus" command in a terminal, enter your password and navigate to the folder to be able to use it. this is not a good, however, because the system uses the lost and found for its own uses-it is not a folder for the computer users.
for more info on the linux file system: [http://www.tldp.org/LDP/intro-linux/html/sect_03_01.html](http://www.tldp.org/LDP/intro-linux/html/sect_03_01.html)
this page has a great table (3/4 way down) and some interesting info.

---


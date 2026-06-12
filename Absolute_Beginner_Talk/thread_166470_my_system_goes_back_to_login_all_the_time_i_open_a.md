---
title: "my system goes back to login all the time i open app"
date: 2006-04-26
forum: Absolute Beginner Talk
---

### Post by lildevil on 2006-04-26
help please 
everytime i open a folder or anything (at least 80% of time) my system goes back to my login screan can anyone help me find out why ?

---

### Post by richardward101 on 2006-04-26
We're not gonna be unable to help without a little more info, so see if you can open up a terminal and type in 

dmesg | tail

if you can't get it that far the log in to a failsafe terminal (option in the login screen) and try it there. there may be something there that could shed light on whats actually going on.

also, just to narrow it down, try logging into Gnome Failsafe (i assume you are using Gnome) and seeing if things still crash there, and then report back.

---

### Post by lildevil on 2006-04-26
thank you for the reply i did as asked and got this hope it helps 

alan@lildevilcomp:~$ dmesg |tail
[4297915.437000] EXT3-fs: mounted filesystem with ordered data mode.
[4297920.901000] kjournald starting.  Commit interval 5 seconds
[4297920.902000] EXT3 FS on hdf1, internal journal
[4297920.902000] EXT3-fs: mounted filesystem with ordered data mode.
[4297944.894000] kjournald starting.  Commit interval 5 seconds
[4297944.894000] EXT3 FS on hdf1, internal journal
[4297944.895000] EXT3-fs: mounted filesystem with ordered data mode.
[4298026.420000] kjournald starting.  Commit interval 5 seconds
[4298026.420000] EXT3 FS on hdf1, internal journal
[4298026.421000] EXT3-fs: mounted filesystem with ordered data mode.
alan@lildevilcomp:~$

---

### Post by richardward101 on 2006-04-27
hmm still not enough i'm afraid. what would be best i think is if you get it to crash, then log into the failsafe terminal and type
dmesg > dmesg.txt
and attatch the file to your reply.
also, another clarification has occoured to me, when you say your login screen do you meen the graphical ubuntu login or is it a text based one, i.e is it the graphical server thats crashing or is Gnome just logging you out?

---


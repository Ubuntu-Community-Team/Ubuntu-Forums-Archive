---
title: "activating an executable?"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by frozenjake on 2008-02-05
I am new (24hrs>) to Ubuntu. I have messed with command line throughout my career, incl early DOS, Cisco CLI, and other odds and ends. I have downloaded the Dark Places linux port , and all the executables are in the right folder. How do I get the executable files to run? <----NOOB question!

Thanks!

---

### Post by logos34 on 2008-02-05
chmod +x

[http://icculus.org/twilight/darkplaces/readme.html#HowToInstallQuake_Linux](http://icculus.org/twilight/darkplaces/readme.html#HowToInstallQuake_Linux)

---

### Post by Linux_Man on 2008-02-05
Ok, first off make sure the files are tagged as executable, in most graphical file managers you can right click and make it executable (you can go via the CLI using chmod but the last time I tried to make it be executable I messed it up so read the man page using man chmod if you want to do it that way) then if it is you /usr/bin path you should just be able to type whatever the name was and it would execute if it isn't you will need to type in ./*name of binary* to run it if it is in the directory you are at. Hope this helps!

---

### Post by frozenjake on 2008-02-05
sweet! Thanks a bunch guys. It still runs all kinda choppy and screwed up, but I guess that'd be the gaming forum, huh....
TY!:guitar:

---


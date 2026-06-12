---
title: "An message I keep getting"
date: 2006-10-06
forum: Absolute Beginner Talk
---

### Post by saintj0n on 2006-10-06
Occasionally, during my adventures in debian package installing, I bump into this message:



An older version is available in a software channel

Generally you are recommended to install the version from the software channel, since it is usually better supported.

What is a software channel and why is it better?

---

### Post by WalmartSniperLX on 2006-10-06
this is your repos. It is a repository of software on a bunch of servers you can access and download programs from. You can acces by going to System/Administration/Synaptic Package Manager.  

In order to get all the dls available open System/Admin/Software Properties   and check ALL the boxes and click close, then reload. 

To download from the the reops you can use synaptic and in 'search' type in the name of the program. Then check it off for installation then click 'apply".

Also if you know the name of the program you want to install (the name in the repos that is), you can use ```
 sudo apt-get install <app name> 
``` in a terminal

EDIT: Its better because all the programs in it are either edited or compiled to work with ubuntu without flaws. A LOT of debian packages out there require certain system packages to be installed (in ubuntu) because they arent compiled for ubuntu, really. So its better because if you can get the program in the software channels, it will always work.

---

### Post by saintj0n on 2006-10-06
Does synaptic manage dependencies fairly reliably? I install IDE's and often download tarballs to compile.  I hate having to mess with dependencies but they seem to be prevalent in programming -type apps.

---

### Post by Polygon on 2006-10-06
usually most of the time if a program has any dependency it will tell you to install this program it will need also these other programs/libs, and you just press  ok and it will also mark those for installation.

---


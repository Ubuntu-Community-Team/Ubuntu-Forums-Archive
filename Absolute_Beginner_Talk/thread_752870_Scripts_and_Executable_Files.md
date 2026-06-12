---
title: "Scripts and Executable Files"
date: 2008-04-12
forum: Absolute Beginner Talk
---

### Post by jou770d on 2008-04-12
I use both Gutsy and XP (for some uni related stuff) and for some reason some of the files that I save/download from the internet on windows are always set as executable on Gutsy. And this is starting to get annoying.
It mostly happens with .html files and as I have set it as default behaviour for executables to run (to make using my home-made scripts easier) that means that each time I try to open one of those files I usually double click it and notice that nothing is happening so I remember the problem and I right click it to chose open with firefox.
I've tried right clicking and unchecking "allow executing as program" but the check won't go.. (I don't know how to do the same from terminal, I only know how to make the file executable from there).
Any workaround to avoid this problem??

And I also have a second question regarding some of the 'home-made' scripts I've mentioned.
I've two very simple scripts to make it easier to copy packages from my desktop to my laptop and vice versa.
Here they are:
```
#!/bin/bash

mkdir -pv packages_copy
sudo cp -vu /var/cache/apt/archives/*.deb ./packages_copy/
beep
```

```
#!/bin/bash

sudo cp -vu ./packages_copy/*.deb /var/cache/apt/archives/
beep
```

They work perfectly well but only if I executed them in a terminal, otherwise I only get the beep (and an empty folder with the first one). I'm guessing that's because of the 'sudo' in there but being a noob I'm not sure.
Is it possible to make them work only by double clicking them?

---

### Post by Average Joe on 2008-04-12
For the first issue:

You could try to mount your Windows (FAT32/NTFS) partitions with the following options in your /etc/fstab file:
```
defaults,uid=1000,gid=1000,fmask=0133,dmask=0022
```
This will make you the owner of all the files and directories on the Windows partition, allows you to both read and write the files and execute directories, and others only to read files and execute directories (assuming that you have uid=1000). So files on the Windows partition are not executable any longer.

The second issue:

I am not sure but, what if you only allow root to run your scripts (by making it owner and setting the right permissions):
```
sudo chown root:root <scriptname>
sudo chmod 700 <scriptname>
```

Maybe then it will ask you for the root password if you double click on it.

---

### Post by Claus7 on 2008-04-12
Hello,

I do not remember where, but I had come accross this issue once again (I'm talking about your second question). I do not think that you should be able to solve it at least easily. The best way to run a script is via terminal. 
Once I wanted to recreate a graph with different input via script, I double clicked and the result was that the graph remained unchanged. I went via terminal and everything was ok! 

I do not remember the reason why this is happening, maybe someone else could explain or give a solution as well... My proposal is trust the terminal!

Regards!

---


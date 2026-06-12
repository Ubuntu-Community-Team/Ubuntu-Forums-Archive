---
title: "Installing programs not in synaptic?"
date: 2005-09-15
forum: Absolute Beginner Talk
---

### Post by hansoffate on 2005-09-15
I have a .deb file. 

This is what i did and the outcome.  

> hans@hans:~/Desktop$ sudo dpkg -i /home/hans/Desktop/peerguardnf-1.5beta.i386.deb
Password:
(Reading database ... 59193 files and directories currently installed.)
Preparing to replace peerguardnf 1.5 (using .../peerguardnf-1.5beta.i386.deb) ...
Unpacking replacement peerguardnf ...
Setting up peerguardnf (1.5) ... 

Now my questions are...is it installed? how do i launch it? Can i get it into the aplications bar?

---

### Post by az on 2005-09-15
dpkg -L peerguardnf


that will list the files in the package.  You will see what file to run to start it.

---

### Post by aysiu on 2005-09-15
It is installed.
Try typing peerguardnf in the terminal. See what happens.

---

### Post by d1337 on 2005-09-15
From the application menu drop down, you can select run application and type in the command to run it.  You can also right click on the top or bottom panel and add a custom application launcher once you know what the launch command is.  There is some quite useful info in the [Unofficial Guide](http://ubuntuguide.org) on adding applications to menus namely installing **smeg**.

d1337

---

### Post by hansoffate on 2005-09-15
> hans@hans:~/Desktop$ dpkg -L peerguardnf
/.
/etc
/etc/p2p.p2b.p2p
/etc/PG.conf
/debian-binary
/usr
/usr/share
/usr/share/man
/usr/share/man/man1
/usr/share/man/man1/peerguardnf.1
/usr/bin
/usr/bin/pgtext
/usr/bin/peerguardnf

hans@hans:~/Desktop$ peerguardnf
peerguardnf: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory 

That is what i get.  Any ideas?

---

### Post by d1337 on 2005-09-15
Methinks you have some dependency issues.
[This Page ](http://rpm.pbone.net/index.php3/stat/4/idpl/1925940/com/peerguardnf-1.5_0.1-1.guru.suse93.i686.rpm.html) shows that as a required package.

---

### Post by hansoffate on 2005-09-15
ahh, yes you are correct. How would I get the dependency?

---

### Post by d1337 on 2005-09-15
I think that will depend on your repositories and the availability of that package to Ubuntu. An apt-cache search doesn't show that particular lib, but several very close to it...who knows.  And, there may be others from the required list that you might not currently have installed...which may also be tricky to get and to make work.  Might I suggest using the [Unofficial Guide](http://ubuntuguide.org) to update your repository list and to have a peak within synaptic to see if there is already a package that may do just what you need it to do.  In synaptic, search for guard or filter to see if that might be the case.  Otherwise, I'm certain that peerguardnf could be made to work within Ubuntu, but that is far beyond my noob capacity.

d1337

---

### Post by hansoffate on 2005-09-15
Thanks for all your help. If your  newb then I'm a ... well newblet or something not even enough to be a newb lol.

---


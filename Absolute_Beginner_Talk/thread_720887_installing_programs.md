---
title: "installing programs"
date: 2008-03-10
forum: Absolute Beginner Talk
---

### Post by Leafx on 2008-03-10
hi i am brand spanking new to using linux so i have no idea how to install anything
example
i am trying to install xchat, an irc client. it even shows install directions on their site
# Unpack the archive:
tar -xzvf xchat-x.x.x.tar.gz
or
tar -xjvf xchat-x.x.x.tar.bz2
# Run the configure script:
cd xchat-x.x.x
./configure
# Compile the program:
make
# Become root and install the program:
su
(enter password)
make install 


i just get errors. i dont know how to locate the terminal to files when they are sitting right on my desktop
other programs that i wish to install are just sound drivers and azureus

---

### Post by bodhi.zazen on 2008-03-10
Always best to install from the repos :

[https://help.ubuntu.com/community/SoftwareManagement](https://help.ubuntu.com/community/SoftwareManagement)

Also Ubuntu uses sudo rather then su :

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Use gksu for graphical apps :

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by mikewhatever on 2008-03-10
cd ~/Desktop <-- To move to the Desktop.
Please note that Terminal is case sensitive, so that 'desktop' would not work.
Now, xchat seems to be in the repositories, so there is no need installing from source.
To run the latest of Azureus, check out this [http://ubuntuforums.org/showthread.php?t=678122&highlight=azureus](http://ubuntuforums.org/showthread.php?t=678122&highlight=azureus), or install the slightly older version from the repositories.

---

### Post by Leafx on 2008-03-10
i also have no clue as to what repositories i have or where to get them
i dont know when i need to download source files and what not. it says on the download page it works for fedora linux but does that mean i can download that and go from there? how do i find out if i need package depencies and where do i get them??

---

### Post by -gabe-noob- on 2008-03-10
ok heres what I would do go to
system- administration- synaptic package manager

edit: Synaptic= repos as i understand it

here you can search for the program you want. 

if it's not in synaptic then for a tar.zg I usually extract to my desktop and follow the instructions from their.

---

### Post by bodhi.zazen on 2008-03-10
No, installing packages is much easier then that.

You can use ADD/Remove or synaptic.

See the links I gave you plus this :

[https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)

---

### Post by -gabe-noob- on 2008-03-10
The forum mod... and I kinda said the same thing

I'm pretty new to linux, though I've been using it for a couple of months and I like to think I just got over the learning curve,,, cause... I CAN DO STUFF lol  but yeah aperntly in this case synaptic or the "repos" is the way to go.

edit: synaptic will attomaticly install any needed dependencies aswell... and main poster I replyed in your wireless internet  thread tell me if I helped you any

---


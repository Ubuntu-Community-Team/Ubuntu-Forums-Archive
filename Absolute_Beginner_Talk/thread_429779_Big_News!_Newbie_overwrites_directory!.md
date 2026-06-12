---
title: "Big News! Newbie overwrites directory!"
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by ChuxMix on 2007-05-01
Yup, I did it.
I knew it would happen eventually.
The good part is that it was nothing serious.
I was trying to create a modem script text file in my /etc/ppp/peers and didn't pay enough attention and wound up creating a text file named peers. /etc/ppp/peers is now gone. :confused: 
Just a word of caution to other noobs like me, go slow, pay attention, and make frequent backups!!!
My next task: learn how to make frequent backup of system.
Could anyone post a .zip of a clean /etc/ppp/peers file?
I'd rather not do a re-install for this one small thing...
I promise I'll learn to backup my system!!! :KS

Flavour: Feisty

---

### Post by kittyhawk63 on 2007-05-01
No /etc/peers here. File doesn't exist in default Feisty. Al least that is true of me.
kh

---

### Post by steve.horsley on 2007-05-01
I don't seem to have one of those at all. Fresh install of Feisty. You don't mean /etc/ppp/peers do you?

---

### Post by ChuxMix on 2007-05-01
Oh, yes.
The folder in question is /etc/ppp/peers.

---

### Post by steve.horsley on 2007-05-02
Attached is a tar file. Use these commands to restore the peers directory:
[B]sudo -i
cd /etc/ppp
tar xf peers.tar[/B]
but of course that last line will have to specify the path to peers.tar, e.g. tar -xf /home/chuxmix/Desktop/peers.tar

---

### Post by ChuxMix on 2007-05-02
Thanks Steve!!!!!
That was a big help and saved me a lot of time!!!!

---

### Post by steve.horsley on 2007-05-02
I'm glad I could help.

---


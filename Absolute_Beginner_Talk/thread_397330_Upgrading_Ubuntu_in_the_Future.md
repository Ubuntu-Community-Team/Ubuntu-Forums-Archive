---
title: "Upgrading Ubuntu in the Future"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by nphoops on 2007-03-30
I'm going to install Feisty Fawn once it reaches it's completed stage, but what do I do when the next version is released in 6 months? Will I have to wipe my HDD and start all over? :confused:

---

### Post by ubuntu27 on 2007-03-30
You don't need to wipe your HD to upgrade to a new version :)

It is your option to whatever do a clean install or to upgrade from your current install. ;)

---

### Post by jimbren on 2007-03-30
Do you have ubuntu installed now?  It sounds like you don't, but you're planning to, so that's what I'll assume in my answer.  Let me know if that's not the case.

When you're doing the installation and get to the partitioning\formatting phase, you can set up a partition for /home.  This is not the default, but it isn't hard to do, and you can find instructions for doing so here: [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning).  (This is an excellent site for all kinds of Ubuntu questions, by the way.)

The advantage to having /home on it's own partition is when you do subsequent installations, either of an upgrade or the same version, you can save all of your /home data.  This means all of your documents, pictures, mp3s, as well as your personal configuration files for individual programs will be saved from install to install.  All you do is make sure you don't format that partition during installation, and then flag it as /home when you're actually setting up the partitions, and you're set.  

It also makes it pretty easy for doing backups, if that's something you plan on doing.  

Even with this method, you would still run into some files that you need to reconfigure however you had them, but you can always make copies of them to /home before you do a new install, and then you're set.  

If you haven't installed linux before, this might sound hard, but it's really not.  Have some faith and read the page I cited above, and you'll be good to go.

jimbo

---

### Post by nphoops on 2007-03-30
I'll  be using wubi, will that change things?

---


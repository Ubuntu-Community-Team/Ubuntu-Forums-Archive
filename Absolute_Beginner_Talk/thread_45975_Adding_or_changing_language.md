---
title: "Adding or changing language"
date: 2005-07-02
forum: Absolute Beginner Talk
---

### Post by pat_togo on 2005-07-02
Hi all,
I am living in China and installing Ubuntu on some computers to be sent to Togo West Africa. I have installed the english version (?), is there a way to change the platform to french or should I restart the installation? Otherwise is there a way to add french language to the start menu so that when you choose french you have it in french and when you choose english you have it in english?
Thanks.
Patrick

---

### Post by GTvulse on 2005-07-02
Do not redo the installation. You can install basic French support off the installation CD.

With the CD inserted in the computer, open Synaptic, click on the "sections" button, scroll down to the end of the list and search for "language-pack-fr". If you want full French support you will need to install "language-support-fr". 

For the latter you have to be connected to the internet and enable the network repositories, therefore, you may want to install the files in a computer with an internet connection, take note of what gets installed and then copy all those deb files from /var/cache/apt/archives to a CD and install by hand using dpkg (type man dpkg at a terminal prompt for the application manual).

In fact, if you update a computer with the same hardware and specs with the latest security updates (that you have to enable in Synaptics repository settings), you can copy those deb files to the same cd and install them in the other computers so that the people in Toga can have up-to-date systems without having to connect to the internet and update them themselves (which can be a burden in the third world, security updates amount already to more than 150 Mb calculating off the top of my head, not my idea of fun using dial-up.

Good luck with your endeavours! I've done it myself years ago for people living in  Africa and Southern Central Himalayas (among other parts of the world...).

---


---
title: "Trouble With Xubuntu"
date: 2006-10-01
forum: Apple PPC Users
---

### Post by Warcrafter on 2006-10-01
I can't use azureus or any bittorent clients.  I recently had ubuntu and xubuntu and I had to reinstall it because when I restarted xubuntu the task bars at the top and bottom of the screen where not there.  So I reinstalled it on an iMac G3 with just Xubuntu.  Is there a way to install ubuntu with out a disc because I entered a code in the terminal that I read in a forum that downloaded and installed xubuntu.  So what do I do to use these programs.  Im trying to download the digg video podcasts.

---

### Post by DirtDawg on 2006-10-01
You can install by opening the terminal and entering:
```
 sudo aptitude update && sudo aptitude install ubuntu-desktop
```
You should know that you can install the programs you want on Xubuntu just fine. They'll be available in Synaptic. The pieces of Gnome they need to run will be installed, you don't need to install *all* of Gnome (unless you want to, of course).

---

### Post by Warcrafter on 2006-10-02
how do I install part of gnome?  azureus wasn't in synaptic or add/remove.

---

### Post by DirtDawg on 2006-10-02
> **Warcrafter said:**
> how do I install part of gnome?  azureus wasn't in synaptic or add/remove.

Hmm. I'm not in front of my Linux box at the moment, but I believe I checked and Azureus was in the repos. Are you certain you have universe and multiverse enabled? That would be the easiest way to go.

Otherwise, I believe the above command will install gnome as Ubuntu uses the Gnome desktop.

---

### Post by bodycoach2 on 2006-10-02
It's my understanding (correct me if I am wrong) that Azureus, like Frostwire, is a Java based platform. You have to go through the steps to get Jave working on an iMac:
[https://help.ubuntu.com/community/Java?highlight=%28java%29#head-81c3789bc76872336f69a7af90d1759ef38eeb64](https://help.ubuntu.com/community/Java?highlight=%28java%29#head-81c3789bc76872336f69a7af90d1759ef38eeb64)

It's a bit of work, but I got it to work on two old iMac G3 333Mhz computers Try getting that to work.

> **Warcrafter said:**
> I can't use azureus or any bittorent clients.  I recently had ubuntu and xubuntu and I had to reinstall it because when I restarted xubuntu the task bars at the top and bottom of the screen where not there.  So I reinstalled it on an iMac G3 with just Xubuntu.  Is there a way to install ubuntu with out a disc because I entered a code in the terminal that I read in a forum that downloaded and installed xubuntu.  So what do I do to use these programs.  Im trying to download the digg video podcasts.

---

### Post by DirtDawg on 2006-10-02
> **bodycoach2 said:**
> It's my understanding (correct me if I am wrong) that Azureus, like Frostwire, is a Java based platform. 

Ouch, I didn't know that. I've never actually used it. Let us know how it works.

---

### Post by K.Mandla on 2006-10-02
Yup, those two need Java to run. You can get that with *sudo aptitude install sun-java5-bin* or *sun-java5-plugin* if you want Java inside Firefox/Swiftfox too.

If you want a small torrent client just for testing purposes that doesn't use Java (like if you want to make sure the problem isn't your network), try rtorrent. It's terminal based, so it's much lighter, and doesn't need any Java so you can see where the problem lies without installing another giant torrent client.

EDIT: Hmm. I just realized I was in the Mac arena. I might have just given bad advice. My fingers are crossed. ... #-o [-o< Sorry if I'm off base.

---

### Post by Warcrafter on 2006-10-02
thats weird because when I had ubuntu I could use azureus fine and i never had to install java.  I ran the update manager when I reinstalled xubuntu and downloaded all the updates.

---


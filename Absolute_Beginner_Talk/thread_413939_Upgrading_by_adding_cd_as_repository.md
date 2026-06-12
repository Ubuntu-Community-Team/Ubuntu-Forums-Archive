---
title: "Upgrading by adding cd as repository"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by PetePete on 2007-04-19
i've downloaded via bittorrent the standard kubuntu cd and burned it to disk, i thought it would be quicker than waiting for repositories and stuff

anwyays, how do i use the adept manger to upgrade my system from the CD?
someone mentioned about adding the CD as a repository, but i dont know how to do that (i know how to add repositories, but just not 1 from CD)

could someone explain?


thanks!!!

---

### Post by PartisanEntity on 2007-04-19
I have never upgraded, I usually just do a clean install, but from what I have been reading the best method is to launch the Update Manager, it should show you that a new version is available and there will be an  upgrade button, click it and follow the on screen instructions, also see:
[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

---

### Post by aysiu on 2007-04-19
If you downloaded the Alternate CD, paste these commands in [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
sudo mv /etc/apt/sources.list /etc/apt/sources.list.edgy
sudo apt-cdrom add
sudo apt-get update
sudo apt-get dist-upgrade
``` If you downloaded the Desktop CD, you can't upgrade from that. You can do only a reinstall with that.

---

### Post by PetePete on 2007-04-19
uh f*cks sake.
looks like i'll download hte alt CD then

seriously guys, its stuff like this which put people off linux... 

why can't i just put it in the drive and it automaticlly realises i already have edgy and asks if i want to upgrade..


thanks for the advice though :)

---

### Post by aysiu on 2007-04-19
I've filed a bug report on the Ubuntu website:
[https://bugs.launchpad.net/ubuntu-website/+bug/107789](https://bugs.launchpad.net/ubuntu-website/+bug/107789)

It has the description *Not obvious that Desktop CD can't be used for upgrade*

Maybe they'll fix that soon.

---

### Post by reazn on 2007-04-20
> **PetePete said:**
> uh f*cks sake.
looks like i'll download hte alt CD then

seriously guys, its stuff like this which put people off linux... 

why can't i just put it in the drive and it automaticlly realises i already have edgy and asks if i want to upgrade..


thanks for the advice though :)

maybe you should read the instructions?

---

### Post by PetePete on 2007-04-20
> **reazn said:**
> maybe you should read the instructions?

you sound like my girlfriend.

Thanks for filling the bug report.

---

### Post by mlissner on 2007-04-21
> **aysiu said:**
> If you downloaded the Alternate CD, paste these commands in [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
sudo mv /etc/apt/sources.list /etc/apt/sources.list.edgy
sudo apt-cdrom add
sudo apt-get update
sudo apt-get dist-upgrade
``` If you downloaded the Desktop CD, you can't upgrade from that. You can do only a reinstall with that.

Aysiu, you always have great advice. Will these commands need to be reversed after the upgrade so it doesn't always look for the CD?

Thanks.

---

### Post by lumarh on 2007-04-21
i had the same problem, got the desktop cd and didnt realise it couldnt be used to upgrade.

it doesnt make sense to me that its not upgrade enabled but oh well

---

### Post by mlissner on 2007-04-21
Well, I attempted this method, but it failed miserably. 

I ended up going to [http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/), and getting a new Feisty sources.list list. Now that I have that, I ran sudo apt-get update and then sudo apt-get dist-upgrade. Hopefully this isn't going to kill my computer, but I'm too impatient to try much else at this point...

---


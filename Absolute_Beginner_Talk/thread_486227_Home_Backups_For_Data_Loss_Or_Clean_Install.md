---
title: "Home Backups: For Data Loss Or Clean Install?"
date: 2007-06-27
forum: Absolute Beginner Talk
---

### Post by ityro on 2007-06-27
Hello All,

Some home backups protect only the home/user folder while others such as Sbackup include additional folders along with the home/user folder.

Am I correct in assuming (hah!) that the backups protecting only the home/user folder are for clean installs while those with folders in addition to the home/user folder are for data loss protection? 

If I do a clean install of Gutsy then restore a home backup containing /var /etc and /usr/local wouldn't I be replacing parts of Gutsy with Feisty? 


Thanks for your time.

---

### Post by starcraft.man on 2007-06-27
I'm not sure exactly what your getting at. I think your talking about folder synchronization, whereby you instruct a program to back up folders x y z in home folder to a backup place. The purpose of those is really just to provide redundancy of critical data in case of failure.

I don't know what you mean by home/user verse more folders... most synchronizations are just for data.

In reference to the last bit, if you install Gutsy (its still Alpha/Tribe not recommended) and restore Feisty files, you will definitely have problems. Not recommended.

If your looking for a solution to back up an entire install, please look at drive imaging suites like Partimage. It makes a bit for bit copy of your partition and allows for quick restoration of a functional OS with all your customizations. In conjunction with synchronization of your folders in home, this makes a great back up solution.

[Partimage guide by Aysiu.]("http://www.psychocats.net/ubuntu/partimage")
[Backing Up with rsync.]("http://www.psychocats.net/ubuntu/backup")

That should do it, enjoy.

---

### Post by ityro on 2007-06-28
Thank you starcraft.man,

Sorry. I did not make myself clear. I do not synchronize anything so I did not think of it. And to top it off I used a bad example with Gutsy, and it did cross my mind I was making a mistake.

I guess my real question is:  after a clean install from Edgy to Feisty would I want to restore my home folder with a backup that contained anything in addition to my Edgy home folder? Such as /var /etc /usr/local?

Thanks Again.

---

### Post by Nythain on 2007-06-28
theres a few files outside of /home that i back up regularly.

/etc/samba/smb.conf - Samba configuration file
/etc/X11/xorg.conf - x configuration file
/boot/grub/menu.lst - grub configuration file
/etc/apt/sources.list - self explanatory

those are pretty universal...
i also back up many other /etc/ files, various configuration files for software i install

minor note, not sure if its been mentioned... if you back up your /home folder, make sure a few things... a. the user on the fresh install is the same as the user you used in the previous install and b. make sure you get the apps to the same version, sometimes configuration options change in versions, so /home/whatever/kde from a kde 3.5 isnt going to work so well if you only have 3.4 or so on the fresh install

---

### Post by ityro on 2007-06-28
Thank You Nytham,

I think I have my answer. My system is small (3GB) so I do backups of my entire system using TAR and Grsync for protection from data loss and my foul-ups. Used to do Mondo Archive but it stopped working when I upgraded from Dapper to Edgy.

If my next upgrade fails (after Gutsy is stable) and I have to do a clean install I will restore my Feisty home folder only. No extras.

Thanks for the tips.

---


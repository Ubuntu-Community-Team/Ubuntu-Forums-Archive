---
title: "Ubuntu + backups?"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by TURNER on 2007-04-30
Hi all, 

I am about to go tinkering with Ubuntu, in order to install restricted drivers for a dreaded ATI card, just in case things go wrong, is there a way in which I can back up my current settings in order to roll it back upon horror scenario?

thanks in advance!

---

### Post by Nythain on 2007-04-30
what are you wanting to back up.
/etc/X11/xorg.conf is a good file to back up if you are tinkering with driver settings and whatnot.
a list of files i regularly back up consists of...
/etc/X11/xorg.conf
/etc/apt/sources.list
/etc/samba/smb.conf
any amarok playlist i have made
i export my firefox bookmarks to a file regularly

you could also consider backing up your /home folder in case you have to completely reinstall, saves a lot of Desktop configuration time

---

### Post by koconnor100 on 2007-04-30
> **TURNER said:**
> Hi all, 

I am about to go tinkering with Ubuntu, in order to install restricted drivers for a dreaded ATI card, just in case things go wrong, is there a way in which I can back up my current settings in order to roll it back upon horror scenario?

thanks in advance!

there's no quick backup. 

My ISP lets me store 30 meg of stuff on the web (good enough for a novel I'm writing , since I tested it and can access it with fire fox)

I have two computers , one xp one currently in the toilet (had ubuntu 7.04 , played with drivers , crashed, install ubuntu 6.10 , play with vid drivers , crash ... currently still crashed while I d/l 7.04 live cd image) so if you get a similar set up installing SAMBA to get access to a shared folder on the xp machine is an option. Or even finding a freeware ftp server for xp and just ftp'ing to and from it on your home network. 

Backing up the settings is generally pointless, since if she all goes down you're throwing in the live cd and reformatting the drive completely.  Back up your data / mp3's , whatever you were working on instead. 

Oh yeah , don't forget to back up that cute image you're using as desk top wall paper. I keep forgetting that and it takes me simply ages to find it again ....

---

### Post by TURNER on 2007-04-30
Hi Nythain, 

Thanks for your response, 

As you have mentioned, the "main" configuration files would be enough, I basically don't want to start over, as I've already spent hours hacking at my xorg.conf file in order to accommodate my monitor.

I have toyed with the idea of backing up the home folder, I think theres a tutorial kicking about here somewhere, however most of my important files get saved on an external....therefore I dont think its necessary to go partitioning and stuff..

Could you possibly explain what the samba file is for?

---

### Post by TURNER on 2007-04-30
> Oh yeah , don't forget to back up that cute image you're using as desk top wall paper. I keep forgetting that and it takes me simply ages to find it again ....

Good thinking!! :)

---

### Post by koconnor100 on 2007-04-30
> **TURNER said:**
> Hi Nythain, 

Thanks for your response, 

As you have mentioned, the "main" configuration files would be enough, I basically don't want to start over, as I've already spent hours hacking at my xorg.conf file in order to accommodate my monitor.

I have toyed with the idea of backing up the home folder, I think theres a tutorial kicking about here somewhere, however most of my important files get saved on an external....therefore I dont think its necessary to go partitioning and stuff..

Could you possibly explain what the samba file is for?

SAMBA lets you share folders across the network , even with windows machines. If you can get it working. Thus the old drag and drop bit and that file is now on a windows machine (backed up) so if your linux goes down , reinstall SAMBA and grab it back. 

never did get samba working on ubuntu 6.10....

---

### Post by Nythain on 2007-04-30
the samba file is the configuration file for my samba server, the way i share files with the xp machines on my home network.

i had set samba up perfectly in edgy, then reinstalled to feisty without backing the configuration file for samba up (i wasnt expecting to many problems). Then it took me like 4 days to get samba working from scratch again, something just wasnt jiving right... so now its on my list of important configuration files that i have a back up of

---


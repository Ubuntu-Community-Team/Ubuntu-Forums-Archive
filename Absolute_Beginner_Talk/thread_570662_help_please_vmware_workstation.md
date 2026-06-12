---
title: "help please vmware workstation"
date: 2007-10-08
forum: Absolute Beginner Talk
---

### Post by powerfulx100 on 2007-10-08
Hi, how can i get windows XP on vmware workstation? does vmware come with xp or do I have to get xp from somewhere else because I have only ubuntu in my system. and how do I install Vmware-workstation-6.0.1-55017.i386.rpm ? thanx

---

### Post by dca on 2007-10-08
Well, first you need to purchase a Windows XP license from Microsoft or go to local store and purchase full install version of XPSP2 which costs anywhere from $85.00 for license only if you have installer or $199 - $299 at BestBuy in the US...
 
I believe VMWare "Player" is available from the Ubuntu repos through Synaptic, the VMWare 'Server' is available from vmware's website...

---

### Post by Discov3ry on 2007-10-08
If you want to install on Ubuntu, you can download a .deb packaged instead of .rpm. Rpm is for RedHat/Fedora/CentOS systems. 

VMware does not come with any OS installed. You can get some appliances based on all kinds of OS's here: [http://www.vmware.com/appliances/](http://www.vmware.com/appliances/) But you do need your own install media if you want to install a fresh OS in VMware.

---

### Post by powerfulx100 on 2007-10-08
alright. is there a way to install windows xp from iso image from ubuntu? and  why vmware server and not workstation? thank you :)

---

### Post by kapellen421 on 2007-10-08
vmware server allows you to create the virtualized os. Player will only play a virtualized os that has already been created.

---

### Post by wakeboarder on 2007-10-11
Player is free and can't create vmware images etc

Workstation costs $ and have many features

Server is free and can create images and run images but don't have all the bells and whistles that Workstation have.

Both player and server can be installed via Synaptic if you configure the corrects repos.

My guess is that server is in here:
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse

Good luck!
:guitar:

---

### Post by hyper_ch on 2007-10-11
and if you have a WinXP iso then you can mount that easily as cd in vmware(server/workstation) so that it boots from it and lets you isntall it.

---


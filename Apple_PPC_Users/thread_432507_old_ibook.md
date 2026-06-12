---
title: "old ibook"
date: 2007-05-04
forum: Apple PPC Users
---

### Post by gala.martin on 2007-05-04
hi all,
 I have just got an old ibook. it is the first model of ibook ever produced, featuring G3 366 MHz and 64 Mib RAM. Do you think I have any chance to install ubuntu there? I would go for the alternate ubuntu (possibly xubuntu) ppc feisty; since the alternate install process is not LIVE, I would prefer not to format the hard drive if not sure to get something.

 Thanks

---

### Post by 3rdalbum on 2007-05-04
You'll need to upgrade the RAM to at least 160 megabytes of RAM to run the Xubuntu Live CD with any semblance of speed. Check Apple's documentation on how to add RAM, and what sort of RAM it uses; then go to a computer store and buy some. Apple stores do overcharge on memory.

When you find that Xubuntu runs, download the Alternate CD, and install from there. I still advise against using the Live CD installer and especially on low-end machines.

---

### Post by stmiller on 2007-05-04
The G3 iBooks are 100% supported in Linux. Running Xfce4 you should be all set. After doing the standard ubuntu install, type
sudo apt-get install xubuntu-desktop

and that will install the xubuntu distro stuff.

There are more lighter window managers than this, also. If you want even more speed.

---

### Post by discoandy on 2007-05-04
I have a dual usb 500 mhz imac g3 with 368 megs of ram.  and I still couldn't get the normal live CD to work.  

Use the alternate install CD.  and if your screen is funky after installing, search the forums for the answer.  you may have to do some xorg.conf editing.  Nothing too scary though.

---

### Post by zalberico on 2007-05-06
For a computer with the specs you describe you might be better off going with fluxubuntu, its just ubuntu that uses the flux box window manager, (Very minimal and fast check out damn small linux for screen shots).  fluxbox is known for running on very very slow machines.  Good luck!

---

### Post by gala.martin on 2007-05-06
thanks everybody.

fluxbox and flwm are indeed my favourite window managers. but i will not use the ibook myself (my windows-addicted girlfriend will), so i need to put there a complete desktop enviroment. my idea was to install either gnome or xfce, then to manually disable most of the daemons and processes autoloading at startup, and eventually to recompile the kernel. but i need to properly install the system before doing that. 

From your words, I am afraid that i am going nowhere with 64megs RAM, and I really do not want to spend money to fix 7 yo hardware.

at present, a debian install is running on the ibook. it is really minimal (only shell login available), but the girl will get used ;)

thank you

---


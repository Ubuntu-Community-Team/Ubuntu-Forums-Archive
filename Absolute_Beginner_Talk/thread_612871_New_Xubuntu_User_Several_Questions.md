---
title: "New Xubuntu User: Several Questions"
date: 2007-11-14
forum: Absolute Beginner Talk
---

### Post by theirfour on 2007-11-14
New Xubuntu user here (I installed Ubuntu, but it ran too slowly for my computer, so I switched it out and am now very pleased). I'm fairly new to all of Linux and have some quick questions that I couldn't figure out after a couple of minutes of googling. Thus, I figure asking will get me better responses.

1) I'm running on a laptop, and when I originally installed Ubuntu it had all kinds of nice power management options. Xubuntu doesn't seem to have this - how can I access those?

2) I'm dual booting with Windows, and my laptop has a restore partition. Both of these partitions are automatically mounted and show up on my desktop. I don't really want them there as I have no reason to access them (all of my files are on my external hard drive, see next question). How can I get them to go away?

3) In the opposite of the above problem, my external hard drive mounts just fine automatically, but if I leave the computer idle for a long time, it is no longer recognized (the icon is still on the desktop, but attempting to navigate or access files from it results in error messages). I have to unmount/mount it again to get it to work. How do I keep it from getting away from me?

4) My external hard drive is NTFS formatted. Is that going to be a problem?

5) My wireless card is recognized by Xubuntu, but I'm used to Windows giving me an interface through which to connect to networks and such. Is there any such analog for Linux?

Anyway, thanks in advance for the help. As I said before, I'm sort of new to all of this, so any advice you have is appreciated.

---

### Post by Inxsible on 2007-11-14
2) Remove or comment the corresponding entries from the fstab and then restart. That will not mount them at all. ```
gksudo mousepad /etc/fstab
```

4) No

5) nm-applet (atleast in Ubuntu, I am not sure what the equivalent is in Xubuntu)

---

### Post by overdrank on 2007-11-14
Hi and welcome,
1. you can use gnome apps in xfce and vice versa, just use synaptic manager to locate and install them. Synaptic is located under applications, system. [https://help.ubuntu.com/community/SynapticHowto](https://help.ubuntu.com/community/SynapticHowto)
2. answered by Inxsible
3. What version of Xubuntu are you using, Feisty, Gutsy?
4. answered by Inxsible
5. again you can use synaptic but you can also right click on the top panel and choose add to panel and it has a network manager there. And for future reference [https://help.ubuntu.com/xubuntu/desktopguide/C/index.html](https://help.ubuntu.com/xubuntu/desktopguide/C/index.html)

---

### Post by mali2297 on 2007-11-14
Welcome to the forums.:-)

2) I think you need to edit fstab, this might help: 
[http://www.psychocats.net/ubuntu/mountwindows#fstab](http://www.psychocats.net/ubuntu/mountwindows#fstab). 

The link doesn't address your particular wish, but can give you a hint on how to proceed. Try changing "defaults" to "defaults,noauto" at the appropriate line. Of course, you can also follow Inxsible's advice and comment out the entry (add # to the beginning of the line).

5) Check out Wifi-radar. You can find it in Synaptic package manager.

Good luck.

---

### Post by mperry on 2007-11-27
If you want different tools, you could also look at gtkwifi or wicd.  Wicd will require you to remove any of the others since it aims to replace them all.  I've had issues I think with suspend/resume and the gnome network-manager so I removed it.  I only use wifi-radar in daemon mode which is apt-gettable and gtkwifi seems decent.

Most of all, after more than a few years with Linux and various/sundry graphical tools for things I've mostly settled on using command line tools where possible for things like wifi, CD burning, etc.  By the time I install, configure, learn, get frustrated, find something again and repeat; I could have had the original task done any number of times.  The wireless-tools are pretty easy to learn all in all.

---

### Post by crimesaucer on 2007-11-27
#1 Check out the Xfce Menu-->--Settings-->--Screensaver-->--Advanced for power management options... Stand-by, and Suspend, if your laptop can do that.

#2 edit your fstab the way mentioned, also... if you don't want any icons on your desktop at all, there is a setting for that in Xfce Menu-->--Settings-->--Desktop Preferences-->--Behavior: Desktop Icons = none

#3 you should be able to mount it permanently with read/write support at the boot up. It should be in the Ubuntu wiki page.

#4 I use Ntfs-3g and I can read and write to my windows partition... and it is always mounted: [http://www.ntfs-3g.org/](http://www.ntfs-3g.org/)

#5 I recommend Wicd: [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)
...there is also wifi-radar: [http://wifi-radar.systemimager.org/](http://wifi-radar.systemimager.org/)
and Xubuntu has the network manager which also works nicely once you set it correctly.

---


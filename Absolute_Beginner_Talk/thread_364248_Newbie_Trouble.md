---
title: "Newbie Trouble"
date: 2007-02-18
forum: Absolute Beginner Talk
---

### Post by dw426 on 2007-02-18
Hello everyone, after about 4 different distros and 1 video card change, I've finally found (so far), a distro that isn't giving me grief about hardware detection. I do need a little bit of assistance though. 

Problem 1. I installed Shorewall from Synaptic because I figured the safer the better. The issue is, it's nowhere to be seen in the Programs list, and a search of Add/Remove Programs looks as if it was never installed. Has anyone had this trouble?  (A search of "Shorewall" in the forum brought up only a couple of non-related posts from 2005). If it got borked, how can I make sure every bit of it is removed so as not to take a chance on some command or file getting confused by leftovers and screwing my system?

  If it gets removed, is it even really necessary?  I know my way around firewalls meant for Windows as most of them walk you hand by hand through setting it up or sets its own self up. Linux is a brand spanking new endeavor for me:) 

Question 2. I've got an Nvidia FX 5200 256 card, and the default driver seems to detect my resolution just fine, though it wants it on 75Hz and my screen usually goes to 60 and it won't let me change it. Is the default driver able to do 3D and things, or am I going to need to install the proprietary driver either through Synaptic or Automatrix?  Yeah, I brought up Automatrix, lol, some swear by it, some swear at it. Long ago I used Dapper and used Automatrix and it did a fairly good job. I'm probably going to need it for multimedia anyway.

Last Question. Repositories, how in the world do I enable the extras?  I tried through the command line and it threw a fit giving me "command not found or file directory not found" messages. I went straight to the source at Ubuntu's Wiki, but their pictures look nothing like what I see in Synaptics Repo settings.

  I apologize for all the questions, but I've been through 4 days with ATI and Linux, sound card issues and all kinds of good stuff. And now that I'm actually getting further with Ubuntu than I did with the other distros, I really want to get everything squared away so I can finally enjoy being away from Windows. Thank you ahead of time for reading through this and helping me.

---

### Post by sunexplodes on 2007-02-18
1) in synaptic, right click the package and select "mark for COMPLETE removal", and apply it.

2)There's a program called Envy which does a very easy install of the lastest nvidia drivers. 

3) Go into synaptic, click settings, select "repositories"
make sure all the repos you want are checked off.

---

### Post by Maestro23 on 2007-02-18
.

---

### Post by tommcd on 2007-02-18
1) For the firewall, uninstall shorewall as suggested and install firestarter from synaptic. It's very easy to use.
2) For the nvidia driver for the 5200, just use the nvidia-glx driver from the repos. Install by "method 1" from here, if you are on edgy:
[http://doc.gwos.org/index.php/Latest_Nvidia_Edgy](http://doc.gwos.org/index.php/Latest_Nvidia_Edgy)
or for Dapper:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)
If you really want the drivers from nvidia, then follow "method 2" from the above guides. But use only one. DO NOT have both nvidia drivers together. You must completely remove one driver before installing the other. Instructions are in the guides.
3) For automatix, use it if you want. But if you want to learn how to get the multimedia stuff yourself, it's quite easy:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)
[https://help.ubuntu.com/community/RestrictedFormats?highlight=%28restricted%29%7C%28formats%29](https://help.ubuntu.com/community/RestrictedFormats?highlight=%28restricted%29%7C%28formats%29)
In the long run you will be better off learning this stuff yourself rather than rely on automatix.
EDIT: For synaptic repositories, just click settings>repositories at the top of synaptic. Then check the boxes for universe, multiverse, backports, updates, etc. Source code you only need if you are going to compile programs yourself, or install from source, I think. Then just close that box and click the reload button on synaptic.

---

### Post by dw426 on 2007-02-18
Ok, I'll try the other suggestions then. Shorewall uninstalled just fine, however Firestarter is evidently no longer in the repos, the official ones at least. I'll get started on the Nvidia and codecs, thanks a BUNCH for your assistance!

---

### Post by tommcd on 2007-02-18
Firestarter should still be in synaptic. (I'm at work now so I can't check). But after you enable universe, multiverse, and backport repos it should be there. I believe firestarter is in the universe repository:
[http://packages.ubuntu.com/edgy/admin/firestarter](http://packages.ubuntu.com/edgy/admin/firestarter)

---


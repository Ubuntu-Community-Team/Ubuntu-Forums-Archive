---
title: "Machine unusable now"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by Jimmy4eyes on 2007-04-28
Okay, I've been using Dapper on an old desktop of mine with no problem for a while now, no data on it I can't do without.Everyone is talking about Fiesty so, I download the iso and burn it to a blank CD. Then I went for the install. It seemed to go fine, but then it all went tits up.

I basically now have a machine I can't use. Being an old Windows user, I immediately reached for my trusty boot floppy, thinking to reformat, reinstall Windows, then install Dapperfrom the CD, but it now tells me it can't reformat.

What it shows me when I boot up is a low res panel say "Failed to start the X server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?"

If I choose Yes, this is what I get:

X Windows System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux myname-desktop 2.6.15-28-386 #1 PREEMPT
Tue Mar 13 20:49:31 UTC 2007 i686
Build Date: 04 April 2007
Before reporting problems, check http:/wiki.x.org
to make sure that you have the latest version.
Module Loader present
markers: (--) probed, (**) from config file, (==) default setting,
(++) from command line, (!!) notice, (II) informational,
(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(++) Using config file: "/etc/X11/xorg.conf"

which could be written in Khazak for all the good it's doing me right now. Can anyone advise me please, other than taking a hammer to it of course.

---

### Post by Iarwain ben-adar on 2007-04-28
Hiya,

What do you have now? A Dapper or a Feisty machine? Installed or something else? (because you speak of not being able to format the drive)

To get a graphical interface, try this
```
sudo dpkg-reconfigure -phigh xserver-xorg
```


Iarwain

---

### Post by DezSP on 2007-04-28
Noo, sheathe thy hammers! This is a fairly common problem. Assuming you can get to a terminal, type in:

```
sudo dpkg-reconfigure xserver-xorg
```

Which should reinstate your xorg.conf. A quick reboot and hopefully X will kick into action and you can get a GUI.

Edit: Confounded, beaten to the mark. Just goes to show how common this is. :P

---

### Post by Jimmy4eyes on 2007-04-28
okay, I have the prompt, and typed in what was suggested, and here's what I got,

warning: Setting locale failed.
warning: Please check that your locale settings:
LANGUAGE = "en_GB:en",
LC_ALL = (unset),
LANG = "en_GB.UTF-8"
are supported and installed on your system.
warning: Falling back to the standard locale ("C").
Cannot set LC_ALL to default locale: No such file or directory usr/sbin/dpkg-reconfigure: xserver-xorg is broken or not fully installed

---

### Post by dougfractal on 2007-04-28
If you don't mind starting from scatch.

Boot from CD  and do a clean install reformating the hard drive. 

I've had that issue long ago, There is a google answer out there somewhere but it might just be easier to do a clean install than upgrade.

---


---
title: "MP3 help"
date: 2007-07-07
forum: Absolute Beginner Talk
---

### Post by nynoah on 2007-07-07
Help for some reason I can not play MP3s any more.  I have always been able to in the past.  I had my computer configured to the correct way.  But for some reason I can not now.  I can play M4a and other types of files, but not MP3 for some reason.   I have tried reinstalling to no avail.

---

### Post by deadgobby on 2007-07-07
Is it all or just one media player?

---

### Post by Qwerty_ on 2007-07-07
What version of Ubuntu are you currently running?

Perhaps this will help you

[https://help.ubuntu.com/community/RestrictedFormats/MP3](https://help.ubuntu.com/community/RestrictedFormats/MP3)

---

### Post by nynoah on 2007-07-07
seems to be all...........noatun does not work and neither does amarock

---

### Post by nynoah on 2007-07-07
Fiesty on a 64 bit AMD

---

### Post by nynoah on 2007-07-07
Seems no one has a clue on this........I swear I waste more time that it is worth on Ubuntu

---

### Post by RomeReactor on 2007-07-07
Hi. Are you on Gnome (Ubuntu) or KDE (Kubuntu)? If you're on Ubuntu, try playing them with Rhythmbox; if it doesn't play them, you'll need **gstreamer0.10-plugins-ugly**. I think Amarok uses **xine**, so you'll need:
```
sudo apt-get install gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse libxine1 libxine1-ffmpeg libxine-extracodecs
```
if you don't have them already.

---

### Post by nynoah on 2007-07-07
I am in KDE.....a little while the Gnome section stopped working.....I think that is something to do with grafix....I will worry about that another time.  This is just recent and the other is from months ago.

Here is what happened when I typed your code.




noah@noah-desktop:~$ sudo apt-get install gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse libxine1 libxine1-ffmpeg libxine-extracodecs
Password:
Reading package lists... Done
Building dependency tree
Reading state information... Done
gstreamer0.10-plugins-ugly is already the newest version.
gstreamer0.10-plugins-ugly-multiverse is already the newest version.
libxine1 is already the newest version.
libxine1-ffmpeg is already the newest version.
libxine1-ffmpeg set to manual installed.
libxine-extracodecs is already the newest version.
The following packages were automatically installed and are no longer required:
  kde-core libxalan110 blop kdelibs libxerces27
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
noah@noah-desktop:~$

---

### Post by nynoah on 2007-07-07
From what I gather, it says I already have it installed

---

### Post by RomeReactor on 2007-07-07
Yes, they are. Try opening Amarok in the terminal:
```
amarok
```
and try to play a .MP3 file, and see if it leaves any error messages there.

---

### Post by nynoah on 2007-07-07
Wow you rock....it works.....

I have been trying to get help online with this for DAYS.....no one could help.  BIG thanks to you for taking the time to help with my strange problem.




You would not know how I could get my Gnome back.  I think it is something to do with the display drivers.  I can not even get it to show up in fail safe mode.  All I get is a blue screen with white bars top and bottom

Noah

---

### Post by RomeReactor on 2007-07-07
Sorry, the only thing I can think of at the moment to restore your Gnome desktop is to do an update and try to fix broken packages:
```
sudo aptitude update && sudo aptitude install -f
```
though I don't know if this will cause you any other problems; sorry.

**EDIT**: Or, you could try [completely removing the Ubuntu desktop]("http://www.psychocats.net/ubuntu/purekde") (follow the **Remove Ubuntu** instructions in orange) and then installing it again:
```
sudo aptitude install ubuntu-desktop
```

---

### Post by nynoah on 2007-07-07
Check this out below..........when I type that in, it wants to take out the amarock Xine package......Should I say yes?  I am not sure if this will revert me back to no MP3s again..........I wonder why this comes up?





noah@noah-desktop:~$ sudo aptitude update && sudo aptitude install -f
Get:1 [http://www.getautomatix.com](http://www.getautomatix.com) feisty Release.gpg [189B]
Ign [http://www.getautomatix.com](http://www.getautomatix.com) feisty/main Translation-en_US
Hit [http://www.getautomatix.com](http://www.getautomatix.com) feisty Release
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Translation-en_US
Get:3 [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial Release.gpg [191B]
Ign [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial/main Translation-en_US
Get:4 [http://wine.lowvoice.nl](http://wine.lowvoice.nl) feisty Release.gpg [191B]
Ign [http://wine.lowvoice.nl](http://wine.lowvoice.nl) feisty/main Translation-en_US
Get:5 [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty Release.gpg [189B]
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/free Translation-en_US
Get:6 [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty Release.gpg [189B]
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/free Translation-en_US
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/main Translation-en_US
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Translation-en_US
Ign [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security Release
Hit [http://wine.lowvoice.nl](http://wine.lowvoice.nl) feisty Release
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/non-free Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/non-free Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/free Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/non-free Translation-en_US
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty Release
Hit [http://www.getautomatix.com](http://www.getautomatix.com) feisty/main Packages
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/multiverse Translation-en_US
Get:9 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Translation-en_US
Get:10 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release.gpg [191B]
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Translation-en_US
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) feisty-commercial/main Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main Packages
Ign [http://wine.lowvoice.nl](http://wine.lowvoice.nl) feisty/main Packages
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/free Packages
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/universe Translation-en_US
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates Release
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/free Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/multiverse Packages
Hit [http://wine.lowvoice.nl](http://wine.lowvoice.nl) feisty/main Packages
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/non-free Packages
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/free Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/universe Packages
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/non-free Packages
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/free Packages
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/non-free Packages
Ign [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/non-free Sources
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/free Packages
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/free Sources
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/non-free Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-backports/multiverse Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/free Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) feisty-updates/restricted Packages
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/non-free Packages
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/free Sources
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/non-free Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/free Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/non-free Packages
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/free Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates/multiverse Packages
Hit [http://medibuntu.sos-sts.com](http://medibuntu.sos-sts.com) feisty/non-free Sources
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) feisty/non-free Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-security/multiverse Packages
Fetched 11B in 1s (7B/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done
The following packages will be automatically REMOVED:
  amarok-engines amarok-xine
The following packages will be REMOVED:
  amarok amarok-engines amarok-xine
0 packages upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 32.6MB will be freed.
Do you want to continue? [Y/n/?]

---

### Post by RomeReactor on 2007-07-07
You could go ahead, and re-install amarok later; or you could cancel that and try the other method I just added to my previous response (sorry for the delay, by the way).

---

### Post by nynoah on 2007-07-07
I tried your other method

---

### Post by nynoah on 2007-07-07
I am trying to access my /etc/X11/xorg.conf but for some reason when I try to run that comand, it will not let me do it as Root?  Is there another way to get into it?  I am trying to config beryle

---

### Post by nynoah on 2007-07-07
Nope did not work with the Ubuntu...............I get a solid blue screen and I have to ctrl alt backspace to get out of that

---

### Post by RomeReactor on 2007-07-07
If you're trying to make changes to xorg.conf, it would be a good idea to make a backup first:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```
that way, if somehow the xorg.conf file becomes corrupted, you can restore your backup like this:
```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```
to edit the file (you're still in KDE, right?):
```
kdesu kate /etc/X11/xorg.conf
```

**EDIT**: Do you have Beryl or Compiz (Desktop Effects) enabled? If so, were they enabled when you tried to go into Gnome? you could try turning them off and then log in to Gnome, to see if the problems related to that.

---


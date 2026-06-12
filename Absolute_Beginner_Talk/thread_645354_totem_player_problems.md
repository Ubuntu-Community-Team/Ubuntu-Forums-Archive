---
title: "totem player problems"
date: 2007-12-19
forum: Absolute Beginner Talk
---

### Post by swishthetoad on 2007-12-19
so i just loaded ubuntu last weekend and it really hasn't given much trouble until today when my boyfriend and i wanted to watch a dvd.  we put the movie in and the player refused to work saying it didn't have the proper plug-ins.  

i went through all of the threads on the player and it seems none of them work. 

maybe i'm just missing something. 

please help.

seems like everything i download or try to get i don't have the proper plug-ins for.  did i do a bad boot of ubuntu? or is this normal...?

---

### Post by blueberry17 on 2007-12-20
Try VLC player instead of Totem. Totem is usually very unreliable when playing video. You can either get VLC through the Synaptic Package Manager (go to System > Administration > Synaptic Package Manager). However, if you use Synaptic, make sure to turn on all of your repositories (they can be found under Repositories in one of the Synaptic menus). After you enable all of the repositories, click search and type in "vlc". Check the check box next to the package that says just simply "vlc" and click mark changes. Then at the top of Synaptic click the "Apply Changes" button. If Synaptic pops up a message asking if it is ok to install the dependent packages (the ones VLC needs to run) as well, just click OK. After the installation is complete. VLC should be in the Applications menu.

If you want to install VLC through the Terminal, just make sure again that all of the Repositories are enabled. Type in Terminal

sudo apt-get install vlc

and Terminal will do the rest. VLC should now be in the Applications menu. Good luck!

---

### Post by doorknob60 on 2007-12-20
Try this [http://ubuntuforums.org/showthread.php?t=645288](http://ubuntuforums.org/showthread.php?t=645288) (look at 2nd post)

---

### Post by swishthetoad on 2007-12-20
so i loaded vlc. download was smooth.  even have it in the applications menu. i put the dvd in and nothing happens. load up vlc and doesn't see the disc. 


it's on my desktop now
just taunting me...

---

### Post by RomeReactor on 2007-12-20
Hi. Try doorknob60's suggestion; you could also try with Totem-Xine:
```
sudo apt-get install totem-xine libxine1 libxine1-gnome libxine1-ffmpeg libxine1-plugins
```

---

### Post by swishthetoad on 2007-12-20
i tried the second thread and got this:


Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/multiverse Translation-en_US
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release   
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy-proposed/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Sources
Fetched 2B in 1s (2B/s)
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libdvdcss2 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libdvdcss2 has no installation candidate
--
confused...

---

### Post by RomeReactor on 2007-12-20
Did you add the repositories? they didn't show up in your update; try this:
```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
```
```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```
and lastly:
```
sudo apt-get install libdvdcss2 libdvdread3 libdvdnav4 totem-xine libxine1 libxine1-gnome libxine1-ffmpeg libxine1-plugins
```

---

### Post by doorknob60 on 2007-12-20
Sounds like you forgot to add the Mediabuntu repositories to your sources.list file.

Type this into terminal:
```
gksu gedit /etc/apt/sources.list
```

Then add this to the bottom of the text file that opens and save it:
> deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) gutsy free non-free

Then run this in terminal again:
```
sudo apt-get update && sudo apt-get install libdvdcss2 libdvdread3 libdvdnav4
```

EDIT: rome beat me -.-

---

### Post by swishthetoad on 2007-12-20
it worked. 
yay. 

thank you so much.

---


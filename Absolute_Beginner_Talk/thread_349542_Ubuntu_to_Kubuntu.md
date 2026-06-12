---
title: "Ubuntu to Kubuntu?"
date: 2007-01-30
forum: Absolute Beginner Talk
---

### Post by Effect on 2007-01-30
Okay I'm interested in trying out KDE so I'm installing it through a guide I found. [http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)

I have a question though. If I happen to like it more then gnome and I uninstall gnome does that classify the OS as Kubuntu as a result or is it still considered to be Ubuntu?

Thanks.

---

### Post by BarfBag on 2007-01-30
Ubuntu and Kubuntu are exactly the same.  Kubuntu even has the same update sources.  If you install KDM and KDE and uninstall GDM and GNOME, you'll have a system identical to Kubuntu.  The old boot art (the logo as it's booting) will probably stay the same, though.

---

### Post by sonny on 2007-01-30
That would be Kubuntu, as I understant (someone else correct me if I'm wrong) the only difference is the Desktop Enviroment, there's no special "thing" about Kubuntu, it's only Ubuntu with a KDE look.

---

### Post by jvc26 on 2007-01-30
Well not strictly speaking as you still will be using gnome apps I'm guessing - kubuntu uses konquerer instead of nautilus, koffice rather than OO and other things.
Il

---

### Post by Darkdelusions on 2007-01-30
When i installed KDE on my Ubuntu install it messed up my menus Nothing big just threw a bunch of stuff in random menus.....

I found the Kbuntu 6.10 disk buggy and things didn't work right for me.. However it could have been just me. :)

---

### Post by rfdparker2002 on 2007-01-30
Well (if you didn't already know this) to install kde and the recommended apps is to install the 'kubuntu-desktop' package which depends on everything you need, but make sure you run it from a console (as the graphical package installers don't always support the installion questions) because part way through, when installing the kdm package it will ask you which one (kdm or gdm) you want to appear at start-up (both packages will remain installed), also it's probably best to use aptitude instead of apt-get, as if you decide you no-longer want kde, if you remove the kubuntu-desktop package with aptitude (as long as you installed it with aptitude), it will remove everything that was installed with that package, so you should be able to simply run:
```
sudo aptitude update
sudo aptitude dist-upgrade
sudo aptitude install kubuntu-desktop
```

Then reboot and on your display manager's menu under session you will have KDE as well as Gnome, so just pick it, also if you want it might be a good idea (after the doing the above) to add a repo from [this page]("http://kubuntu.org/announcements/kde-356.php") for a newer version of KDE and one from [this page]("http://kubuntu.org/announcements/amarok-1.4.4.php") for a newer version of the legendary Amarok to your sources.list, then run a dist-upgrade.

Also note:
[LIST]
 [*]You are still running Ubuntu just with KDE as well, Kubuntu is just a name for a specialised KDE-only from initial-install CD type thing[*]Kubuntu/kubuntu-desktop, don't come with/install KOffice, just OOo, as KOffice, isn't good enough to replace OOo yet
[*]For non-free codecs in KDE apps such as Amarok and Kaffiene install the libxine-extracodecs package, which should be available if you have enabled all your repos
[*]The KDE equivalent to Synaptic is Adept, which is installed, and there are 2 forms of: The simple version - Adept installed, A.K.A Add/Remove Programs and the full version, Adept Manager which can be found in the System menu of the K-Menu
[*]Give Konqueror a try for web browsing, it's not as good as firefox, but starts faster and works better with kde
[*]Kopete is the GAIM Equivalent
[/LIST]
Happy KDEing!

---


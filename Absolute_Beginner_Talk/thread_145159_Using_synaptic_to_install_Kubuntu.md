---
title: "Using synaptic to install Kubuntu"
date: 2006-03-15
forum: Absolute Beginner Talk
---

### Post by Cloudy on 2006-03-15
So I left my dialup on this morning to get the necessary packages to install kubuntu-desktop, but I'm having some problems. I think there were a couple packages that didn't download, because whenever I login to my machine the login has the Kubuntu splash and login screen, and as it begins to log me in the background is the default Kubuntu background - but then it suddenly switches over to GNOME. I rebooted and checked the Sessions, and there's only GNOME/Failsafe/Default. 

I'm assuming that I'm going to have to download the kubuntu-desktop package again, but before I do, is there anything I need to do to possibly enable KDE.. ?

---

### Post by Jucato on 2006-03-15
If the download of kubuntu-desktop was complete, it should have asked you whether you would want GDM or KDM to be your default display manager, and a KDE session would be listed there. No need to do any other thing to enable KDE.

My guess is that not all packages have been downloaded successfully. Perhaps there's a way to continue downloading and setting up from Synaptic.

---

### Post by aysiu on 2006-03-15
Can you try just going to Applications > Accessories > Terminal and typing ```
sudo apt-get update
sudo apt-get install kubuntu-desktop
```?

If you don't have it fully installed, it'll list a bunch of packages to be installed and ask whether you want them installed. If that happens, say "no" for now and report back in this thread that it wasn't fully installed.

If it is installed, it'll say kubuntu-desktop is already the newest version.

---

### Post by Adrian on 2006-03-15
You shouldn't have to do more than install **kubuntu-desktop**

[QUOTE=Fenyx]My guess is that not all packages have been downloaded successfully. Perhaps there's a way to continue downloading and setting up from Synaptic.[/QUOTE]

Since kubuntu-desktop is a meta-package, the properly downloaded packages should still be cached. This means that Synaptic probably won't have to download them again.

---

### Post by Cloudy on 2006-03-15
[QUOTE=Fenyx]If the download of kubuntu-desktop was complete, it should have asked you whether you would want GDM or KDM to be your default display manager, and a KDE session would be listed there. No need to do any other thing to enable KDE.

My guess is that not all packages have been downloaded successfully. Perhaps there's a way to continue downloading and setting up from Synaptic.[/QUOTE]

It did ask me, and I selected KDM. 

@aysiu; I'll be sure to do that later tonight. ^^; I'm doing some things on this PC (different one..) right now. X3

@Adrian: Alright. ^^

---

### Post by Cloudy on 2006-03-16
[QUOTE=aysiu]Can you try just going to Applications > Accessories > Terminal and typing ```
sudo apt-get update
sudo apt-get install kubuntu-desktop
```?

If you don't have it fully installed, it'll list a bunch of packages to be installed and ask whether you want them installed. If that happens, say "no" for now and report back in this thread that it wasn't fully installed.

If it is installed, it'll say kubuntu-desktop is already the newest version.[/QUOTE]

It wasn't fully installed, because I just got that package list when I did sudo apt-get install kubuntu-desktop. 
What now?

---

### Post by Cloudy on 2006-03-16
Found out which packages aren't getting installed.

```

W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/konversation/konversation_0.18-1ubuntu3_i386.deb
  Error reading from server - read (104 Connection reset by peer)


W: Failed to fetch http://us.archive.ubuntu.com/ubuntu/pool/main/k/kdegraphics/libkscan1_3.4.3-0ubuntu2_i386.deb
  Error reading from server - read (104 Connection reset by peer)

```

---

### Post by Cloudy on 2006-03-16
Okay.. I tried to redownload the packages and it started redownloading where it just left off, then installed the packages. When I logged out, KDE was an option in the Sessions menu :D!

Now.. I just gotta fiddle with some defaults and stuff and I'm good to go. xD

---


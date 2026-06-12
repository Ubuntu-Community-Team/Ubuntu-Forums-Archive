---
title: "Gnome to KDE"
date: 2006-05-25
forum: Absolute Beginner Talk
---

### Post by alienexplorers on 2006-05-25
How do I go about switching from gnome to kde without having to reload everything or running dual boot.  I know I have to install kde, but how do I get rid of the gnome software.

---

### Post by niviche on 2006-05-25
To install Kubuntu (the KDE version of Ubuntu), type in a terminal:

```

gksudo aptitude install kubuntu-desktop

```

you can then log-in to Kubuntu when you open a session (i.e. when you enter your username and password.

To uninstall the Gnome environment and its default programs, refer to this thread: [HowTo: Fully Uninstall the ubuntu-desktop meta-package](http://ubuntuforums.org/showthread.php?t=96046).

---

### Post by nalmeth on 2006-05-25
sudo apt-get install kubuntu-desktop

---

### Post by hotbrainz on 2006-05-25
Another way of installing it would be:

Download the Kubuntu installer CD.
Burn it.
Pop it into your Ubuntu box.
Go to System > Administration > Synaptic Package Manager
Go to Edit > Add CD-ROM
Add it as a source.
Go to Settings > Repositories
Uncheck every box except the one you just added
Click Reload
Search for kubuntu-desktop
Mark it for installation.
Apply Changes.
Log out.
Click Session.
Select KDE.
Log in.

(As quoted by Aysiu) Worked fine for me :)

Then you can choose your desktop before each session.

---


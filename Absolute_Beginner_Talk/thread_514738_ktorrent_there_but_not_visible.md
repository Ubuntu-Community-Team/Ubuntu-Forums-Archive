---
title: "ktorrent there but not visible"
date: 2007-08-01
forum: Absolute Beginner Talk
---

### Post by kman14 on 2007-08-01
i'm using ubuntu feisty and have ktorrent installed only i can't find it.
it says it's running in the system monitor and i can download a torrent with it - it just disappears.
if i type ktorrent in the terminal it says it's running.
when i first used it the gui was there now it's gone.
i tried installing it again from the website (deb), but it's still the same.

---

### Post by mathewb on 2007-08-01
It may be an issue that you are using Gnome and it's a KDE application. It may not be compatible with Gnome's system tray. A good gtk+ alternative is Azureus.

try running the command for launching KDE's panel. I think it is "kpanel" or "kde-panel". it has been a couple years since i ran KDE.

---

### Post by forestpixie on 2007-08-01
no it's fine with gnome - I use it all the time, is it not at the top with volume control

---

### Post by ugm6hr on 2007-08-01
> **forestpixie said:**
> no it's fine with gnome - I use it all the time, is it not at the top with volume control
KTorrent has an option to minimise to system tray.  As default it doesn't (or at least the version in Ubunut repo doesn't).  The icon looks like a green and red arrow.

Sounds obvious, but, just in case...  If it is running in System monitor - it might be minimised on another desktop, or in the system tray.

If it's definitely not there, then perhaps just kill it from Terminal and relaunch.

---

### Post by kman14 on 2007-08-01
thanks for the replies.

there's nothing in the system tray and it's not on any of the other desktops but when i r/click the torrent i was downloading and tell it to open it with ktorrent it says the following:

> You are already downloading this torrent,  the list of trackers of both torrents has been merged.

i think i may have downloaded ktorrent through automatix originally, so i tried to uninstall it and install it from a .deb.
would it be worth taking it completely off the computer and re-installing it?
would that involve using the purge command and if so how would i enter that?

thanks.

---

### Post by atomkarinca on 2007-08-01
you can do it by typing

sudo aptitude purge ktorrent. when you do that it doesn't delete your torrents so it should be no problemo.

---

### Post by Happy_Man on 2007-08-01
Have you gone in the settings dialog and set it so that it shows an icon when you close it?

---

### Post by kman14 on 2007-08-02
happy_man, do you mean the settings dialog for ktorrent?
if that's right, how would i do this if i can't find the program?

thanks.

---

### Post by RomeReactor on 2007-08-02
Hi. Is this the only program that disappears? Are you using a different theme (not the default "Human")? If you kill Ktorrent from the System Monitor and start it again through the terminal (just type **ktorrent** and press enter) does it leave any error messages there?

---

### Post by kman14 on 2007-08-02
RomeReactor when i type ktorrent in the terminal it just says:

> karl@karl-desktop:~$ ktorrent
kbuildsycoca running...
Reusing existing ksycoca
kio (KService*): WARNING: The desktop entry file /usr/share/applications/DefaultPlugins.desktop has Type=Link instead of "Application" or "Service"
kio (KService*): WARNING: Invalid Service : /usr/share/applications/DefaultPlugins.desktop
kio (KSycoca): ERROR: No database available!


then it looks like it's going to start and pops up this message:

> The file where the data is saved of the torrent "Greys.Anatomy.S03E21.HDTV.XviD-XOR.avi" is missing, do you want to recreate it?


i've uninstalled it, purged it and the above keeps appearing - i don't know if it's part of the problem.

i have changed my desktop a fair bit.
i'm using gdesklets
compiz fusion - switched off currently.
i recently installed a new graphics card but everything went fine with that.

i also started using deluge once ktorrent didn't work properly and now for some reason that won't start at all.
entering deluge into the terminal gives this:

> karl@karl-desktop:~$ deluge
no existing Deluge session
deluge_core; using libtorrent 0.11.0.0. Compiled with NDEBUG value: 1
Applying preferences
deluge_core; using libtorrent 0.11.0.0. Compiled with NDEBUG value: 1
terminate called after throwing an instance of 'boost::filesystem::filesystem_error'
  what():  boost::filesystem::default_name_check: default name check already set
Aborted (core dumped)

maybe i should just use bit tornado

thanks

---

### Post by RomeReactor on 2007-08-02
Open Nautilus in your home folder, press CTRL+H to see the hidden files and folders, look for a **.ktorrent** folder and delete it. Then try opening Ktorrent again.

---

### Post by kman14 on 2007-08-02
there's no .ktorrent folder.
there is a .kde folder and within that is a ktorrent folder - should i delete that?

thanks.

---

### Post by RomeReactor on 2007-08-02
Look inside it and see if there are any configuration files; if there are, delete it. The point is to remove the config files so that they get re-created upon starting Ktorrent again. Also, find Ktorrent in Synaptic and see if it marks it as a broken package.

---

### Post by kman14 on 2007-08-02
rome_reactor if i go into .kde/share/config there is a file called ktorrentrc - is this the file?
i'm guessing it is.

the other thing is if i go into .kde/apps/ktorrent there are three folders  (tor0, tor1, tor3) can i delete those aswell? they are the three torrents i've downloaded thus far.

thanks for your help.

---

### Post by forestpixie on 2007-08-02
should be ok to copy those three elsewhere, assuming that it's not them that caused a problem - then delete everything else

let ktorrent start again, once you know it's starting ok you can copy them back - then right click each let ktorrent check data integrity and it should just carry on from where it got to

if however it crashes again delete them :)

---

### Post by kman14 on 2007-08-02
thanks guys 
that seems to have fixed it.

thanks for all the help.

---


---
title: "Problems connecting with VNC"
date: 2008-04-03
forum: Absolute Beginner Talk
---

### Post by Alekth on 2008-04-03
Hello,

in the last few days I've been having problems connecting to my ubuntu box from the internet. it's my first Ubuntu installation and about a week old so it's probably messy with me trying out packages.

I was able to connect before (to the gnome GUI) with vncviewer. Once that stopped working (connection refused), I tried the tightvnc viewer, which tried to connect while stating "Status: Security type requested" and then Authentication failed.

I uninstalled Firestarter in the process of trying to get it to work, the computer is not behind a router. Remote desktop settings are set to allow viewing/control, ask for password (which is correct), no confirmation from local host required.

It seems something somewhere is set to request encryption.. any suggestion where to look for that? Possibly from the command line (I currently have SSH access).

---

### Post by aaguilar4 on 2008-04-05
you might just want to reinstall vncviewer to see if that resets any of the settings to their default.
try
sudo apt-get purge vncviewer 
sudo apt-get install vncviewer
then just try it over again.  I recently started using vncviewer, so I don't know how it all works just yet.  I was able to connect to my laptop from a windows computer using a password.  It all worked fine but then again I didn't change any of the settings from the command line or anything... just using the GUI.

---

### Post by ghost_ryder35 on 2008-04-05
assuming this is Gutsy with the original VNC version make sure your screen is LOCKED when attempting to connect.  What type of computer are you trying to connect from?

---


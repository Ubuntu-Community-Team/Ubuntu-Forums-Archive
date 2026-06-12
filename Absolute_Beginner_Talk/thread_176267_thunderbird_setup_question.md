---
title: "thunderbird setup question"
date: 2006-05-14
forum: Absolute Beginner Talk
---

### Post by dubhansen on 2006-05-14
i'm in the process of setting up my laptop which i used to run winxp on it. i saved my email folder which contains all my sent/received emails and i cant seem to find the folder i'm supposed to put it in now.  i'm using the latest version of thunderbird and ubuntu 5.1. if anyone can help i would greatly appreciate it. 

i tried the search feature but couldnt find anything that covered what i need. 

thanks

---

### Post by aysiu on 2006-05-14
Did you save your entire Thunderbird Application Data folder from Windows or just the individual emails themselves?

---

### Post by dubhansen on 2006-05-14
i saved the entire application data folder.  i've transferred the files from one machine to another in the past but they were both windows machines. i'm trying to make the migration over to linux now so a lot of the system is new to me.

---

### Post by aysiu on 2006-05-14
Two more questions. Are you using Gnome or KDE? Where are you currently storing your Thunderbird folder--on a Windows partition? On a separate USB drive?

---

### Post by dubhansen on 2006-05-14
using gnome and the folder is stored on a external usb drive.

---

### Post by aysiu on 2006-05-14
Okay.

In Gnome, go to Places > Home.

A Nautilus file browser window will open to /home/dubhansen

Press Control-H

A whole bunch of hidden folders should appear. If you've launched Thunderbird in Gnome already, there should be either a .thunderbird or a .mozilla-thunderbird folder there.

That's your "Application Data" folder.

Look inside that folder. You should see a whole bunch of profile folders (or maybe just one). Delete whatever's in there.

Then, pop in your USB drive. It should appear on your desktop and then open.

Go to your Thunderbird folder. Copy those profiles in there (and any other files (like profile.ini) to your .thunderbird or .mozilla-thunderbird folder.

If you don't have a .thunderbird or .mozilla-thunderbird folder, you may have to create one. Use .thunderbird if you're using Thunderbird from the Mozilla website. Use .mozilla-thunderbird if you're using Thunderbird from Ubuntu.

---

### Post by dubhansen on 2006-05-14
thanks for your help. i got it working now. i appreciate it.

---


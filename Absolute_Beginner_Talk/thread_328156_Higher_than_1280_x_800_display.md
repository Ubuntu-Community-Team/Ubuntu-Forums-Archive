---
title: "Higher than 1280 x 800 display?"
date: 2006-12-30
forum: Absolute Beginner Talk
---

### Post by misawa on 2006-12-30
I've installed Edgy on my Gateway laptop and have installed 915resolution so that I can get widescreen of 1280 x 800.  While this is okay, I'd like to be able to get a higher resolution, maybe 1440 x 900, 1680 x 1050, and 1920 x 1200.  I've used sudo dpkg-reconfigure -phigh xserver-xorg to add the 1280 x 800, but even when I select the other resolutions that I want, they never appear in System > Admin > Screen Resolution - all I ever see are the one I'm using, plus 1024, 800, and 640 4:3 ratio resolutions.  Am I running in to a limit on my video card?  I'll have to boot back in to Xp to check what it allows me to use, but I seem to recall it supporting some pretty high resolutions.

Thanks,
Galen

---

### Post by Steggy on 2006-12-30
It may just be a simple matter of editing your xorg.conf file. That's always been the case for me, since Ubuntu never seems to set my resolution high enough (I'm always stuck on 1024x768 after a reinstall.)

First, do this:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```

That will create a backup of your xorg.conf so if something goes wrong, you can simply return to the old file with this command:

```
sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf
```

Next, open up your xorg.conf for editing:

```
sudo gedit /etc/X11/xorg.conf
```

Scroll down until your see 'Section "Screen"'. Below there is where you need to edit. There should be several indented headings called 'Subsection "Display"'. Under each of those, you should see a line beginning with "Modes", followed by a listing of resolutions. Add your desired resolution to the beginning of each "Modes" line, then save the file.

Now, simply restart your xserver (Ctrl+Alt+Backspace) or restart your computer, whichever your prefer. That should get your new resolution working.

---


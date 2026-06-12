---
title: "[SOLVED] Restoring Nautilus with out Psychocats' script"
date: 2007-08-11
forum: Absolute Beginner Talk
---

### Post by Limitlesschannels on 2007-08-11
Originally I replaced nautilus with thunar as the default file manager using the psychocats' downloadable scripts from [http://www.psychocats.net/ubuntu/nonautilusplease](http://www.psychocats.net/ubuntu/nonautilusplease) .  Somehow my nautilus files screwed up and now when i tried to restore nautilus as the default file manager with the restoration script off the page it is unsuccessful:
```


limitlesschannels@Compy:~/Desktop$ ./restorenautilus.sh

Restoring Computer .desktop file


Restoring Nautilus .desktop file


Restoring folder handler .desktop file


Restoring Home .desktop file


You're missing a Network backup file--nothing to restore. If you had Thunar as your previous default file manager, this is normal.


Nautilus should now be your new default file manager in Gnome again


```
Since the script seems to rely entirely on the back up file created when the first script to replace nautilus was ran, I can't seem to fix it.  How can I reinstall nautilus safely?

---

### Post by felicity on 2007-08-11
Is Nautilus not working as your default file manager now? 

According to what you posted, it states that the error you received is normal if you previously had Thunar as your default file manager.

---

### Post by Limitlesschannels on 2007-08-11
Nautilus is my default file manager; or at least it was before i installed thunar.  I am running Gnome/Ubuntu-Feisty.  Nautilus works when I run it from terminal, double-click a desktop icon, etc.   but access through the panel "places/home folder" loads thunar.

---

### Post by capink on 2007-08-11
Try running these commands:

```

sudo sed -i 's/^Exec=.*/Exec=nautilus --no-desktop computer:/' /usr/share/applications/nautilus-computer.desktop
sudo sed -i 's/^Exec=.*/Exec=nautilus --no-desktop %U/' /usr/share/applications/nautilus-folder-handler.desktop
sudo sed -i 's/^Exec=.*/Exec=nautilus --no-desktop --browser %U/' /usr/share/applications/nautilus.desktop
sudo sed -i 's/^Exec=.*/Exec=nautilus --no-desktop/' /usr/share/applications/nautilus-home.desktop
sudo sed -i 's/^Exec=.*/Exec=nautilus-file-management-properties/' /usr/share/applications/nautilus-file-management-properties.desktop
```

If this does not work try reinstalling nautilus

---

### Post by felicity on 2007-08-11
Uh oh. 

Here's something you can try:

To restore Nautilus as the default:

   1. Launch Nautilus
   2. Right-click a random folder on your filesystem
   3. Click "Properties"
   4. Click "Open with.." tab
   5. Choose "File Manager" (or "Open folder")
   6. Click OK
(from [http://unbreakablemj.blogspot.com/]("http://unbreakablemj.blogspot.com/"))

---

### Post by Limitlesschannels on 2007-08-11
capink:  the commands did nothing.
felicity:  It is already set at "open folder"
to restate in case it was confusing, both nautilus and thunar work for me; well, thunar doesn't run very well, but it is useable.

before I attempt to reinstall nautilus through synaptic, will this wipe out my desktop?  Will the icons be restored once I reinstall?  Is there anything similar that might cause me problems by doing this?

---

### Post by capink on 2007-08-11
The script only modify some *.desktop files in /usr/share/applications
these files can be replaced with the originals.
to obtain the original files follow the following steps:

```
aptitude download nautilus
```

now you will have a deb package in you current directory. Extract the deb package as follows:

```
dpkg --extract /path/to/deb ./tmp
```

now replace the *.desktop files with the originals:

```
sudo cp -vf ./tmp/usr/share/applications/*.desktop /usr/share/applications

```

---

### Post by Limitlesschannels on 2007-08-12
excellent, thank you, it worked.

---

### Post by lanort2 on 2008-03-28
For me alle the commands above did not work. (When I clicked on Places I always received an error)

Additonally I reinstalled nautilus:
```
sudo apt-get remove nautilus
sudo apt-get install nautilus
```
This **worked**.

---


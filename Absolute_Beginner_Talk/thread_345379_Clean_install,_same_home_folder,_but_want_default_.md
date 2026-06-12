---
title: "Clean install, same home folder, but want default DE settings"
date: 2007-01-24
forum: Absolute Beginner Talk
---

### Post by ajifans on 2007-01-24
I think there's probably a simple answer to this one:

 - I want to make a clean install of Ubuntu and Kubuntu, reformatting my / and swap partitions but keeping my /home partition.

 - However I want allow the installer to overwrite my current Gnome and KDE settings and give me the default ones.  

Is there any easy way to do this?

---

### Post by j19sch on 2007-01-24
Your Gnome and KDE folders are saved in your home folder.
So start the LiveCD, access your home folder, delete the GNOME and KDE folders (don't know the names) and proceed with the install. (Or delete all the hidden folders, except those with the settings you do want to keep.)
During installation do not format your /home partition, you only need to set it up as a mount point (screen appears after having selected the partition to install to).

Joep

ps.: There's no reason to format your swap partition. Or do you want to resize it?

---

### Post by Pobega on 2007-01-24
Yeah, I'm pretty sure the folders are located at ~/.gnome and ~/.kde, just mount your hard drive from the LiveCD and delete them. Then go on with the installation as normal.

---

### Post by ajifans on 2007-01-24
Cheers, thought so.

Last time I did it, I just deleted the ./KDE and ./Gnome folders and it seemed to work (didn't notice any ill effects).

However it's good to get a second opinion; I don't like deleting folders if I don't know exactly what they do!

Thanks

---


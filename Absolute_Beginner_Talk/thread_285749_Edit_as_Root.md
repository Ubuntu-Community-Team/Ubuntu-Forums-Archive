---
title: "Edit as Root"
date: 2006-10-27
forum: Absolute Beginner Talk
---

### Post by Phototrek1 on 2006-10-27
Hi,
 I just can't figure out how to edit a system file.  I've installed penggy and i need to edit the configuration files. I'm blocked because i don't have root access.  In kubuntu there is an option to  "edit as root". I don't see it with ubuntu.  I know almost nothing about the command line, so if you can i like to stick to the gui.

I can open the file and edit but i can't rewright the file with the updated verson.  ](*,)  

Thanks,
phototrek

---

### Post by timetunnel on 2006-10-27
Just open a Terminal and enter
```
sudo gedit <filename>
```
for example
```
sudo gedit /etc/apt/source.list
```
It will ask you for the root password and that's it. "Sudo" will execute "gedit" as root and pass the filename to gedit. That means: gedit is started as root.

---

### Post by diepruis on 2006-10-27
You could add an entry to the menu that runs the command "gksu gedit" and label it "Edit as root". This will launch gedit as the root user, allowing you to edit files.

---

### Post by 5-HT on 2006-10-27
A few more alternatives:

Option 1. Recommended

Press Alt+F2 to bring up the 'Run Application dialogue' and enter:
```
gksudo gedit /absolute/path/to/file
```e.g., to edit /etc/apt/sources.list using gedit:
```
gksudo gedit /etc/apt/sources.list
```You can also replace gedit with whichever GUI text-editor you prefer.

Option 2. Not recommended*

Run Nautilus with root privileges, and proceed as you normally would.
```
 gksudo nautilus 
```*Running Nautilus with root privileges is not a very safe thing to do for obvious reasons.

Also, please refer to  [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) for information on Ubuntu's use of sudo and what it means.

---

### Post by TheWizzard on 2006-10-27
please teach yourself to use the safe option! 

it is also a good idea to get used to a cli editor like nano. that saves your day when your x-server crashes.

```
sudo nano /path/to/file
```

i know the commandline loos scary, but if you want to learn linux the cli is the most efficient.

---

### Post by Phototrek1 on 2006-10-27
Thanks for the help,  I'm now able to edit the files.  I'm glad that it was just a simple command.  Usually when i ask a question i get alot of complex commands that i'm not familar with and i end up fustrated and deleting the distro and try another.


Thanks
phototrek1:-D

---

### Post by diepruis on 2006-10-28
> **Phototrek1 said:**
> Thanks for the help,  I'm now able to edit the files.  I'm glad that it was just a simple command.  Usually when i ask a question i get alot of complex commands that i'm not familar with and i end up fustrated and deleting the distro and try another.


Thanks
phototrek1:-D

I almost did this with Ubuntu within the first week. Lucikly I had b0rked my Windows installation and I was forced to stick with it!

---

### Post by Phototrek1 on 2006-10-29
How did you break windows?

---

### Post by diepruis on 2006-10-30
QTParted did *something* to the NTFS partition (I was resizing it).

---

### Post by janmartin on 2006-10-30
Or get Automatix2:

[http://getautomatix.com/wiki/index.php?title=Software_and_Tweaks](http://getautomatix.com/wiki/index.php?title=Software_and_Tweaks)

...Nautilus Scripts (Open Nautilus, and any file with gedit with a right click, as root (GNOME ONLY)...

---

### Post by Phototrek1 on 2006-10-30
Kind of a bummer for your windows loss.  Don't do it with vista you might be sorry and end up paying another $400 dollars.  I stick with XP for my mush have apps like itunes, Adobe PhotoShop CS and DVD playback everything esle i use Linux. 



Plus I'll try the Automatrix.  I like Gnome it not fragmented like KDE.  Though Kubuntu seem's to have a refined KDE. :D

---


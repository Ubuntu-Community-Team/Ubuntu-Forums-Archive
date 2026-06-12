---
title: "Change &quot;Removable Drives and Media&quot; default camera command  in 7.04"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by CamanoAlan on 2007-05-20
The default command for importing camera files into 7.04 is gnome-volume-manager-gthumb %h. This opens the gThumb image viewer. How does one determine the command to enter if one wants to default to the F-Spot Photo Manager instead? 

More broadly, how does one determine what the default command is for any of the devices listed in System -> Preferences -> Removable Drives and Media Preferences?

TIA

Alan

---

### Post by Pragmatist on 2007-05-21
just replace "gnome-volume-manager-gthumb"  with "f-spot-import" 

Here are two ways to find the commands:

"man -k" searches the man pages and their descriptions for the keyword you include.  I'm using the keyword "f-spot"
```
man -k f-spot
```

Even better is to use the "locate" command.  First you have to update its database so it knows what files are on your computer.  You need to do this every time you install/remove files.  The first time you run the updatedb it may take a few minutes, so be patient:
```
sudo updatedb
```

Now you can use locate:
```
locate f-spot
```

The executables are usually in some directory called "bin", so this will narrow the search:
```
locate f-spot | grep bin
```

---

### Post by crazybilly on 2008-02-08
what about the strings? like %d and %m?

what do they mean? and how do you use them?

Thanks!

---


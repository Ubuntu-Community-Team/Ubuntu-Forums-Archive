---
title: "can't access osx backup"
date: 2008-09-04
forum: Apple Hardware Users
---

### Post by smitrog on 2008-09-04
i used gparted live cd to copy my osx HD to my usb HD which i thought had worked since i booted into ubuntu and i could see the osx file structure ok but had the problem of not being able to access the files i want due to the permissions but i thought once i had re-installed osx on my imac i could copy the files no problem but osx doesn't even recognize that there is a file system on the usb HD at all it just give's me the option to format it or ignore it, so what now? the files must be there so there has to be way to get them off.

Basically i have a backup of my old imac HD on a usb HD and want to retrieve some files from it but can't due not having the right permissions so is there a way i can change the permissions of the usb HD in ubuntu? or can Gparted change the permissions?

thanks

edit is my question isn't clear please ask and i'll try to explain it better.

---

### Post by cyberdork33 on 2008-09-04
what filesystem did you use on your external hard drive? Unfortunately it is not as simple as copying the files from your hard drive, reinstalling, then copying them back. Are you just talking about files like music and pictures that were in your home folder?

---

### Post by smitrog on 2008-09-04
the filesystem is HFS+ and the files that i want to recover are my itunes library and emails etc.

---

### Post by cyberdork33 on 2008-09-04
> **smitrog said:**
> the filesystem is HFS+ and the files that i want to recover are my itunes library and emails etc.
probably the easiest thing to do is to open a terminal and do something like ```
sudo chown -R yourusername /Volumes/external_hard_drive
```

---


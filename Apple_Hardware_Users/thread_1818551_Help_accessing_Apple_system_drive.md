---
title: "Help accessing Apple system drive?"
date: 2011-08-04
forum: Apple Hardware Users
---

### Post by Donny Bahama on 2011-08-04
I'm trying to help a friend (who dropped his MacBook Pro) recover his data files. (The drive will no longer boot OS X.) I got the MacBook opened up and pulled out the drive. I have it connected via USB to a Linux box as an [[COLOR=blue][COLOR=blue ! important][FONT=verdana][COLOR=blue ! important][FONT=verdana]external [/FONT][/COLOR][COLOR=blue ! important][FONT=verdana]drive[/FONT][/COLOR][/FONT][/COLOR][/COLOR]]("http://www.mac-forums.com/forums/#"). Ubuntu sees the drive and I can go into Users/Joe but all the subdirectories have an "X" over the folder icon and when I try to open any of them, I get "Failed to open Documents. Permission denied."

'sudo chmod' returns "Read-only file system" but when I run 'mount', it says: /dev/sdb2 on /media/Macintosh HD type hfsplus (rw,nosuid,nodev,uhelper=hal)

I'm a little out of my element, here, and not sure what else to try. Any help would be greatly appreciated.

---

### Post by Basher101 on 2011-08-04
to get the permissions open your filebrowser in the terminal using
sudo nautilus (for gnome) or sudo dolphin (for KDE)

note: you must first mount the drive or you wont see it in the file browser you opened in the terminal
note2: this will open your filebrowser with admin permissions. Make sure not to delete your systemfiles by accident

---

### Post by alokbiyani on 2011-08-06
Hey, 
you can definately shot a mail to APPLE regarding this problem or
can post this prob on to their forums..
This is d way My MacBook Pro Problem had resolved when it showed system failure..

Regards,
Alok Biyani Kolkata

---


---
title: "Ubuntu on the desktop"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by badbob100 on 2007-05-31
I've just installed Ubuntu 7.04 Feisty i386 on my A64 X2. Managed to install onto the HD, but having a couple of problems. I selected VGA mode 1024x768 before the boot.

DVI out not working. Used VGA instead. In the desktop I cannot change resolution to 1680x1050. ATI X1900XT and Philips 20" 16:10
No sound, Creative Labs X-Fi Extreme Music, analogue ouput.
also I have MS Explorer mouse, forward and back buttons aren't working (work fine in XP/Opera)
Trying to add my photos to wallpaper, they're on a NAS.  I can find it, and have created a "shortcut" to below disk explorer thing, but can't use the path in wallpaper..I've tried to add
smb://dns-323/Volume_1/photos
in wallpaper path but it doesn't want to accept it

aha, I installed ATI drivers in "Restricted Drivers Manager" I can now change resolution, 1680x1050 works, and so does DVI!

---

### Post by dave-5B on 2007-05-31
if you go to places > connect to server

you will then be able to mount the samba share of your NAS as a folder somewhere (nautilus can see stuff like smb://... but other programs cant)

to mount it at boot you would have to put an entry in /etc/fstab dont know exactly what it would be though

---

### Post by badbob100 on 2007-06-01
Which options do I select, and what do I type in?

---

### Post by dave-5B on 2007-06-01
Sorry a better idea is to look in Places > Network

just right click on teh shared folder and "connect to this server"

if you dont see anything then I'm an idiot because samba (windows sharing) is not installed by default
to install it:

sudo aptitude install samba smbfs

---


---
title: "Desktop icons double"
date: 2007-09-16
forum: Absolute Beginner Talk
---

### Post by freshspinach on 2007-09-16
My desktop icons signifying places on my computer have duplicated themselves. Anybody know why?

---

### Post by zero-9376 on 2007-09-16
just the ones that represent drives or any icons for folders etc. also is it the same when you use icon view when browsing your nomal directories?

if so you may have changed (or someone/thing else) the default zoom level for nautilus

open a nautilus window (just open a folder) and go to edit->preferences, check the default zoom level for icon view and change if necessary.

---

### Post by freshspinach on 2007-09-16
The icons appear fine in Nautilus, without duplicates. It's just on my desktop that my drives have duplicated themselves. One is my USB external drive and the other is an internal DVD drive. My 'sda1' and my two drive partition icons shown on my desktop don't duplicate.

---

### Post by zero-9376 on 2007-09-16
hmm sorry i misread your original post i thought the icons had doubled in size :P

there is a bug report which may be related to your problem but there doesnt appear to be any solution there, there are also other bug reports but again the ones i saw didnt provide solutions
[https://bugs.launchpad.net/ubuntu/+source/gnome-volume-manager/+bug/70380](https://bugs.launchpad.net/ubuntu/+source/gnome-volume-manager/+bug/70380)

are all the volumes shown? if these volumes are using ntfs-3g or something it may be realtated to that, or beryl/comiz - this is all from bugreports

you can probably try searching these forums based on your situation, or post back with more details like what /etc/fstab and /etc/mtab say, in the meantime though you can disable the drives showing on the desktop at all using gconf-editor

alt-f2 to bring up run dialog > gconf-editor > browse to /apps/nautilus/desktop/volumes_visible and untick it

if your lucky it may remove one set drives (although i highly doubt it) but at least you wont have them clutering your desktop and you can still access them through places, or while your in the desktop section of gconf you can tick computer icon visible to have more windows like access to drives.

is your problem persistent through logins and reboots?

---

### Post by freshspinach on 2007-09-16
That bug report seems like the same problem I'm experiencing. My external drive is using ntfs-3g, which could be a factor, but my dvd drive is also showing duplicate icons.

I've noticed that this problem comes and goes across multiple reboots and logins. I experienced this issue right after installing feisty but then it went away. The icons started duplicated themselves again last night, though i can't remember reconfiguring or installing anything. 

Rebooting doesn't make it go away. 'Ejecting' the drives by right clicking removes one icon and disables access to the other one.

I can still access my drives just fine, so it's really just a visual issue more than anything. I'll try disabling the drives as you suggest.

---

### Post by makmiler on 2008-01-21
This is my workaround to this problem. It refreshes the volume icons on the desktop every time you log in.

create a file somewhere in your home directory, and put this inside:

gconftool --type bool -s /apps/nautilus/desktop/volumes_visible false
gconftool --type bool -s /apps/nautilus/desktop/volumes_visible true

Save it, and make it executable

Open System > Preferences > Sessions

Under Startup Programs, add the script you just created.


Until official patch is made, this is a workaround.

R.M

---

### Post by freshspinach on 2008-01-22
Thanks! The workaround works!

---


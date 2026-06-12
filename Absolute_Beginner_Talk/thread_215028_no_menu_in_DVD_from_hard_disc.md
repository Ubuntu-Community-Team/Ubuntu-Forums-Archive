---
title: "no menu in DVD from hard disc"
date: 2006-07-13
forum: Absolute Beginner Talk
---

### Post by wolfmaniac on 2006-07-13
what i did is that i copy the whole video_ts folder to my hard disc and tried to play it using mplayer totem and xfmedi.

but i cud not get the dvd menu.
instead individual files are played .
any suggestions on the problem

---

### Post by x64Jimbo on 2006-07-13
I don't know the equivalent Gnome app, but in KDE, there is a program called k9copy which does the same thing as DVDShrink in Windows. It rips the whole DVD to an ISO file that you can burn to a new disc. You can also mount ISO files in Linux like DaemonTools in Windows but you don't need a special tool to do it. 
sudo mkdir /mnt/iso/
sudo mount -o loop -t iso9660 mymovie.iso /mnt/iso/
It's pretty cool, actually.

---

### Post by orb9220 on 2006-07-13
Same here last night I ripped dvdshriked a movie and watched with xine.

And the menu structure doesn't work for folders.
Only iso's or actual dvd's mounted in cdrom drive.

I could be wrong but haven't seen a way yet.

---


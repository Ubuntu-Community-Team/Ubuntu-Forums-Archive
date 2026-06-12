---
title: "ext usb drive"
date: 2006-05-16
forum: Absolute Beginner Talk
---

### Post by crossface on 2006-05-16
noob here, I am experienced with ms and have been lucky with Kubuntu so far. Installed, hardware ok, upgrade/Adept ok, Firefox dl and installed.
I have experimented with all the apps and the OS itself  dapper and find it as good or better than ms. (and cheaper) 
I think I have found a keeper with Dapper. I am trying to move my files, least a gig of mp3 and some photos from my usb external drive to my desktop. Kubuntu recognizes and asks me what to do with it. I can see all my files but can't move them to the desktop. I am GUI oriented and can't figure out the rite commands. Is there a way to do it with GUI if not what command are necessary for the file transfer. Thank in advance!

---

### Post by Lord Illidan on 2006-05-16
[quote=crossface]noob here, I am experienced with ms and have been lucky with Kubuntu so far. Installed, hardware ok, upgrade/Adept ok, Firefox dl and installed.
I have experimented with all the apps and the OS itself  dapper and find it as good or better than ms. (and cheaper) 
I think I have found a keeper with Dapper. I am trying to move my files, least a gig of mp3 and some photos from my usb external drive to my desktop. Kubuntu recognizes and asks me what to do with it. I can see all my files but can't move them to the desktop. I am GUI oriented and can't figure out the rite commands. Is there a way to do it with GUI if not what command are necessary for the file transfer. Thank in advance![/quote]

From the terminal, it should be as easy as:

```
cd /media/sda1 (or wherever your usb disk is located, normally there.
cp * /home/INSERTUSERNAME/desktop/

```

From the GUI:
KDE usually puts an icon for your ext usb drive on your desktop when it appears. Navigate to it, and select the files, etc...(like Windows)

---

### Post by crossface on 2006-05-16
I have created a folder of all things "my music" for the mp3's and "my photos for the jpg's. I can navigate to it but which selection should I choose the move selection does not move anything, but seems to just change the path.  I don't want to cut and paste, seems like copy should do it but how?

---

### Post by crossface on 2006-05-16
[QUOTE=crossface]I have created a folder of all things "my music" for the mp3's and "my photos for the jpg's. I can navigate to it but which selection should I choose the move selection does not move anything, but seems to just change the path.  I don't want to cut and paste, seems like copy should do it but how?[/QUOTE]


Got it transferred. Thanks for the input. Ended up doing a drag & drop with the copy selection. 2.5 hours later my mp3s all 8.3 gig of them was  transferred to computer files. Kubunta has a lot of upsides. Have not discovered any downsides yet, think ms is in trouble.

---


---
title: "Cannot open mp3"
date: 2007-11-19
forum: Absolute Beginner Talk
---

### Post by Waldo22 on 2007-11-19
Does anyone know why I am getting this message when opening mp3 files?:

The filename "Track 01.mp3" indicates that this file is of type "mp3 document". The contents of the file indicate that the file is of type "MP3 audio". If you open this file, the file might present a security risk to your system.

Do not open the file unless you created the file yourself, or received the file from a trusted source. To open the file, rename the file to the correct extension for "MP3 audio", then open the file normally. Alternatively, use the Open With menu to choose a specific application for the file.

---

### Post by gn2 on 2007-11-19
Do you have the mp3 codecs installed?

If you haven't or don't know, copy and paste this in a terminal: 

sudo apt-get install ubuntu-restricted-extras

---

### Post by kleo skywalker on 2007-11-19
I've faced this problem with corrupted files. For example, I once inserted an old and rather scratched audio CD into the CD drive, and got the same message for most of the files. Also happens when I try to open an incomplete download when too little has been downloaded.

---

### Post by Waldo22 on 2007-11-19
> **gn2 said:**
> Do you have the mp3 codecs installed?

If you haven't or don't know, copy and paste this in a terminal: 

sudo apt-get install ubuntu-restricted-extras

Yikes! I attempted to install restricted packages, but now I get a message:

E:dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

Terminal says, "requested operation requires superuser privilege"

Looks like I'm in over my head here.

---

### Post by fenian on 2007-11-19
Open a terminal and enter...
> sudo dpkg --configure -a

then go to add/remove programs in the applications menu.Search for gstreamer and choose to install the following Ubuntu restricted exras,Gstreamer extra codecs,Gstreamer ffmpeg video plugin, GStreamer plugins for aac, xvid, mpeg2, faad,and GStreamer plugins for mms, wavpack, quicktime, musepack.This will give you the packages to play a wide variety of media files.

---

### Post by Waldo22 on 2007-11-19
Many thanks!  Back to normal, at least.  Great to have help in time of need!:)

---


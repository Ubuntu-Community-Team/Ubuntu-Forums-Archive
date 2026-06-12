---
title: "Music player problems"
date: 2006-02-07
forum: Absolute Beginner Talk
---

### Post by CujoQuarrel on 2006-02-07
Trying to get a music player to work. 

What I have is an external USB NTFS HD that contains my music files. I'd like to use my new Kumbutu box here as a player but I'm not having a lot of luck.

The system recognizes the HD and the files are accessable. I think I've gotten the permissions correct with world haveing rx priv.

So far I can't get XMMS, amarok etc to play a file from the external. They don't give me any errors they just sit there. If I copy a file from the external to the local HD I can play them fine with XMMS but not with Amarok. 

VLC will play the files from the external.

Any suggestions?

---

### Post by JShadow on 2006-02-07
What format are the music files and what engine are you using in amarok? 

You might be having a GStreamer problem. I find the Xine engine is easier to get going. Search for amarok-xine in Adept.

---

### Post by CujoQuarrel on 2006-02-07
The files are in MP3 format

---

### Post by JShadow on 2006-02-07
Yeah, and you're probably using GStreamer. You can either try installing gstreamer0.8-mad or else amarok-xine via Adept. 

If you use amarok-xine, in amarok go to the settings menu, configure amarok, then engine. Select Xine there and you should be good to go

---

### Post by CujoQuarrel on 2006-02-08
Bingo!!!

We have achieved musica.

Thanks bunches

---


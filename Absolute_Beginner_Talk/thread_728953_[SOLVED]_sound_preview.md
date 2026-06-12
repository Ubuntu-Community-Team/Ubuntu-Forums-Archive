---
title: "[SOLVED] sound preview"
date: 2008-03-19
forum: Absolute Beginner Talk
---

### Post by celticbhoy on 2008-03-19
I have just noticed that when I hover the mouse over a sound file in nuatilus that it no longer previews the file, I dont know how long this has been like this as my sound is turned down most of the time. Is this a feature that I can just turn back on, or is there a bigger problem. The sound works fine during playback from apps ok.

---

### Post by superprash2003 on 2008-03-19
the sound preview option can be set here.. go to places->computer .. then click on edit->Preferences .. then go to the preview tab .. and you will find an option for Sound files

---

### Post by Jareth on 2008-03-19
I had the same problem and someone told me what to do, I can't find the post now though.

This one suggests leaving it off because it crashes nautilus.
[http://ubuntuforums.org/showthread.php?t=698328&highlight=sound+preview](http://ubuntuforums.org/showthread.php?t=698328&highlight=sound+preview)

I have had that happen to me, the music file doesn't stop playing, very annoying!

---

### Post by celticbhoy on 2008-03-19
I have already tried that - it is set to always.

How do you find what app is set to play the previews - might have to do with that ??

---

### Post by Jareth on 2008-03-19
I just read something which reminded me what it was,
"Audio Previewing (This applies to all Ubuntu releases.): The Ubuntu File Manager Nautilus can preview music files if you hover your mouse pointer over the file. If you would like to add this functionality to your desktop, install the mpg321 and vorbis-tools."

I remember installing the mpg321 in synaptic and I think that was all I did, but maybe you need to check the vorbis-tools is installed too.

Actually I just realized while writing this that I haven't enabled it since installing ubuntu, doh!

I'll try it and get back to you.

---

### Post by glennric on 2008-03-19
> **Jareth said:**
> 
I remember installing the mpg321 in synaptic and I think that was all I did, but maybe you need to check the vorbis-tools is installed too.


You need mpg321 for wav and mp3 files, vorbis-tools is for ogg files.

---

### Post by Jareth on 2008-03-19
I think this thread has it worked out. Mine finally works after installing the esound package and rebooting. You do need to reboot so don't forget.

[http://ubuntuforums.org/showthread.php?t=576995&highlight=sound+preview+icon]("http://ubuntuforums.org/showthread.php?t=576995&highlight=sound+preview+icon")

read it all first to make sure you don't miss nothin.

Good luck!

---

### Post by celticbhoy on 2008-03-19
Needed the esound package and the mpg321 package thanx guys

---

### Post by Jareth on 2008-03-20
Hi, hope its all working now for you.
I just found this as well which may be good for someone else or the future
[http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_to_get_Mouse_over_preview_of_MP3_files_working]("http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_to_get_Mouse_over_preview_of_MP3_files_working")

---


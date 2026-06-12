---
title: "Rhythmbox doesn't play mp3 file when you double click on it. Is this normal?"
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by lebe0024 on 2007-05-11
If I change my default mp3 program from totem to rhythmbox, and I then double click on a mp3 file, rhythm box opens up but it doens't play the file. However, I can play my library mp3's just fine from rhythmbox. Is this normal?

---

### Post by Fylk on 2007-05-11
Are the new MP3s added to your library?

---

### Post by lebe0024 on 2007-05-11
No. I don't think so.  My library was empty before and after I double clicked on the file.

---

### Post by Zunino on 2007-05-13
> **lebe0024 said:**
> If I change my default mp3 program from totem to rhythmbox, and I then double click on a mp3 file, rhythm box opens up but it doens't play the file. However, I can play my library mp3's just fine from rhythmbox. Is this normal?
I have got the same behavior with Rhythmbox 0.10 on my newly installed Feisty Fawn. Usually, when a music file is double-clicked, the expected behavior is for the assigned default application to be launched (if not already open) and start playing back that file. As of now, double-clicking on a music file will cause Rhythmbox to be launched but neither will it play the file nor will it add the file to the playlist.

I have observed that, once Rhythmbox has been open, double-clicking on a music file produces the expected behavior. Does anybody know of a way to fix this situation?

Thank you,

-- 
Ney André de Mello Zunino

---

### Post by lebe0024 on 2007-05-14
Well, the work around for me right now is to assign totem as the default player.  That way, when you click on a file, at least it get played.  But I still use rythmbox to browse/play my library.

---

### Post by slackmaster on 2007-06-06
Hello,

OK MP3s don't work.  I found a forum with this command:  sudo apt-get install gstreamer0.8-plugins.  Its supposed to allow MP3s to run.  I try to reimport my music folder from an external drive.  Ryhythmbox doesn't add anything.

Any ideas?  Thanks.

---

### Post by strabes on 2007-06-06
If you're using feisty, run ```
sudo aptitude install ubuntu-restricted-extras
```

Also check this page: [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by slackmaster on 2007-06-06
Hi,

Thats was fast!  I posted ten minutes ago!  Yes I am using feisty.  I already entered the other code you listed.
.  What can I do to undo the my last action?  Do I need to?  Does Linux have an equivelancy to system restore? 
 Anyway let me try your suggestion.

Well the sun java agreement appears with an <ok> at the bottom that doesn't respond to <enter>.  I guess I just close the terminal and that counts as an <ok>.  

One other question, with windows, you usually are prompter to restart the computer after installing applications.  Also you sometimes are instructed to close all apps during install.  Do you recommend by default closing all apps and rebooting after each install?  Or can you run apps, install packages, and skip rebooting generally if there isn't a prompt?

---

### Post by slackmaster on 2007-06-06
Hello again,

By the way, I'm really appreciative of you all answering questions in this forum..  
Back to rhythmbox...so I restarted everything and reimported my files.  As usual, the gstreamer plugins to decode mp3 files cannot be found.  Was the command you gave me supposed to fix this issue or is it something entirely different?

S.:-k

---

### Post by slackmaster on 2007-06-07
> **Zunino said:**
> I have got the same behavior with Rhythmbox 0.10 on my newly installed Feisty Fawn. Usually, when a music file is double-clicked, the expected behavior is for the assigned default application to be launched (if not already open) and start playing back that file. As of now, double-clicking on a music file will cause Rhythmbox to be launched but neither will it play the file nor will it add the file to the playlist.

I have observed that, once Rhythmbox has been open, double-clicking on a music file produces the expected behavior. Does anybody know of a way to fix this situation?

Thank you,

-- 
Ney André de Mello Zunino

Hello,

I was having a problem playing MP3s as well.  I tried following a number of tips but they didn't work.  I found a simple solution though.  In fact this solution makes setting up many different popular debian apps an easy task 
 Just install Automatix.  This programs has a list of many applications including a number of media players that can handle MP3s.  I installed Listen Music Player o.5.  It will import your library from an external HD, shuffle the songs, provide links to lyrics, wikipedia, and even LastFM.  Good luck.

S.

---

### Post by downhillgames on 2007-06-14
```
sudo apt-get install gstreamer-0.10-plugins-ugly
```
will make mp3s work. might also need the package `lame'

---


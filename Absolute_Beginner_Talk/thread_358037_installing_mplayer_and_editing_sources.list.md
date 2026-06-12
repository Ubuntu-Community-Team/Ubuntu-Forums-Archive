---
title: "installing mplayer and editing sources.list"
date: 2007-02-10
forum: Absolute Beginner Talk
---

### Post by Ceta on 2007-02-10
I installed mplayer from the package manager but I get this error when trying to play a file: error opening/initializing the selected video_out(-vo) device.  Is it because mplayer isnt installed properly or because I dont have the right codecs installed?  How do I install codecs?  Is there anything else I have to do after installing mplayer from the package manager? It gives the same error when trying to play dvds too.

I read a guide saying i have to alter and save sources.list.  It wont let me save the file after I edit it though because i dont have the proper permission.  So I tried a different suggestion saying I edit in sudo gedit but then I cant figure out how to save the file to "apt".

---

### Post by taurus on 2007-02-10
From a terminal, type **gmplayer** and right click.  Go into Preferences and change the video to something else like x11.  Shut it down and now see if you can play a video file.

And if you want codecs, check out this guide.

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---


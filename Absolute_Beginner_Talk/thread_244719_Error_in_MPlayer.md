---
title: "Error in MPlayer"
date: 2006-08-26
forum: Absolute Beginner Talk
---

### Post by U5tabil on 2006-08-26
when i now try to play a movie/clip i get this error error 

opening/initializing the selected video_out (-vo) device.

Anyone know what that means? and what to do with it?

---

### Post by kencoe on 2006-08-27
don't know if it will help, but I found this in google...

[http://www.linuxquestions.org/questions/showthread.php?t=458293](http://www.linuxquestions.org/questions/showthread.php?t=458293)

---

### Post by Bachstelze on 2006-08-27
Try using the X11 output module in Preferences > Video.

---

### Post by jISh on 2006-08-27
What kind of video are you trying to play? This is a common error if Mplayer doesn't support the filetype (although the program has a broad range of supported codecs).

---

### Post by tkrisz on 2006-08-28
I have the following errors playing mplayer and mplayer-plugin (amd64 with 64 bit Dapper):

.wmv (8): 
it works on 70% of the video well, but simetimes go mad (see attachment, 1st: OK). It is the same in every video player: xine, totem, mediaplayer...

.ram
I tried to listen to some online radio in my browser, but it does not work at all. It writes:
Getting playlist...
Then: Playing [http://123.45.67.89](http://123.45.67.89) (for 1/2 sec.)
Then: Stopped.
No sound output. Just a grey screen with the mplayer logo.

Quick Time 7:
1 file has freezed my Firefox, otherwise it seems like working, except for 1 thing: It buffers only 99%, then i have to rightclick on Play 2-3 times to start.

I have no control buttons for the plugins. Should i have?

---

### Post by Bachstelze on 2006-08-28
Those three formats are proprietary, so codecs for them might be a bit buggy. Did you install w32codecs ?

---

### Post by tkrisz on 2006-08-29
No, but i have a lot of codecs installed.
Should i do it even if i'm an amd64 user?

---


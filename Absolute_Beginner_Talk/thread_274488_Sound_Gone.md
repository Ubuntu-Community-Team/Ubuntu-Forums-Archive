---
title: "Sound Gone"
date: 2006-10-09
forum: Absolute Beginner Talk
---

### Post by clarkhuke on 2006-10-09
I am running the most recent (and by that I mean I just installed the most recent updates 15 minutes ago and restarted the computer) version of Dapper Drake. Out of no-where last week my sound died.
By that I mean it is totally dead. 
It is stuck on mute and I cannot do anything to raise the volume. Also, when attempting to play sound in various programs they tell me I am missing GStreamer or my sound card isn't properly configured.
The strange thing is, is that I it worked perfectly fine before that time. 

I don't know if it has anything to do with it, but about the same time I forgot my password and had to go in 'recovery mode' and changed it that way. I doubt it has anything to do with it though.

-Clark :confused:

---

### Post by Mr Frosti on 2006-10-09
Changing your password should not affect your sound. Your sound card icon being "muted" is a representation that packages are missing and you cannot use sound right now.

To correct this issue, try reinstalling the "gstreamer" packages by running the following command in a terminal:

```
sudo apt-get install gstreamer0.10* --reinstall
```

This should reinstall the mixer applications, as well as the numerous gstreamer packages. Once this is done, restart your machine and see if the sound issue is resolved.

---


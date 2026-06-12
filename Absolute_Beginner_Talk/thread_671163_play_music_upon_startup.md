---
title: "play music upon startup"
date: 2008-01-18
forum: Absolute Beginner Talk
---

### Post by Zippo Master on 2008-01-18
This probably requires more technical linux know-how than I have.  I am looking for a way to  have my music start playing when I boot up.  Any ideas?

---

### Post by Cypher on 2008-01-18
If you mean your MP3 music beyond just the startup sound, then suppose you XMMS as your player. Just load it up, set it to auto-play when it starts up (assuming the playlist has been set up) and then go to Systems->Preferences->Sessions and you will see XMMS listed there, click on it and have it load up every time you login.

This way the next time you login, XMMS will be automatically launched and will being playing music..

No technical linux know-how needed..:)

FYI, I'm guessing a little on the Session manager as I don't have access to my Ubuntu machine right now, but play around in there to get this to work..

---

### Post by forestpixie on 2008-01-18
if it's not listed add it to the list - other than that can't think of anything 

need to navigate to the correct file - probably /usr/bin

but if you can't find what your looking for, in a terminal do whereis

```
whereis xmms
```

for instance, replace xmms as you wish

---

### Post by Zippo Master on 2008-01-18
Thanks for the quick replys.  So I've downloaded xmms, set a playlist, configured it to load when I boot but how do I make xmms auto play when it starts?  Thanks again.

---

### Post by tgalati4 on 2008-01-18
On the XMMS window, right-click Options-->Preferences.  Look around.

---

### Post by mcduck on 2008-01-18
The coolest way to get this would be using MPD. As it runs as it's own user, the music will start playing even before you get a chance to log in to your desktop..

All you need to do is leave MPD playing when you shut down the computer, and it will continue playing when you start the machine again.

---

### Post by Mujaheiden on 2008-03-02
To have xmms play the playlist upon startup, add the** -p** flag in the launcher. See** [man xmms]("http://linux.die.net/man/1/xmms")** for more options. Its not in the preferences.

On KMD, I want to use my computer as an alarm clock, connecting to  webradio. I don't believe MPD plays proprietary streams?

---

### Post by MONODA on 2008-03-02
no dont do it that way. go system->admin->login window click on the accessability tab and from there you can choose to play a song at login

---

### Post by Mujaheiden on 2008-03-02
which is wholly different then a stream, but thanks a bunch.

---


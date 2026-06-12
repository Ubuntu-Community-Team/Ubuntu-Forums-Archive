---
title: "Changing Video Settings back..."
date: 2007-09-11
forum: Absolute Beginner Talk
---

### Post by PropheticAngel on 2007-09-11
I had my video working completely fine for the last month, but today I needed to use a projector, so I messed stuff up trying to get it to work.

Every time I try to play a video in totem I get the error that the video output is in use by another application.  

I think it has something to do with:
```
 sudo dpkg-reconfigure -phigh xserver-xorg
```

or something with xrandr, but I don't think I did anything with that.

Is there any way I can just reset everything back to normal?  I restored to the back-up xorg.conf that command gave me, but it didn't fix anything.

---

### Post by bsharp on 2007-09-12
Sorry about taking so long to respond, open up a terminal and type:

```
sudo dpkg-reconfigure x11-common
```

and answer the questions as closely as possible. That will reconfigure your X-server and should get everything back to normal.  As for the code you posted above, I don't know what that means.  I'm just giving you what has worked for me in the past.

---

### Post by PropheticAngel on 2007-09-13
I tried it, but I still get errors when opening videos.

Totem gives me: The video output is in use by another application.  Please close other video applications, or select another video output in the Multimedia Systems Selector.

But after that error, the video seems to work fine...

---


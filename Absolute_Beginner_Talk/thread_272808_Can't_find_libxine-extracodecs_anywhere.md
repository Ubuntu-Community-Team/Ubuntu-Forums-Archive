---
title: "Can't find libxine-extracodecs anywhere"
date: 2006-10-07
forum: Absolute Beginner Talk
---

### Post by teiresias on 2006-10-07
I've installed amarok fine, but can't play anything from my imported old iTunes collection (it's all drm-free mp3s and aac-encoded files).  Amarok is using the xine engine, so I'm pretty sure I need the libxine-extracodecs package, but I can't seem to find it.

I have every repository turned on (everything is checked) and I still can't find it, and putting "sudo apt-get libxine-extracodecs install" into a terminal doesn't work either.

Can anyone tell me what I'm doing wrong?  Where the heck is this thing?

---

### Post by WalmartSniperLX on 2006-10-07
did you try ```
 sudo apt-get update 
``` first?

(not sure if that will do the trick but its worth a try)

btw its 

```
 apt-get install 
```

---

### Post by teiresias on 2006-10-07
I'll try that.  I noticed that when I "Reload" under synaptic that it hangs at 9 out of 11 packages of some kind and I end up having to cancel out of it.  Maybe it's in one of those that it doesn't seem able to pull down at the moment.  Not sure though.

---

### Post by aysiu on 2006-10-07
What do you mean by "everything checked"?

Get a fresh list:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

Then try again: ```
sudo aptitude update
sudo aptitude install libxine-extracodecs
``` If that doesn't work, post here the output of those two commands.

---

### Post by teiresias on 2006-10-07
I mean when I go to the listing of repositories in Syanptic I have all of them checked and then press "Reload."  I'll try your suggestion when I get home tonight.

Actually, I'm having a more Amarok-specific issue now, it got updated to a new version and now it freezes whenever it tries its initial parsing of my music library.  Oh well, that's neither here nor there concnerning my inability to find the libxine-extracodecs package.

---


---
title: "uninstalling realplayer 10"
date: 2007-02-16
forum: Absolute Beginner Talk
---

### Post by aijazbaig1 on 2007-02-16
Hello.
I managed to install realplayer by following the instructions on the real player web site and i even got the FF plugin working..
However for some bizarre reason, the clips that are being displayed on websites only display the vide but do not play back the sound stream.
On checking the plugins folder in the firefox plugins directory (i installed the latest version 2 manually in the 'opt'  directory and hence the path to the plugins is opt/firefox/plugins and it lists the following plugins which I think are related to realplayer:

nphelix.xpt
nphelix.so

Is there something wrong there.
And is there a way in which I could go about an uninstall followed by the fresh install of realplayer followed by the plug ins..
And how does one go about uninstalling a manually installed application program in linux especially ubuntu dapper drake...:confused: 

Hope to hear from you guys soon,

Aijaz.

---

### Post by SuperKillar on 2007-02-16
Hi aijazbaig1,

**Well I think this is how you could go about removing it:**

```
sudo apt-get remove realplay
```
This should uninstall the plugins too.


**And to install it again you do:**

```
sudo apt-get install realplay
```

This should do the trick, If this doesnt help I don't know :)

-SuperKillar

---


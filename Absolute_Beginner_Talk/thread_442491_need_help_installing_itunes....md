---
title: "need help installing itunes..."
date: 2007-05-13
forum: Absolute Beginner Talk
---

### Post by indrion on 2007-05-13
yeah i'm trying to get itunes on my computer, do i just download it from the mac site and use wine to open it?

---

### Post by Pobega on 2007-05-13
iTunes doesn't work under any GNU/Linux distribution, if you need iTunes I advise you to dual boot between Mac or Windows.

---

### Post by l951b951 on 2007-05-13
Using the forum search feature for "itunes" came up with this previous post.


[http://ubuntuforums.org/showthread.php?t=434950](http://ubuntuforums.org/showthread.php?t=434950)

---

### Post by starcraft.man on 2007-05-13
Just in case, you can see the version/entries [here.]("http://appdb.winehq.org/appview.php?iAppId=1347")

Best advice is to dual boot itunes into mac/windows (and even running itunes in windows can cause serious issues from some of my friends experiences). Honestly, just burn your songs to CDs (a rewritable would be good) and the rip em back off, then you can have em un DRM. Or, try Jhymn (i dunno if its currently working or not >.>)... I just don't think itunes has a place on Ubuntu, it certainly doesn't try to be open or friendly...

---

### Post by cam2009 on 2007-05-14
Use Amarok. I used iTunes for years, and nothing on Windows I found compared to it, but Amarok beats it just about everywhere. Getting your iPod to work might take some simple tinkering, but it's the best music player I've ever used.

---

### Post by starcraft.man on 2007-05-14
Gamefreak, we don't need your cursing on these forums. This is the second time I've seen you curse in two posts that i've seen you make (I just checked your posts and you seem to like cursing in all your posts) not to mention you keep saying how horrible Ubuntu is in your posts too. There is a really simple solution to this, don't use Ubuntu. Go back to windows/mac whatever you were using before, and then all your things will work. Please stop stop venting on our forums with foul language, these are children and people who could get offended about. Not to mention rampant cursing by people usually is simply a disguise for someone with a lacklustre vocabulary.

---

### Post by gamefreak90 on 2007-05-14
sorry, but I need help, im not used to ubuntu, my ipod wont connect to amarok, and i have been tinkering w/ this all night, just gettin tired i guess, sorry for the cursing...can someone help me out?

---

### Post by starcraft.man on 2007-05-14
> **gamefreak90 said:**
> sorry, but I need help, im not used to ubuntu, my ipod wont connect to amarok, and i have been tinkering w/ this all night, just gettin tired i guess, sorry for the cursing...can someone help me out?

Well, ok, that is better... no cursing makes me happy and I will help. It should automount as a drive I think. When you plug it in via USB, wait 20 seconds and then if it doesn't pop up on the desktop, run this in terminal (Applications > Accessories > Terminal):

```
sudo fdisk -ls
```

then copy and paste the output here.

---


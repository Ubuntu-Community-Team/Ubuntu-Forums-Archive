---
title: "New flash install -how? [Resolved]"
date: 2006-12-10
forum: Absolute Beginner Talk
---

### Post by onemind on 2006-12-10
Hi,

I have been having problems with flash like no sound and sound being out of sync with video and some have suggested installing the latest beta version of flash player. Being a total noob, i dont know how to do that :)

Any help would be great.

Thanks

---

### Post by joplass on 2006-12-10
try this:
[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)

---

### Post by ThrobbingBrain66 on 2006-12-10
Make sure you remove the old version of flash first.  Many people have encountered issues without doing this.

```
sudo apt-get remove flashplugin-nonfree
```

---

### Post by igknighted on 2006-12-10
go to labs.adobe.com and find the flashplayer 9 update beta.  Then download the archive and extract it.  There is a readme and another file (flashplaer.so i think).  Read the readme, it will tell you where to put flashplayer.so.  Once you put it in the directory the readme says, your flashplayer will work.  Two things, first you will need sudo to do this.  Second, go ahead and overwrite any old file that is in there.

---

### Post by aysiu on 2006-12-10
This tutorial will help you out:
[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

---

### Post by onemind on 2006-12-10
Thanks all, youtube is finally woking well :)

---

### Post by ktraglin on 2007-03-10
onemind:  Which solution worked for you?

---


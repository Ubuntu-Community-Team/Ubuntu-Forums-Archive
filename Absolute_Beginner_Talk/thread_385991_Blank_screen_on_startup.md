---
title: "Blank screen on startup"
date: 2007-03-16
forum: Absolute Beginner Talk
---

### Post by maccawolf on 2007-03-16
Ubuntu 7.10.

Was working fine two days ago (cept a HAL error which I haven't had time to correct.)

Now, when I boot up, I just get a blank desktop.
 Upper and lower bars are there, but there are no icons or anything there.
 I had also changed the background, and that has defaulted back to the orangy brown default screen.

---

### Post by taurus on 2007-03-16
> **maccawolf said:**
> **Ubuntu 7.10**.


Feisty Fawn is not even out yet and you're already on the next release!

---

### Post by dannyboy79 on 2007-03-16
the hal error is your problem. Plus, Taurus is saying if you're new to linux than you shouldn't be trying Fiesty, go with Dapper or Edgy. Fiesty is still in development and you won't get people helping you because it's not released yet.

---

### Post by maccawolf on 2007-03-16
whatever the version that is next to the newest. (not the one that was released in Alpha a couple of days ago. the one before that.)

---

### Post by dannyboy79 on 2007-03-16
oh, are you saying that you're running **6**.10? if so, than we can maybe help. You'll want to resolve the hal error, hal is a major part of the internal workings I beleive.

does this help?
I've had some success editing /etc/usplash.conf. I changed it from 1280x1024 (my standard display resolution) to 800x600 and now usplash works. 

OR

[http://www.ubuntuforums.org/showthread.php?t=290655&highlight=bootup+blank+screen](http://www.ubuntuforums.org/showthread.php?t=290655&highlight=bootup+blank+screen)

---

### Post by maccawolf on 2007-03-16
Dannyboy,

 I figure I will get to the HAL issue this weekend, right now I've got too many other MAJOR issues.


ANyway, my screen res is 1024x768  (really don't wanna go back to 800x600)

I read the two pages on the link you provided, and I also have an NVIDIA card, not ATI.
As I mentioned, this was all working fine for a few days. (I've only had Unbuntu installed for less than a week now.)

I get the splash screen. I have sent the link home to look at again when I have that machine at my disposal. (at work now)

---

### Post by dannyboy79 on 2007-03-16
are you running an nvidia driver? or are you just using the default vesa or nv driver? if you're running the nvidia driver and your kernel was updated, then you need to reinstall your nvidia driver.

also, if you do
cat /var/log/Xorg.0.log 

what is at the end of it? anything about problems?

---

### Post by maccawolf on 2007-03-16
Right now, I'm just using the default drivers for everything. I figure I want to understand a bit more before I go F*CKING around with drivers and such.

Could it be my updates? I think that was one of the last things I did before I shut down the last time it worked. There were 139 updates. You think they're conflicting somewhere?

---


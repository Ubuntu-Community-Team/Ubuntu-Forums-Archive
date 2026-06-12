---
title: "sound not working"
date: 2006-10-24
forum: Absolute Beginner Talk
---

### Post by dhawald3 on 2006-10-24
I am a newbie to linux
I installed Kubunutu 6.1 on my
Pc with Intel 845gebv2 board
        ati redeon 7000 series card
        512 mb ram

The sound was running from the live cd
but after I completely installed it
I cannot hear mp3,mpg video or any other sound.

---

### Post by wpshooter on 2006-10-24
Is this the Edgy version of Kubuntu ?

If so, it is still BETA.

Have you considered the Dapper Drake 6.01.1 version of Ubuntu or Kubuntu ?

---

### Post by dhawald3 on 2006-10-24
> **wpshooter said:**
> Is this the Edgy version of Kubuntu ?

If so, it is still BETA.

Have you considered the Dapper Drake 6.01.1 version of Ubuntu or Kubuntu ?

I have 6.06 dapper drake version.

But how come the sound works in live cd,but not in complete install

---

### Post by mercurysquad on 2006-10-24
1) For mp3, wma etc. you have to install all the codecs (look at sticky thread above)

2) Otherwise, if you have the speaker icon near your clock, most probably things are fine, it's just a matter of enabling muted channels etc. In my experience with installing Ubuntu on 6-7 laptops I have noticed that most often ALSA's volume settings are set to looney defaults.

In a terminal, type **alsamixer** and then unmute all channels and set them to about 75% volume. Mute unmute is by the M key. Vol up/down is by up/down key. Then press escape, and play something.. see if it works.

---

### Post by Kateikyoushi on 2006-10-24
I doubt the live cd can play mp3 read this page for explanation why. [LINK]("https://help.ubuntu.com/community/RestrictedFormats")
If you have sound for example during login or in System >> Preferences >> Sound, then you need to install the codecs for those media files. Follow the instructions in the previous link.

If you have no sound at all read this guide to find out what is the problem. [LINK]("http://doc.gwos.org/index.php/Comprehensive_Sound_Problems_Solutions_Guide")

---


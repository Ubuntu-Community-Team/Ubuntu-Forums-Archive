---
title: "media is choppy after activating 5.1 support for speakers"
date: 2008-03-11
forum: Absolute Beginner Talk
---

### Post by Mauler5858 on 2008-03-11
Ok i am currently using alsa on my system just fine. I can play a game for instance and using exaile in the background just fine. However i was only getting 2 channel sound. I used the following etit to the asoundrc file to activate my 5.1 speakers:
```

pcm.!default {
    type plug
    slave.pcm "surround51"
    slave.channels 6
    route_policy duplicate
}


pcm.analog {
    type plug
    slave analog_slave;
}

pcm_slave.analog_slave {
        pcm surround51;
        format S32_LE;
}

```
Since then whenever i try to play media via alsa it is extremely choppy. Also if i try to open any application that uses sound, and then try to open another app that uses sound(ie open media player, then open a game). The first application only has access to sound. The other app stays muted.

If i remove this configuration i go back to 2 channel sound. I really want to get 5.1 working for media capabilities. Please help :P

---

### Post by Mauler5858 on 2008-03-11
bump

---

### Post by Mauler5858 on 2008-03-12
bump again

---

### Post by FreewareFan on 2008-03-12
It might help to know where you got the edit information from?

---

### Post by Mauler5858 on 2008-03-12
I got it from a post in the Multimedia Forum:

[http://http://ubuntuforums.org/showthread.php?t=719694]("http://http://ubuntuforums.org/showthread.php?t=719694")

---

### Post by FreewareFan on 2008-03-12
Well, I'm not sure how much this will help, but the choppy sound seems like a symptom of not having the sound buffer set high enough, especially now that you are doing the surround sound task.  It would be a logical assumption that the sound buffer needs to be increased in order to handle the extra info that it's having to process....

Just a thought....

FwF

---

### Post by Mauler5858 on 2008-03-12
Im still a linux novice.  Any advice on how to do this?

---

### Post by FreewareFan on 2008-03-12
I do not know the answer to that question.  I've done a search on Google, and it returned a lot of hits, but none of them applied to Gutsy.

Sorry, can't help you with that one...  Maybe start another thread?

FwF

---

### Post by FreewareFan on 2008-03-12
Actually, here are two sites that might just be the help you've been looking for:

[http://www.halfgaar.net/surround-sound-in-linux](http://www.halfgaar.net/surround-sound-in-linux)

[https://help.ubuntu.com/community/SurroundSound](https://help.ubuntu.com/community/SurroundSound)

FwF

---

### Post by Mauler5858 on 2008-03-14
Nice guides, will check them out when i get home.

---


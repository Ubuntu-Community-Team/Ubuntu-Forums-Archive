---
title: "Amarok Replay Gain"
date: 2008-03-03
forum: Absolute Beginner Talk
---

### Post by h-town on 2008-03-03
I'm having trouble installing the replay gain script in amarok through the script manager. After I install it and then click run for wavgain i get an error:

The script 'wavgain' exited with error code: 1
Details: Error: not enough or wrong parameters

Any ideas??

---

### Post by wulfhound on 2008-05-02
> **h-town said:**
> I'm having trouble installing the replay gain script in amarok through the script manager. After I install it and then click run for wavgain i get an error:

The script 'wavgain' exited with error code: 1
Details: Error: not enough or wrong parameters

Any ideas??

I don't think that's what you click on - look above it for replaygain or something like that.

L

---

### Post by bmike78 on 2008-05-26
Ran into the same issue on my asus eee (runs Xandros)

Go to Tools > Script Manager

Click on amarok_replaygain.py and then click Configure, then click Dependencies.

Depending on what you want to tag, you'll have to install that package dependency.  In the case of mp3's, I installed the mp3gain package:

# apt-get install mp3gain

Close out amarok and open back up.  You should see that dependency removed from the list and appear at the top as a file type you can tag.

---

### Post by Juleshu on 2008-05-30
How do you use replaygain? I extracted it, now what do I do with? The readme file is useless.

---


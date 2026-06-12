---
title: "How to reset sound to default"
date: 2008-02-14
forum: Absolute Beginner Talk
---

### Post by Afkpuz on 2008-02-14
I have messed with my sound settings and now I have no sound.  I was trying to make my external 5.1 card actually put out surround sound, but now I've broken it  Nothing is detected in System>Preferences>sound.  How can I set it back to the way it was right after a clean install?

---

### Post by eggdeng on 2008-02-14
Try running
```
asoundconf list
```
to see how alsa identifies the available sound cards. Then run
```
asoundconf set-default-card xyz
```
where xyz is the name of your onboard sound card according to the output of the 1st command.
Reboot for changes to take effect.

---

### Post by Afkpuz on 2008-02-14
No cards are listed

---

### Post by spiderbatdad on 2008-02-14
could you post the result of ```
aplay -l
```
```
cat /proc/asound/card0/codec#* | grep Codec 
```

---

### Post by Afkpuz on 2008-02-14
aplay -l
```

aplay: device_list:207: no soundcards found...

```


cat /proc/asound/card0/codec#* | grep Codec

```
cat: /proc/asound/card0/codec#*: No such file or directory

```

I was trying to install the ALSA drivers as per the instructions on the wiki.  I got hung up on some step in the middle and can't go forward or backwards.

---


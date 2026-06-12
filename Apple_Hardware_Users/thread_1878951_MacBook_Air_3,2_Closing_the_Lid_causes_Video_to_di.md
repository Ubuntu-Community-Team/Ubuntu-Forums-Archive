---
title: "MacBook Air 3,2 Closing the Lid causes Video to dissapear"
date: 2011-11-10
forum: Apple Hardware Users
---

### Post by dylanjuran on 2011-11-10
Hello guys. for the longest time i wanted to install ubuntu on my Air but it didn't have appropriate drivers and was not in the know-how to fix them myself. so now with 11.10 it's working, but not flawlessly. if ishut the lid to my MacBook Air it goes to sleep, but when i open it back up the screen is black. now when i say black i mean that it's actually displaying black image. when i suffocate the o it fades out the black to the OFF display (obviously) anyone have a fix, or know why this is?

Side note. with the lid stays open and it falls asleep, no issues. only have problems when the lid closes.

side side note. :) any way to make the trackpad not freak out when ore than one finger on it?

thanks,
Dylan Juran

---

### Post by dylanjuran on 2011-11-10
FYI i just set my settings to "do nothing" when lid is closed on both battery and power. quick fix, but not perfect. DJ

---

### Post by Ms. Daisy on 2011-11-10
System Testing worked to fix a similar issue on my PC laptop, but I don't know if it would work on apples.

---

### Post by cyberco on 2012-02-04
I have exactly the same problem. Did you ever solve it?
I've been running Ubuntu on MacBook Air's for years now but this is one of the stickiest problems I ran into (and by far the most annoying).

---

### Post by dbanck on 2012-03-02
You have to install the latest nvidia-drivers:

```
apt-get install nvidia-current nvidia-settings
```

---


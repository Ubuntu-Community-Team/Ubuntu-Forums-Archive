---
title: "ASUS X55C inner microphone problem"
date: 2013-07-20
forum: Asus Ubuntu Support (CLOSED)
---

### Post by aaronlasanta on 2013-07-20
As the title suggests, I have a problem with the internal microphone in my asus x55c. I tried in settings-inner microphone, and tested it, but it didn't respond to my voice, as if there were no microphone at all. Did anybody else have this problem? Do you know how to fix it?

---

### Post by Ubunterrific on 2013-07-31
Have a play around with

```
alsamixer
```

You type that into a terminal and adjust the volumes of specific outputs/inputs and press escape ('Esc') to quit when you're done. Look for 'mic' and 'mic boost' and boost up the input a little. Test it out while doing this, so you're not recording it *too *loudly lol There should be a nice application installed by default called 'Sound recorder' which records a sound you play and saves it as a music file. Calibrate it til it's perfect for you.

---


---
title: "ktorrent crashes"
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by diskotek on 2007-05-23
hi, 

i'm using feisty fawn without any problem. but i always had problems with torrent clients. i used azureus and bittorent before (they crashed much). and finally i stuck to ktorrent. it was nice for last 3 weeks, but after now, it crahes after 10 minutes everytime i try it.

1. how can i see the log file/crash info?
2. you have any idea from here?

thank you

---

### Post by InuyashaDuelist on 2007-05-23
What do you mean "it crashes"? What exactly happens?

---

### Post by lopagof on 2007-05-23
Same as above^^^^^^^66

---

### Post by mjukis on 2007-05-27
I found a solution in another thread. just download a new version from ktorrents homepage and the crashing wil go away.

---

### Post by diskotek on 2007-05-27
> **InuyashaDuelist said:**
> What do you mean "it crashes"? What exactly happens?

it just closed itself... i'll try the tip (downloading new version)... thank you!

---

### Post by diskotek on 2007-06-06
i upgraded to never stable version from repo's, but again same thing haapens. here is the code when i2m starting it from the terminal

```
Qt: Warning: X Error: BadDevice, invalid or uninitialized input device 157
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Qt: Warning: Failed to open device
Qt: Warning: X Error: BadDevice, invalid or uninitialized input device 157
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Qt: Warning: Failed to open device
kio (KMimeType): WARNING: KServiceType::offers : servicetype ThumbCreator not found
kio (KMimeType): WARNING: KServiceType::offers : servicetype ThumbCreator not found
kio (KMimeType): WARNING: KServiceType::offers : servicetype ThumbCreator not found
kio (KMimeType): WARNING: KServiceType::offers : servicetype ThumbCreator not found
Qt: Warning: QObject::disconnect: Unexpected null parameter
Qt: Warning: QObject::disconnect: Unexpected null parameter

```

than crashes like that

```
disko@disko:~$ Qt: Warning: QGArray::at: Absolute index 0 out of range
KCrash: Application 'ktorrent' crashing...
KCrash cannot reach kdeinit, launching directly.


```

---

### Post by diskotek on 2007-06-06
at the endd i instaalled beta version, it works better than stable releases. no problem for now.

---


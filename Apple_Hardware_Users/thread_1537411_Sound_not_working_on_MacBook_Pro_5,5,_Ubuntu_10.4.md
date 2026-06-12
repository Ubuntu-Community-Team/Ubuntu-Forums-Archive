---
title: "Sound not working on MacBook Pro 5,5, Ubuntu 10.4"
date: 2010-07-23
forum: Apple Hardware Users
---

### Post by skailasa on 2010-07-23
I installed Ubuntu on my MacBook Pro (model 5,5) yesterday. I followed the steps in the community wiki to get sound working ([https://help.ubuntu.com/community/MacBookPro5-5/Lucid#Sound](https://help.ubuntu.com/community/MacBookPro5-5/Lucid#Sound)) , but it still is not working. Could anybody please help?

Thanks!

---

### Post by Nopstnz8 on 2010-07-25
Wondering the same. This is the only major thing I still can't get working...

---

### Post by kennethsime on 2010-07-27
This was pretty much the last feature to get working for me, too. This is what worked for me:

from the terminal, run gksudo gnome-alsamixer

enter your password for sudo priveleges (sudo priveleges shouldn't be required but for me this is working better for some reason)

unmute any muted speakers (specifically the front speakers)

---


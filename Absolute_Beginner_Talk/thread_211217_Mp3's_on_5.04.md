---
title: "Mp3's on 5.04"
date: 2006-07-07
forum: Absolute Beginner Talk
---

### Post by KrisDwyer on 2006-07-07
](*,) 

Hey I'm (temporarily) running on Ubuntu 5.04, waiting for my Dapper CD's to arrive. And I got a thinking. How do you get mp3 playability on Hoary?

Thanks in advance,
Kris

---

### Post by Daiver on 2006-07-08
Hi, please see this: [http://ubuntuguide.org/wiki/Ubuntu#How_to_install_Multimedia_Codecs](http://ubuntuguide.org/wiki/Ubuntu#How_to_install_Multimedia_Codecs)

Hope it helps!

---

### Post by KrisDwyer on 2006-07-08
> **Daiver said:**
> Hi, please see this: [http://ubuntuguide.org/wiki/Ubuntu#How_to_install_Multimedia_Codecs](http://ubuntuguide.org/wiki/Ubuntu#How_to_install_Multimedia_Codecs)

Hope it helps!

Nah mate, didn't work. I'm still on Hoary :(

---

### Post by catlett on 2006-07-08
Usualy just installing mp123 and vorbiss tools with this command does it
```
 sudo apt-get install mpg321 vorbis-tools
```
But I don't have Hoary. If that doesn't work, this is a link to a listing of Hoary Hot To's [http://www.ubuntuforums.org/showthread.php?t=53050](http://www.ubuntuforums.org/showthread.php?t=53050)

---

### Post by woedend on 2006-07-08
5.04 uses gstreamer .8.  to get mp3 support you have to install the "multiverse" set of gstreamer plugins from the multiverse repo.  again, xmms will still play them by default with nothing else.

---


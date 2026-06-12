---
title: "can ubuntu play mp3 files?Plaese help!!"
date: 2006-02-13
forum: Absolute Beginner Talk
---

### Post by ramaadhitia on 2006-02-13
when i want to play my mp3 files in ubuntu with rhtymbox there are no any sounds came out from the speaker,but i can play my ogg files so what's wrong?
can you help me guys???!

---

### Post by GTvulse on 2006-02-13
[QUOTE=ramaadhitia]when i want to play my mp3 files in ubuntu with rhtymbox there are no any sounds came out from the speaker,but i can play my ogg files so what's wrong?
can you help me guys???![/QUOTE]
Enable the universe repositories and install gstreamer0.8-mad or gstreamer0.8-ffmpeg. The latter will allow you to reproduce some MPEG1/2 and MPEG4 video, a.k.a. DivX5/XviD.

---

### Post by Robgould on 2006-02-13
See the automatix link below. Playing mp3's in ubuntu is a legal grey area in the US so ubuntu does not come able by default.

---

### Post by shamrock_uk on 2006-02-13
You cannot do this by default because of licensing restrictions that would make it possibly illegal to include this capability in the shipped distro. 

Instructions [here](https://wiki.ubuntu.com/RestrictedFormats).

---

### Post by paulmilliken on 2006-02-13
Yes, ubuntu can play mp3's but not using the default setup.  You will have to follow the instructions on [https://wiki.ubuntu.com/RestrictedFormats?action=show&redirect=mp3](https://wiki.ubuntu.com/RestrictedFormats?action=show&redirect=mp3) or you can use Automatix [http://www.ubuntuforums.org/showthread.php?t=80295](http://www.ubuntuforums.org/showthread.php?t=80295) to make numerous customisations.

Paul

---


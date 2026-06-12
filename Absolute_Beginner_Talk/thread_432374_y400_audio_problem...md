---
title: "y400 audio problem.."
date: 2007-05-03
forum: Absolute Beginner Talk
---

### Post by djafar on 2007-05-03
Hi, i'm new in this forum..

i just want to ask why my audio driver won't work in ubuntu feisty..
i'm using lenovo y400 28A. Plz help.. i just can't work in this silent environment..

_djafar_

---

### Post by nanotube on 2007-05-03
[this google search]("http://www.google.com/search?q=ubuntu+y400+sound&sourceid=mozilla-search&start=0&start=0&ie=utf-8&oe=utf-8&client=mozilla&rls=org.mozilla:en-US:unofficial") might turn you onto something useful.

---

### Post by djafar on 2007-05-04
There is a thread on these forums about it [http://www.ubuntuforums.org/showthread.php?t=314383](http://www.ubuntuforums.org/showthread.php?t=314383)
--------------------------------------

I've read those thread, but it just don't work w/ my machine.. i think it's only work in ubuntu 6.. any other options?..

-djafar-

---

### Post by djafar on 2007-05-04
hm, still no answer in here..

---

### Post by isnusun on 2008-02-14
I had the same problem before. on my gutsy, the Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02) made no voice. even its driver installed correctly. 

to check wether you have same soundcard do this : 

```
# lspci |grep Audio
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)


```
then I found a link from googling, [http://anelsa.wordpress.com/2007/11/22/sound-ubuntu-lenovo-y400-33a/](http://anelsa.wordpress.com/2007/11/22/sound-ubuntu-lenovo-y400-33a/) and it works for my lenovo Y400 laptop:
i just did this : 

```
sudo vim /etc/modprobe.d/alsa-base 
```

and then add this line : 

```
options snd-hda-intel model=laptop-eapd
```

and reboot your system then

hear what happen.

---


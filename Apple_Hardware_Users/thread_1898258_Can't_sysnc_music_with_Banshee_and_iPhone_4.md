---
title: "Can't sysnc music with Banshee and iPhone 4"
date: 2011-12-21
forum: Apple Hardware Users
---

### Post by quwax on 2011-12-21
Hello,
I just installed Ubuntu 11.10 on the eeePC 1001 HA of a friend of mine.
He also has a iPhone 4 running OS 4.3.3 jailbreaked
Ubuntu 11.10 comes with the latest version of Banshee which is 2.2.1 and libimobiledevice2
The iPhone is recognized, but not under it's name, like in Unity or Shotwell but just as Apple iPhone and I can't sync - I always get the error "the mp3 format is not supported ...."
so I followed these instructions:

> 1. Jaibreak the phone (via [http://jailbreakme.com]("http://jailbreakme.com/"))
2. Install openssh from cydia
3. ssh to the phone
4. change DBVersion to 4 in the /system/library/lockdown/Checkpoint.xml
5. Generated HashInfo following the link [http://ihash.marcansoft.com/](http://ihash.marcansoft.com/)
6. copy HashInfo to the folder /var/mobile/Media/iTunes_Control/Device/
7. Reboot the phone
8. Mounted device automatically using Ubuntu Natty (libmobiledevice, ifuse and so on already installed)
9. Sync using BansheeRhythmbox on the other side doesn't recognize the iPhone at all :(
I know there are a couple of threads about this and I read them all, but didn't work.
Any further tip to make that work would be highly appreciated 
thanks
quwax

---

### Post by linuxcraze on 2011-12-21
Can you play mp3 music without iphone. i mean using only banshee without the iphone or anything attached to your pc.
If not you need to get the mp3 codecs first. you can get those for free from the fluendo website. you just need to do a free registration.

Well for the syncing part i too do have an iphone, I've tried rhythmbox but it has also failed me as it did for you. So instead I opted for another player "Clementine". It works totally fine for me. I hope it does it for you.

To install clementine use the following commands:
```

$ sudo add-apt-repository ppa:me-davidsansome/clementine
$ sudo apt-get update
$ sudo apt-get install clementine

```

---

### Post by ben2talk on 2012-05-06
Clementine just gives checksum errors...

---


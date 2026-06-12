---
title: "Transformers DVD not working (all other dvds work)?"
date: 2007-11-27
forum: Absolute Beginner Talk
---

### Post by westyonfire on 2007-11-27
Hi guys, I've just bought the transformers dvd, stuck it in my laptop and nothing happens. other dvds work fine. I've tried installing every codec ive seen mentioned online and those libraries but still nothing. VLC won't play it (it just quits itself with no error msgs), neither will movieplayer or gxine (codec error msgs)...so i have no idea what to do now.

im wondering if its to do with the dvd region. I travel quite a bit and i remember when i bought this laptop a few years ago the guy said i could change the dvd region a few times only until it locked onto a region. is this region locking thing hard wired into the dvd player or will it reset after formatting and reinstalls?...also its playing other dvds with the same region as the transformers dvd...so..wtf mate?! maybe its some new dvd encryption or something?

any help would be much appreciated.

ps. the transformers dvd in question work fine on my home dvd player.

---

### Post by OldGrey on 2007-11-27
Have a look at this it may help you.

[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs#head-780db298b62beea3e785ce27b68ec2f52d443515](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs#head-780db298b62beea3e785ce27b68ec2f52d443515)

---

### Post by ronmarley1 on 2007-11-27
My first though was that the region was different, but you say it's the same for other DVD's you can play.  I guessing here, but is it a HD-DVD?  This link may shed some light: [http://en.wikipedia.org/wiki/HD_DVD](http://en.wikipedia.org/wiki/HD_DVD)
EDIT:  in reading the link, it seems that some disks are released as hybrids (HD-DVD and regular DVD).  Maybe try flipping it over?
Sorry, just guessing here...

---

### Post by flange on 2007-12-11
Just wanted to say that I was having the same problem with the same movie as the OP.  OldGrey's link fixed it for me.  I set my just-out-of-the-box DVD drive to region 1.  MPlayer is now able to play the Transformers DVD.

Thanks!

---

### Post by PhoenixP3K on 2007-12-11
My Ubuntu install is about 2 weeks old and I had totally forgot to enable commercial DVD playback. When I poped Transformers in it wouldn't play.
```

wget -c http://packages.medibuntu.org/pool/free/libd/libdvdcss/libdvdcss2_1.2.9-2medibuntu4_i386.deb
sudo dpkg -i libdvdcss2_1.2.9-2medibuntu4_i386.deb

```
Here was a fast and easy fix :D

---


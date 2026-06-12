---
title: "Another Media Player Issue"
date: 2007-01-12
forum: Absolute Beginner Talk
---

### Post by a_dum_bum on 2007-01-12
I know there's a bunch of threads similar to this issue, but none quite like this problem I've been having, at least not that I could find.
I've mounted an ntfs partition that has all of my "my Documents" crap from windows, including a bunch of mp3s. I try opening them in Amarok or Kafeinne, and they open fine, no errors or anything. The thing is, when I click play, it'll highlight the song, "play" it for a split second, though no sound comes out, and go on to the next song.
I CAN play wavs and other formats of sound, so I figured it's got to do with the mp3 format.
I'm running kubuntu 6.0.6 with the xine engine. Any help?

---

### Post by Liolikas on 2007-01-12
Run mplayer from concole and read carefully in errors. If you are lucky it will write that some /etc/smth/andsoon/6sdsds67.dll is not found.
Then try to find that file with google using name+download and put it in his place. Create directories if they do not exist at all.

At least for me it worked. 8)

---

### Post by ComplexNumber on 2007-01-12
then you probably haven't got the right codecs to play mp3 files. fire up synaptic and download gstreamer-plugins-ugly, gstreamer-plugins-good, and gstreamer-plugins-bad.

---

### Post by slimdog360 on 2007-01-12
have you installed the restricted codecs. I think Automatix can doi this. You may also want to look at the ubuntu starter guide. Just google it if you dont know the page.

---

### Post by a_dum_bum on 2007-01-12
Thanks guys. I've been going crazy with trying to find some magical fit-all codec that will make everything work. I'll see what I can do!

---

### Post by smile_sunshine on 2007-01-12
useful links :[https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")
[http://www.psychocats.net/ubuntu/sources]("http://www.psychocats.net/ubuntu/sources")   also has clearer instructions on how to enable extra repositories which you need to do if you havent already done it before to download the packages

---


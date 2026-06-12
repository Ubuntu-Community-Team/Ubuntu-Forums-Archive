---
title: "Led Zeppelin dvd"
date: 2007-12-25
forum: Absolute Beginner Talk
---

### Post by rosswmcgee on 2007-12-25
My new Led Zeppelin dvd/will not play/ Totem says I do not have the right gstreamers. I have
/$ sudo apt-get install totem-gstreamer/ and it says I have the latest one. VLC/Kaffiene does: not recognize it either. I am lost as to what  I need to do?On startup it says could not read from source :guitar:

---

### Post by Xorg.conF on 2007-12-25
most dvd's are encrypted and you need to install a certain package in ubuntu.  

take a look at this it will solve your problem:
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)

---

### Post by spiderbatdad on 2007-12-25
do you have all the gstreamer codecs?

---

### Post by wormser on 2007-12-25
Which Zeppelin DVD did you get?  I have a 45 minute version of Dazed live in Seattle.  You did not say which version of Ubuntu you have.  I believe this is what you need.

#

For Ubuntu 7.10 Gutsy Gibbon, [other versions]("https://help.ubuntu.com/community/Medibuntu#head-7486ed038a9becc1dff10a24cc07a38a00d70e9f").

```
sudo wget http://www.medibuntu.org/sources.list.d/gutsy.list -O /etc/apt/sources.list.d/medibuntu.list
```

#

Then, add the GPG Key:

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

Install these packages.
```
sudo apt-get install libdvdread3 libdvdcss2 libxine1-ffmpeg totem-xine
```

---

### Post by Xorg.conF on 2007-12-25
not only do I have the gstreamer packages I have all that I need to play any restricted format all from a single package in add/remove, I even got the package I gave you a link to in this one, perhaps I should have given you this instead.

search Ubuntu restricted extras in add/remove and it should have everything.

---

### Post by rosswmcgee on 2007-12-25
Thanks so much tis working now. The dvd is" Live at Royal Albert Hall". Your sudos did the trick. As Iwatched the terminal I noted they removed totem gstreamer, which was contrary to their own directions.O well I am happy! Thanks again.

---

### Post by wormser on 2007-12-25
Make sure you mark the thread as Solved and give thanks with the button left of the quote button on the post that helped.

---


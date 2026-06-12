---
title: "quicktime"
date: 2007-01-17
forum: Absolute Beginner Talk
---

### Post by rbhigday on 2007-01-17
My college class requires Quicktime to view or listen to the professors lectures. What do I need to be able to load this as the things I pick do not seem to work.

Thanks

---

### Post by taurus on 2007-01-17
The media plugins from [http://www.getautomatix.com](http://www.getautomatix.com) would let you play quicktime stuff.

---

### Post by oracle5 on 2007-01-17
All I did was install vlc and nothing else to watch quicktime movies and just about everything else. I didn't have to download and special codecs or anything extra.

oracle5

---

### Post by tuxcantfly on 2007-01-17
w32codecs, gstreamer0.10-pitfdll, gstreamer0.10-ffmpeg

install those packages, you'll need the plf repos for w32codecs

also install the gstreamer0.10-good, bad, and ugly, multiverse packages, you'll need multiverse repos

---

### Post by rbhigday on 2007-01-17
> **oracle5 said:**
> All I did was install vlc and nothing else to watch quicktime movies and just about everything else. I didn't have to download and special codecs or anything extra.

oracle5

dl that and that did not work.

---

### Post by rbhigday on 2007-01-17
> **tuxcantfly said:**
> w32codecs, gstreamer0.10-pitfdll, gstreamer0.10-ffmpeg

install those packages, you'll need the plf repos for w32codecs

also install the gstreamer0.10-good, bad, and ugly, multiverse packages, you'll need multiverse repos

Does this mean I have to unload totem-xine?

---

### Post by rbhigday on 2007-01-17
ok more data.

When I play the file I get 

```
Totem could not play 'fd://0'.

Audio codex 'qualcomm purevoice' is not handled. you might need to install Additional Plugins to be able to play some types of movies
```

---

### Post by rbhigday on 2007-01-17
> **taurus said:**
> The media plugins from [http://www.getautomatix.com](http://www.getautomatix.com) would let you play quicktime stuff.

I get an ```
Fatal error: mplayer and ff plugin
An apt-based error occured and installation was unseccessful
```

---

### Post by spockrock on 2007-01-17
does the file work with vlc or mplayer??

---

### Post by rbhigday on 2007-01-18
> **spockrock said:**
> does the file work with vlc or mplayer??

that is a negative to both

---

### Post by rbhigday on 2007-01-18
Ok it now loads but does not play, go figure :)

I get with xine
Unsupported codec:

Audio Codex: Qualcomm PureVoice (Qclp)

any idea where to find this?

---

### Post by upallnight on 2007-01-26
I am having the same problem with my school video files. It needs the Qualcomm Purevoice codec for the audio. The video works fine for me, but without sound. The codec for windows is installed from a cd, but I don't know how to get it to play in totem on linux.

---

### Post by upallnight on 2007-01-27
Here is a website with a unix codec for download:

[http://www.cdmatech.com/products/purevoice_download.jsp](http://www.cdmatech.com/products/purevoice_download.jsp)

However, I don't know how to get it to work with a linux media player.

---


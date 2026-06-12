---
title: "WMV problems"
date: 2007-06-30
forum: Absolute Beginner Talk
---

### Post by akschnare on 2007-06-30
I have looked everywhere and I still can't figure out how to get wmvs to play in Feisty. I can get picture, but I don't get sound. If anyone knows why it sure would be a great help. Thanks.

---

### Post by AndyCooll on 2007-06-30
You need to install w32codecs.

:cool:

---

### Post by akschnare on 2007-06-30
Thanks... how do I do that?

---

### Post by Seisen on 2007-06-30
```
sudo apt-get install w32codecs
```

But it is illegal to use them in the United States, because its copyright infringment.

---

### Post by bashologist on 2007-06-30
> **akschnare said:**
> Thanks... how do I do that?

Here's how I always do it. It works fine for me but use with caution. This method will use Mplayer to play it, but other players might work as well.

Open a terminal with:
Applications -> Accessories -> Terminal

Then copy and paste:
```
sudo apt-get install mplayer; if which mplayer; then cd /tmp; if wget http://www1.mplayerhq.hu/MPlayer/releases/codecs/all-20061022.tar.bz2; then tar -xvjf all-20061022.tar.bz2; sudo mkdir /usr/lib/win32; sudo mv all-20061022/* /usr/lib/win32/; fi; else echo "install mplayer first"; fi
```

Then try opening the movie with Mplayer. If it gives you some error message try changing the video driver in Mplayers preferences.

---

### Post by RomeReactor on 2007-06-30
If you still want to install w32codecs, you'll need to add the [Medibuntu]("https://help.ubuntu.com/community/Medibuntu") repositories to your **/etc/apt/sources.list**; after that's done, search for **w32codecs** in Synaptic.

---

### Post by cogadh on 2007-06-30
> **Seisen said:**
> But it is illegal to use them in the United States, because its copyright infringment.
No one really knows for sure if these are legal or not in any country. Since the w32codecs package does not allow for the decrypting of encrypted or protected content, it only allows the playback of such content, it may not be illegal in the US at all (it doesn't violate the DMCA). However, they could be a copyright violation, since they are apparently a direct copy of the Windows proprietary codecs. That would make them illegal in any country where MS has copyrights or patents, not just the US. Then again, this could be one of those occasions where the ownership of a legitimate Windows license means you are also free to posses the codecs package. To my knowledge, there has been no official ruling on this and the status of this package is still up in the air.

---

### Post by akschnare on 2007-06-30
Thanks. I got the sound to work, but it seems to skip every second or so, until it just cuts out completely. Does anyone know why? I mean, this file plays well in Windows but I don't want to have to reboot just to play a 2 minute video.

---

### Post by RomeReactor on 2007-07-01
**akschnare**, try opening your video player from the terminal by writing it's name (**totem, mplayer** or **vlc**) and pressing enter, then opening one of the files that are giving you trouble; it might leave messages there that could be helpful in diagnosing the problem. Also, if you have Beryl, try disabling it and play a video then.

---


---
title: "Lag when streaming audio"
date: 2006-09-04
forum: Absolute Beginner Talk
---

### Post by 3rr0r on 2006-09-04
Hi,  I stream audio from [http://www.radioblogclub.com](http://www.radioblogclub.com)

Anyways, when I was streaming my music and web surfing I had no problem, but it seems whenever i click on a link or do anything that uses any bandwidth it lags my musics for 1/2 a sec or so...

Any reason why it would lag in Ubuntu but not in XP ?  My connection hasn't changed any.  Also, I would like to add that you need flash player to stream the audio and installing flash was not fun in ANY way, learning experience yes, but still proved to be very difficult.

---

### Post by xyz on 2006-09-04
Hi-
Try to check if you've got DMA on. For HowTo, go here:
[https://help.ubuntu.com/community/DMA](https://help.ubuntu.com/community/DMA)

---

### Post by bodhi.zazen on 2006-09-04
> **3rr0r said:**
> Hi,  I stream audio from [http://www.radioblogclub.com](http://www.radioblogclub.com)

Anyways, when I was streaming my music and web surfing I had no problem, but it seems whenever i click on a link or do anything that uses any bandwidth it lags my musics for 1/2 a sec or so...

Any reason why it would lag in Ubuntu but not in XP ?  My connection hasn't changed any.  Also, I would like to add that you need flash player to stream the audio and installing flash was not fun in ANY way, learning experience yes, but still proved to be very difficult.

Not sure this helps, but for streaming try streamtuner.

---

### Post by 3rr0r on 2006-09-04
> **bodhi.zazen said:**
> Not sure this helps, but for streaming try streamtuner.

linky please?

---

### Post by 3rr0r on 2006-09-04
> **xyz said:**
> Hi-
Try to check if you've got DMA on. For HowTo, go here:
[https://help.ubuntu.com/community/DMA](https://help.ubuntu.com/community/DMA)

Let me rephrase...

When I use Xp and stream music from my site, no lag.  I can download programs while streaming, view multiple webpages and my music does not lag.

Now, I use Ubuntu, and load A page causes delay in my music, streaming from the same site that I use to use.  

What I want to know is, why does it lag in Ubuntu, but not in XP ?

---

### Post by bodhi.zazen on 2006-09-04
> **3rr0r said:**
> linky please?

[streamtuner](http://www.nongnu.org/streamtuner/)

Install via synaptic or:
```
apt-get install streamtuner
```

---

### Post by 3rr0r on 2006-09-04
> **bodhi.zazen said:**
> [streamtuner](http://www.nongnu.org/streamtuner/)

Install via synaptic or:
```
apt-get install streamtuner
```

thank you very much!

---

### Post by bodhi.zazen on 2006-09-04
Not sure about your lag problem. Could be you do not have the proper drivers for your sound card, your downloader takes up all your bandwidth, I just don't know.

I do not have this problem so it is not inherent to Linux, Ubuntu, or streaming (via streamtuner) or downloading (via d4x).

---


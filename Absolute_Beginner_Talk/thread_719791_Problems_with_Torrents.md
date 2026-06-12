---
title: "Problems with Torrents"
date: 2008-03-09
forum: Absolute Beginner Talk
---

### Post by gustasonfrever on 2008-03-09
Every time I download a torrent and use it (I've tried deluge, frostwire, transmission, azureus) my computer crashes. Would it be my internet provider? I have comcast if that helps

---

### Post by Flying caveman on 2008-03-09
Yes. Its Comcastic isn't it.  

I have comcast and this worked for me, [http://www.tweak3d.net/forums/tech/possible-fix-comcast-torrent-blocking-28264](http://www.tweak3d.net/forums/tech/possible-fix-comcast-torrent-blocking-28264)

so for example, ktorrent uses port 6881 you would use ```
sudo iptables -A INPUT -p tcp --dport 6881 --tcp-flags RST RST -j DROP

```

---

### Post by gustasonfrever on 2008-03-09
How do I find out what port im using?

---

### Post by Flying caveman on 2008-03-09
it depends on what torrent client you're using,  Like in my example kTorrent uses 6881 by default, but you can change it if you want to.  I'm sure the other clients allow you to change which port they use also.  

I haven't used the other ones you mentioned except, azureus.  so I don't know.

---

### Post by The Titan on 2008-03-09
your computer crashes, i doubt a port can cause this... thats a little intense

---

### Post by Flying caveman on 2008-03-09
Maybe he meant his internet, crashes???  Before I did this, my internet would stop when I tried to use ktorrent, and I would have to reset my router to get it working again.  maybe even the client crashed too, but not my computer.

---

### Post by The Titan on 2008-03-09
> **Flying caveman said:**
> Maybe he meant his internet, crashes???  Before I did this, my internet would stop when I tried to use ktorrent, and I would have to reset my router to get it working again.
thats still strange.  Do you know what causes this?

off-topic: love your sig.

---

### Post by Flying caveman on 2008-03-09
> **The Titan said:**
> thats still strange.  Do you know what causes this?

off-topic: love your sig.


I only have a general understanding of how this works.  What comcast is doing is sending a packet that will reset your connection,  That, command ```
sudo iptables -A INPUT -p tcp --dport 6881 --tcp-flags RST RST -j DROP 
```
blocks the reset packet.

I'm guessing the reset packet doesn't just stop communications on that port, it resets everything.   I think some torrent clients switch ports randomly,to get around some other method of stopping them, so it kills them too.

I actually like the smell of patchoulli :)

---

### Post by The Titan on 2008-03-09
that makes sense, i was just wondering for future reference. It's no big deal.

> 
I actually like the smell of patchoulli


I just el-oh-el'ed for real.  Thanks for the laugh.

---

### Post by Flying caveman on 2008-03-09
Quote:
Originally Posted by gustasonfrever View Post
I have a Pentium III 753mhz Dell with 128 mb of RAM.

Yeah dude! get more RAM.

---


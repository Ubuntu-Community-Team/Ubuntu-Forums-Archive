---
title: "iPod Classic on Ubuntu"
date: 2008-02-20
forum: Absolute Beginner Talk
---

### Post by ImThatNerd on 2008-02-20
Well since I do not have windows I have to try and find an app so my ipod can have their own library(Like itunes) and my brother can his own, I read this thread:

[http://ubuntuforums.org/showthread.php?t=619615](http://ubuntuforums.org/showthread.php?t=619615)

But it didn't work for me. When I connected my ipod to my computer Rythmbox popped up and showed all my music. I haven't heard anything about it allowing you to try and put music on your ipod so I was afraid to try it, since if it erased my music I would have no way to put it back on. My iPod is the new 6G Classic, 80GB. 

If there is an up-to-date tutorial on how to get an ipod 6g working on Ubuntu so I can have my own library, same with brother and are able to put our music on our ipods. He has a 1G or 2G Nano.

---

### Post by TheOrangePeanut on 2008-02-20
[http://lilserenity.wordpress.com/2007/12/22/virgin-mobile-praise-ubuntu-and-ipod-nano-3g/](http://lilserenity.wordpress.com/2007/12/22/virgin-mobile-praise-ubuntu-and-ipod-nano-3g/)

This is how I got my Ipod Classic to work.  I don't know if it works with Rhythmbox (I'd assume it does, since RB uses libgpod), but I do know that it works with Amarok.

---

### Post by wolfen69 on 2008-02-20
just open the ipod like you would any attached drive,(close rhythmbox) copy and paste the files to a folder to back them up. then see if you can add music to it.

---

### Post by ImThatNerd on 2008-02-20
> **TheOrangePeanut said:**
> [http://lilserenity.wordpress.com/2007/12/22/virgin-mobile-praise-ubuntu-and-ipod-nano-3g/](http://lilserenity.wordpress.com/2007/12/22/virgin-mobile-praise-ubuntu-and-ipod-nano-3g/)

This is how I got my Ipod Classic to work.  I don't know if it works with Rhythmbox (I'd assume it does, since RB uses libgpod), but I do know that it works with Amarok.

I followed it. Plugged in iPod, showed my music. Copied over 1 song. Song copied over and played. I noticed none of my album art shows up....

Also why wont Rythmbox let me edit song name and artist and all that?

---

### Post by doorknob60 on 2008-02-20
Maybe Rythmbox doesn't work with album art? Try using Amarok, it might fix both problems.
Type this into a terminal to install Amarok:
```
sudo apt-get install amarok
```

---

### Post by Xodarap on 2008-02-21
I followed the post given above and installed a newer version of gtkpod; I was able to successfully transfer music onto my iPod but now it won't play (when I hit play it goes to the play screen but is just stuck at 0:00). Any ideas?

Alternatively (or, ideally, in addition to), does anyone know of a way to do the equivalent of the "reset" available from iTunes?

---


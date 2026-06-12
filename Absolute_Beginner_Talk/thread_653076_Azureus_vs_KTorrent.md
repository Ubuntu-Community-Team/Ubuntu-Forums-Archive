---
title: "Azureus vs KTorrent"
date: 2007-12-29
forum: Absolute Beginner Talk
---

### Post by tonycm1 on 2007-12-29
I'm debating between installing either Azureus or KTorrent on my Ubuntu 7.10 Gutsy laptop.

I've heard that Azureus is Java based and can consume a lot of resources (which would not be good for an old laptop such as mine)

I've also heard that KTorrent is KDE based, so to install it in a GNOME environment (such as Ubuntu 7.10 Gutsy), I need to install additional files (libs?) which also take up resources.

So I just wanted to get some feedback from the forum what would be recommended?
:confused:

---

### Post by bigyoy on 2007-12-29
I use Azureus. For some reason I couldn't get KTorrent working through my router even after playing around with port numbers whereas Azuereus seemed to work with little messing about.

As for system hogging, I haven't noticed it on my Athlon 3200 xp with 1gb ram. 

If I were you, I would try azureus and if you don't get on with it, look into Ktorrent or something else.

---

### Post by TidusBlade on 2007-12-29
Azureus is really a resource hog so I wouldnt recommend it, and since you use GNOME, why not check out Deluge, can be found in the repos (Synaptic). nice full featured and lightweight, complete with plug ins ;)
Or use this command to install it:
```
sudo apt-get install deluge
```

---

### Post by jonnywombat on 2007-12-29
I too would recommend deluge.. It has a simple gui but has a lot of options neatly tucked away..

Jonny

---

### Post by hyper_ch on 2007-12-29
If you want to go very slim or very geekish or be able to control your torrent client from a pure ssh connection, you can also use rtorrent.

---

### Post by funrider on 2007-12-29
ktorrent has many plugins to play with, like uPnP, better tracking of individual files

also you can allocate CPU and memory for the program, pretty customizable.

---

### Post by Hallvor on 2007-12-29
For Gnome, I`d recommend Deluge too.

---

### Post by Famous Mortimer on 2007-12-30
I'm also in a similar situation, having just switched to Ubuntu from Windows and being a bit "aaarrgghh! Stuff, but what to download?" Well, time to have a go and see what I can see.

---

### Post by hyper_ch on 2007-12-30
of course you could also run µTorrent trough wine...

---

### Post by Liolikas on 2007-12-30
> **hyper_ch said:**
> If you want to go very slim or very geekish or be able to control your torrent client from a pure ssh connection, you can also use rtorrent.
Yes I agree. With **rtorrent** you will need some time to learn it and configure, but it is more than worth to do it.
Then you can hide your downloads in terminal like alt+ctrl+f2 and back to GUI with alt+ctrl+F7. ;)
And with good configuration you just have to download .torrent file with Firefox and from this point rtorrent overtakes the job. No even single click needed. That rocks :lolflag:
And fact that rtorrent use extreamly small amount of resources rocks even more.

---

### Post by hyper_ch on 2007-12-30
even better to run rtorrent in a "screen" ;) it doesn't take much time to learn ;)

---

### Post by KhaaL on 2007-12-30
The only "problem" Ktorrent have is that it's unpopular on private trackers...

---

### Post by atomkarinca on 2007-12-30
Why don't you give Transmission a go? It's very lightweight and once you get the hang of it, it's no different from other alternatives.

```
sudo apt-get install transmission
```

---

### Post by TidusBlade on 2007-12-30
Also gotta agree with rtorrent! Really easy to learn, in my opinion. and runs with extremely little resources, and I find it popular on many private trackers, if thats what you use. But it had no GUI, so if you need one, thats a different story.

---


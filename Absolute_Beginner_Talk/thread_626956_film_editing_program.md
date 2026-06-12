---
title: "film editing program"
date: 2007-11-29
forum: Absolute Beginner Talk
---

### Post by kahram.yoon on 2007-11-29
Does ubuntu have an advanced video editing program? I also have a question on downloading adobe premier pro CS3.  If i download it from a torrent website, will i be able to install it and if i do, what will i have to do in order to install it?

---

### Post by Matthew Bartram on 2007-11-29
I think Kino is supposed to be quite good for video editing. Though when I tried it some time ago it wouldn't work.

Is that a Windows version of Adobe Premier Pro? Or have they got a linux version? If it's the standard windows one, I doubt it will work well - it might work with wine, but I expect there's a good chance that if it did it would go slow, video editing (as I understand it) being such an intensive process.

---

### Post by mpgarate on 2007-11-29
ive poked around at everything, and the easiest to use is kdenlive

sudo apt-get install kdenlive


its fairly buggy, but better than everything else. Video editing is the only part of linux that dissatisfies me.

---

### Post by ptn107 on 2007-11-29
You check out Ubuntu Studio yet? [http://ubuntustudio.org/](http://ubuntustudio.org/)

If you have Ubuntu 7.10 installed you can just install the video applications from Ubuntu Studio 7.10
```
sudo apt-get install ubuntustudio-video
```
Which includes cinepaint, dvgrab, ffmpeg, ffmpeg2theora, kino, pitivi, stopmotion


To completely install Ubuntu Studio from Ubuntu:
```
sudo apt-get install ubuntustudio-desktop
```

Or download the DVD image:
[http://ubuntustudio.org/downloads](http://ubuntustudio.org/downloads)

---

### Post by ijason on 2007-11-29
is ubuntustudio supposed to be a custom release of ubuntu? or just a suit of programs to run on your existing ubuntu?

---

### Post by KCPokes on 2007-11-29
> **mpgarate said:**
> ive poked around at everything, and the easiest to use is kdenlive

sudo apt-get install kdenlive


its fairly buggy, but better than everything else. Video editing is the only part of linux that dissatisfies me.

+1 for Kdenlive.  

I use Kino to pull my video from my camcorder, kdenlive to edit and add effects, and finally mandvd to create the menus and burn the final disk.  Of course you can do most of that in one program, but I went the route of multiples to suite my needs.

---

### Post by mgmiller on 2007-12-02
I also add +1 for kdenlive.

KCPokes said:
> I use Kino to pull my video from my camcorder, kdenlive to edit and add effects, and finally mandvd to create the menus and burn the final disk.  Of course you can do most of that in one program, but I went the route of multiples to suite my needs.

I am curious: 
1) why don't you use kdenlive to import from your camcorder?
2) What is the "One program" you refer to?

---


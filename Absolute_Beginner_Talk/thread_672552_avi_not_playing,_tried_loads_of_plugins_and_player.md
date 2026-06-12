---
title: "avi not playing, tried loads of plugins and players"
date: 2008-01-19
forum: Absolute Beginner Talk
---

### Post by Sunlust on 2008-01-19
Hi, i have a avi movie, I'm not sure how it's encoded recently ripped by my mate for me, so that I can play it on my computer.
Problem is that I can't play it.
I tried restricted formats or whatever its called, i read about 4-5 hot to's and nothing helps, I tried Smplayer, Mplayer, Totem, VLC, nothing opens the movie.
Totem just says that it doesn't have a plugin, Mplayer freezes, Smplayers just doesn't do anything, VLC "pretends to play it" but nothing happens except the timebar moving and no voice, I also tried automatix to install all plugins etc, nothing works...

Any tips?

---

### Post by SunnyRabbiera on 2008-01-19
hmm, I am wondering if this is a windows media 11 file...
if so this might not be possible

---

### Post by meborc on 2008-01-19
have you installed ubuntu-restricted-extras package? ... it sounded like you have, but i just wanted to be sure...

if it is a standard .avi file, then any given media player should be able to play it... are you sure the file is OK?

---

### Post by billgoldberg on 2008-01-19
.avi isn't actually a "real" file type. It could be alot of codecs.

If vlc can't play it the file could be bad.

Did you install dvd support, I don't know if it helps but it could).

Maybe this could help?

[http://ubuntu.wordpress.com/2005/12/04/libdvdcss2-and-w32codecs-for-ubuntu/](http://ubuntu.wordpress.com/2005/12/04/libdvdcss2-and-w32codecs-for-ubuntu/)

---

### Post by Sunlust on 2008-01-19
> **SunnyRabbiera said:**
> hmm, I am wondering if this is a windows media 11 file...
if so this might not be possible

Well, it might be, since it's really recent, I think it was an xvid, whatever it means, i'm not really into this stuff to be honest.

---

### Post by Sunlust on 2008-01-19
> **meborc said:**
> have you installed ubuntu-restricted-extras package? ... it sounded like you have, but i just wanted to be sure...

if it is a standard .avi file, then any given media player should be able to play it... are you sure the file is OK?

Yeah I have them...




> **billgoldberg said:**
> .avi isn't actually a "real" file type. It could be alot of codecs.

If vlc can't play it the file could be bad.

Did you install dvd support, I don't know if it helps but it could).

Maybe this could help?

[http://ubuntu.wordpress.com/2005/12/04/libdvdcss2-and-w32codecs-for-ubuntu/](http://ubuntu.wordpress.com/2005/12/04/libdvdcss2-and-w32codecs-for-ubuntu/)

I have libdvdcss2 installed :/
I am not sure about how the file is.

What I noticed is that, it actually shows as a video file, but sometmies the icon is as a text file, does it mean it's broken?

---

### Post by jleaker01z on 2008-01-19
If this is something you downloaded off a P2P program, the RIAA, MPAA etc intentionally upload bad files to frustrate consumers of pirated software.  So it is not uncommon for files obtained this way to not work.

Not that I am implying you would be doing anything illegal, or that I have learned this from experience or anything. :popcorn:

---

### Post by jeffbilling on 2008-01-19
I download lots of YouTube .avi  files of woodturning and they all work fine.
Why not download a small YouTube file and see if it works - if it does then you know it is probably the file you have been given that is the problem.

---

### Post by jeffbilling on 2008-01-19
Further to my last message - I am using Totem Movie Player

---

### Post by RomeReactor on 2008-01-19
Hi. Which backend are you using with Totem--Gstreamer or Xine? If it's Xine you may need more packages:
```
sudo aptitude install libxine1-ffmpeg libxine1-plugins libxine1-gnome
```
Also, try right-clicking on the .avi file, select 'Properties', then go to the last tab and post what you find there.

---

### Post by Thund3rstruck on 2008-01-20
When I build new machines I just follow the [Ubuntu Guide]("http://www.ubuntuguide.org") and install DVD support and W32Codecs. I've never had any trouble playing anything I've tried (avi, divx, xvid, etc, etc)

---

### Post by Sunlust on 2008-01-20
eh, nothing helped, about testing on another avi, I don't have a stable internet connection to download anything from youtube to test, I'm on my neighbours wifi ...
thanks for trying, eh.

---


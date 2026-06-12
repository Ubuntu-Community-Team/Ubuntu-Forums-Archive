---
title: "open office presentation"
date: 2008-01-15
forum: Absolute Beginner Talk
---

### Post by celticbhoy on 2008-01-15
[SIZE="4"][COLOR="SeaGreen"]I run a pub which has a couple of TV's which mostly show sport. One of these is connected to a DVD player. I have made a presentation in OO presentation, and I want to know the best way to transfer this to a DVD to show on the TV. I realise that I may have to show this as a simple slideshow, rather than as a fancy presentation, and that will be OK, I just need to know the steps involved, and if I will require any other software.

Thanx in advance for any suggestions and solutions.[/COLOR][/SIZE]

---

### Post by ryana on 2008-01-15
You could get a video card with video out and run the cables to the televisions...
Or... [http://www.linuxforums.org/forum/suse-linux-help/48343-photo-slideshow.html](http://www.linuxforums.org/forum/suse-linux-help/48343-photo-slideshow.html)

---

### Post by celticbhoy on 2008-01-15
No good, PC is in the house, and I want to show in the bar.

---

### Post by polmir on 2008-01-15
try it
**dvd-slideshow** --- This is the main script. It generates a DVD-compatible MPEG2 video file
with audio from a text file input listing of pictures and effects.

**qdvdauthor** --- GUI frontend for dvdauthor and other related tools

```
sudo apt-get install dvd-slideshow
sudo apt-get install qdvdauthor
```

[http://dvd-slideshow.sourceforge.net/wiki/Main_Page]("http://dvd-slideshow.sourceforge.net/wiki/Main_Page")
[http://qdvdauthor.sourceforge.net/]("http://qdvdauthor.sourceforge.net/")

---

### Post by celticbhoy on 2008-01-15
I guess this works from individual pics. It looks like it will work, but as a matter of interest, is there anything that will do it from a presentation file automatically ??

---

### Post by celticbhoy on 2008-01-16
Just a thought is there a screen recorder that will save to a video format that i could start and then record the presentation and edit with video editing software before burning?

---


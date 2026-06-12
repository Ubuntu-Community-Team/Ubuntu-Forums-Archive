---
title: "What is MPD and how Do i Make it Work with Conky?"
date: 2007-10-01
forum: Absolute Beginner Talk
---

### Post by R-Dot-Yung on 2007-10-01
What is MPD and how Do i Make it Work with Conky?

---

### Post by R-Dot-Yung on 2007-10-01
bump

---

### Post by R-Dot-Yung on 2007-10-01
Buhdump

---

### Post by 3rdalbum on 2007-10-02
MPD == Music Player Daemon.  It sits in the background and plays music; you can control it from a graphical frontend (or from the web). I don't know if there is a Conky plugin for it.

---

### Post by skipo on 2007-11-22
> **R-Dot-Yung said:**
> What is MPD and how Do i Make it Work with Conky?

Info about MPD:

[http://mpd.wikia.com/wiki/Main_Page]("http://mpd.wikia.com/wiki/Main_Page")

You also need to install some client to control MPD.

When you have successfully installed MPD you can show info about it in Conky. You have to edit .conkyrc. For example you can put these lines under the line TEXT:
```
${if_running mpd}
$mpd_smart
$mpd_album
$mpd_status $mpd_elapsed/$mpd_length
$endif
```

It shows artist, song, status of mpd and elapsed time/length of song.

For some reason, when I kill mpd, conky dies also. Really annoying.

---

### Post by alphane on 2007-11-29
Same issue here, skipo.

If I stop the MPD via terminal, conky bails out also.  I've wrapped the conky variables in an {$if_running mpd} ... {$end if} (not sure on syntax there, but it's right in my conky, and I'm at work) but the issue prevails.

I've just taken to stopping / pausing the MPD track rather than killing it, it's really low on resources, so I'm not too fussed, but would be good to know what's going on.

---


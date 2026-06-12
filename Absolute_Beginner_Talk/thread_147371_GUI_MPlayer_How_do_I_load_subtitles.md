---
title: "GUI MPlayer: How do I load subtitles?"
date: 2006-03-20
forum: Absolute Beginner Talk
---

### Post by tux101 on 2006-03-20
The video I am trying to watch includes subtitles.  The only option I found is loading subtitles as a seperate file.  How do I select built-in subtitles?

---

### Post by Pragmatist on 2006-03-20
This site explains you must do it on the command line:
from: [http://www.linux.com/howtos/DVD-Playback-HOWTO/usage.shtml](http://www.linux.com/howtos/DVD-Playback-HOWTO/usage.shtml)
> Subtitle and audio options for MPlayer have to be specified on the command line. The format is -alang NN or -slang NN where NN is the two-letter language code of the language you want. For example, to play back Japanese audio with English subtitles, type:  # mplayer dvd://1 -alang ja -slang en 

Here is Mplayer's explanation of your extensive subtitles options:
[http://www.mplayerhq.hu/DOCS/HTML-single/en/MPlayer.html#subosd](http://www.mplayerhq.hu/DOCS/HTML-single/en/MPlayer.html#subosd)

---

### Post by mlind on 2006-03-20
If you find MPlayer akward, try VLC media player. It's very good and supports
subtitles too. It's available via apt-get.

---

### Post by tux101 on 2006-03-20
It's not DVD.  It's a video file.

How would I select Channel 1 of the subtitle options?  Or if the option is 'English[eng]'?

---

### Post by Pragmatist on 2006-03-20
What kind of video file?  Please give filename extension (.avi .vob .mov.....)

---

### Post by mlind on 2006-03-20
well if it's somekinda format that supports embedded subtitles, then you just
select the appropriate video track. On VLC you can select video track from 'Video'
menu.

---

### Post by tux101 on 2006-03-20
[QUOTE=Pragmatist]What kind of video file?  Please give filename extension (.avi .vob .mov.....)[/QUOTE]
avi, mkv, ogm.

---

### Post by bored2k on 2006-03-20
[QUOTE=tux101]The video I am trying to watch includes subtitles.  The only option I found is loading subtitles as a seperate file.  How do I select built-in subtitles?[/QUOTE]
Press the M (or J; forgot) button. The OSD should display what is is currently selecting.

---


---
title: "Democracy and feisty ppc... does it work"
date: 2007-11-29
forum: Apple PPC Users
---

### Post by skj on 2007-11-29
when I go to watch a downloaded clip, say from you tube, it justs closes without playing.

what am I doing wrong?  I installed it from add/remove programs.

---

### Post by Twiggy003 on 2007-11-30
I have the very same problem on my ibook g4, but I use Gnash now for my youtube viewing, seems to almost work.

---

### Post by skj on 2007-12-01
twiggy,

I have democracy, vlc, totem and gnash installed. For kicks I un-installed vlc. here's what happened:

Like you say, gnash almost works.  With a you tube video, it starts, or at least wants to start.  What happens is that the clip gets ready to play but the window where it plays from is just a light tan screen instead of the video.  It goes through the motion of loading but stops there.

Also, wmv files don't play in anything either.

Any ideas?

---

### Post by oswaldkelso on 2007-12-01
> **skj said:**
> twiggy,

I have democracy, vlc, totem and gnash installed. For kicks I un-installed vlc. here's what happened:

Like you say, gnash almost works.  With a you tube video, it starts, or at least wants to start.  What happens is that the clip gets ready to play but the window where it plays from is just a light tan screen instead of the video.  It goes through the motion of loading but stops there.

Also, wmv files don't play in anything either.

Any ideas?
Mplayer can play wmv and wma You may need to install some libs or codexs?

I cant get gnash to work but on my debian ppc box but all the other players work including miro >there is an issue when using the totem plugin and the mplayer plugin for mozila. As I understand it  you need to use one or the other

#To get and play youtubevideo I installed clive then I add the address of the video

Code:

$ clive [http://www.youtube.com/watch?v=yCYzn6K59oI](http://www.youtube.com/watch?v=yCYzn6K59oI)
clive-0.3.3/nomad (python-2.4.4/urlgrabber-3.1.0)
kb/s: off  gzip:yes  agent:iveogo/1.0.4
o/w : off  r/n : off  proxy: off
play: off  r/en: off  ffmpg: off
status: 17KB 100% (1 of 1) [[http://www.youtube.com/watch?v=yCYzn6K59oI...]](http://www.youtube.com/watch?v=yCYzn6K59oI...])
status: checking file length... 13.768MB
queue: 1 (total: 13.768MB), failed: 0, skipped: 0.
write: /home/g5/UbuntuBerylMiroAndTheStringCheeseIncident.flv
transfer: 13.768MB / 13.768MB (100%) [00:00:00]      97.00KB/s


To play type the name of the player and the name of the downloaded file (use tab complete) for eg to enter the line belowI did mpla TAB then Ub TAB

#code:
$ mplayer UbuntuBerylMiroAndTheStringCheeseIncident.flv 
or
$ vlc UbuntuBerylMiroAndTheStringCheeseIncident.flv 
or
$ xine UbuntuBerylMiroAndTheStringCheeseIncident.flv 

etc

---


---
title: "Can't type in Kismet (edgy)"
date: 2006-11-12
forum: Absolute Beginner Talk
---

### Post by Big D on 2006-11-12
[B][SIZE="4"][/SIZE]
This is a Kismet problem that is probably not a a kismet problem:-k .
[SIZE="5"]I can't type in Kismet.[/SIZE]
I got kismet apt-get and made sure I got as many recommendeds as possible but for some reason my key strokes do nothing in Kismet.  Everything works fine except that I can't do any keystrokes.  (I turned off the pop up in kismet_ui.conf).  
I have a Netgate 2511 (I like it a lot).

1.  My changes to the kismet.conf are:
      suiduser=me
      source=wlanng,eth2,none
      gps=true
      waypoints=true
      waypointdata=~/.gpsdrive/way.txt

2.  I start kismet in one of two ways:
      I use airsnort to set the card in rfmon
       I look at kismet

or 
      I use airsnort to set the card in rfmon
      I enable gpsd 
      I start kismet

I just reinstalled edgy after trying to fix the problem by installing the tarball.  It was working fine when I first got it which is one of the reasons why I reinstalled edgy.  

Oh yeah: I tried setting the ui to curses instead of panels but that didn't change anything.

Thanks in advance for anyone who might help with this miscellaneous problem.:)

---


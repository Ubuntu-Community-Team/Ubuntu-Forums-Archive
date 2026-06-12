---
title: "A Couple of Newbie Questions."
date: 2006-03-19
forum: Absolute Beginner Talk
---

### Post by xshady87 on 2006-03-19
So I just got Ubuntu to work, but I still have a few questions. First of all, I don't have any sound. I have a SoundBlaster Audigy LS, and I tried looking on the website for drivers, but found none. Secondly, I would like to know how to play .wmv files on Totem. The HowTo on this was kind of complicated, so if anyone could dumb it down, that would be great. Finally, my internet is runnning a little slow. Again, any help pn these topics would be great. Thanks a lot!

---

### Post by varunus on 2006-03-19
I've seen a couple posts about sound issues with that card...Search around the forum, it should fix your problem.

Also, to get codecs and everything, use Automatix.  Its an addon program for Ubuntu that does a whole bunch of stuff; it will set up codecs (and, if you want, a whole bunch of stuff like flash, java, dvd support, etc).
[http://www.ubuntuforums.org/showthread.php?t=138405](http://www.ubuntuforums.org/showthread.php?t=138405)

---

### Post by xshady87 on 2006-03-19
I installed Automatix and updated everything, but for some reason, .wmv video files still aren't playing. Also, the internet's still running a LOT slower than it was on windows.

---

### Post by varunus on 2006-03-19
Try opening up synaptic and installing totem-xine...automatix should install it, though.  Also, did you do the "commerical codecs" option in automatix?

For net speed...what kind of connection are you on?  I can't think of anything off the top of my head except that maybe (if you're using a router) that your router doesn't support IPV6.  Do you know if your router supports IPV6, or is it IPV4 only?

---

### Post by xshady87 on 2006-03-19
Automatix isn't showing a 'commercial codecs' option, just 'multimedia codecs'.

---

### Post by Jimmey on 2006-03-20
The internet thing is most probably one of two things:

The first is that it could be a IPv6 problem. I've no idea about that.
The second is a DNS problem. If you're using an in-correct DNS address, things're going to run slowly. If you're running a decent router, then change the DNS address to match the default gateway ( the default IP the router has. Mine's 192.168.1.1 ). If you're not running a router, your ISP will be happy to help you out.

---


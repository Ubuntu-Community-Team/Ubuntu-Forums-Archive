---
title: "Sound on Democracy TV (youtube videos)"
date: 2006-10-15
forum: Absolute Beginner Talk
---

### Post by findus on 2006-10-15
Hi,
Have been playing with Democracy TV player which is amazing!  However, when I download videos from youtube through it (flv videos?) I can't get any sound.  I have the flash plugin installed, and have configured firefox with aoss so I get sound, and wondered what I needed to do to get sound on Democracy with flash videos.  

Hope someone can help!

Fin

---

### Post by Coda on 2006-10-21
0.9.0 doesn't support FLV videos, unfortunately. 0.9.1 does, but it's not available for Ubuntu yet.

[http://www.getdemocracy.com/news/2006/10/democracy-player-091-released/](http://www.getdemocracy.com/news/2006/10/democracy-player-091-released/)

---

### Post by j-strap2 on 2006-10-22
> **Coda said:**
> 0.9.0 doesn't support FLV videos, unfortunately. 0.9.1 does, but it's not available for Ubuntu yet.

[http://www.getdemocracy.com/news/2006/10/democracy-player-091-released/](http://www.getdemocracy.com/news/2006/10/democracy-player-091-released/)

0.9.1 is a significant improvement on 0.9.0 - there is no package yet but the   source tarball is very easy to run. I just had to install libxine-dev to get it to run.

---

### Post by findus on 2006-10-24
Thanks for the info guys,
Just been trying to install from the tarball but I am missing GKT+-2.0 amongst other dependencies that I can't seem to find on Synaptic.  I have the multiverse and universe enabled.  Any ideas?

Cheers,
Fin

---

### Post by Coda on 2006-10-25
The Ubuntu packages for 0.9.1 are available from their website now.

---

### Post by Coda on 2006-10-25
Well, it looks like the FLV problem isn't a Democracy bug:

[https://launchpad.net/distros/ubuntu/+source/xine-lib/+bug/66414](https://launchpad.net/distros/ubuntu/+source/xine-lib/+bug/66414)

[http://sourceforge.net/tracker/index.php?func=detail&aid=1578159&group_id=9655&atid=109655](http://sourceforge.net/tracker/index.php?func=detail&aid=1578159&group_id=9655&atid=109655)

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=357423](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=357423)

Crap.

---

### Post by Pixilarion on 2007-01-06
Seems it has been fixed in the CVS version of Xine. Hence, it should be fixed in the next release...
Hopefully Ubuntu will integrate this new version ASAP :rolleyes: 

Just hang in there: help is coming (I hope)...

---

### Post by gh0st on 2007-01-06
I seem to have the same problem with Democracy TV. I have the Flash 9 beta installed and it works great in the browser on YouTube, I've never found a video it can't play in Firefox (famous last words :-)) is this just a bug in Democracy TV then?

---

### Post by Pixilarion on 2007-01-06
> **gh0st said:**
> is this just a bug in Democracy TV then?

Nope, It's just that Firefox doesn't use Xine as a backend to play these videofiles. I guess it uses MPlayer which is already fully capable of playing flv WITH sound.
It is a problem of all programs using Xine as a video backend (like DM TV does). So it isn't even in the hands of the developers of DM TV to repair this. One solution could be that DM TV changes to another backend, but for some reason they don't...

---

### Post by gh0st on 2007-01-06
> **Pixilarion said:**
> Nope, It's just that Firefox doesn't use Xine as a backend to play these videofiles. I guess it uses MPlayer which is already fully capable of playing flv WITH sound.
It is a problem of all programs using Xine as a video backend (like DM TV does). So it isn't even in the hands of the developers of DM TV to repair this. One solution could be that DM TV changes to another backend, but for some reason they don't...

Right, I get you now. So it's really a core thing in all apps that use Xine or the Xine engine anyway. Maybe they'll move DM TV to mplayer or gsteamer eventually if the problem doesn't get fixed. Just a matter of waiting for a fix then I suppose :rolleyes: 

Thanks for the info

---

### Post by Pixilarion on 2007-01-07
Actually, there using VLC already as a backend on WIndows and MacOSX, so I don't get it  why they actually use xine on Linux. So I'm puzzled...
So just like I said: hang in there ;)

---

### Post by motang on 2007-01-08
> **Pixilarion said:**
> Seems it has been fixed in the CVS version of Xine. Hence, it should be fixed in the next release...
Hopefully Ubuntu will integrate this new version ASAP :rolleyes: 

Just hang in there: help is coming (I hope)...

Can't wait, hopefully it would be updated soon, so that I can enjoy Democracy TV.  It's a cool piece of software, just no sound right now.  Thanks for the info

---


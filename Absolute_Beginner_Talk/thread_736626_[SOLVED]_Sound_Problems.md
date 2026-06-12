---
title: "[SOLVED] Sound Problems"
date: 2008-03-26
forum: Absolute Beginner Talk
---

### Post by mrshmizzie on 2008-03-26
OK, so I have trying to fix the damn sound on my aspire 7520, but to no avail. Here is what I've done so far:

I've downloaded drivers from Realtek's website. Attempted to install, but ended up not being able to even start ubuntu. I've written the following post regarding that.

[http://ubuntuforums.org/showthread.php?p=4558628](http://ubuntuforums.org/showthread.php?p=4558628)

I decided to do a clean install of ubuntu and attempt to install the drivers again. I used the following post to attempt to install again. It's about half way down posted by panosg77.

[http://ubuntuforums.org/showthread.php?t=545401](http://ubuntuforums.org/showthread.php?t=545401)

Now after installing these drivers I now have the sound icon with a X over it. When I double click it I get the following error:

No volume control GStreamer plugins and/or devices found.

The sound does work in vista. Please someone help!!!!

---

### Post by spiderbatdad on 2008-03-26
This is your first Ubuntu install? Give Hardy beta a try. It's the latest pre-release of Hardy Heron the Long Term Support release of Ubuntu due out in April.

[http://www.ubuntu.com/testing/hardy/beta](http://www.ubuntu.com/testing/hardy/beta)

---

### Post by mrshmizzie on 2008-03-26
Ok fixed my problem myself. I'll post just in case anyone else has the same problem.

I installed the drivers from the following site.

[ftp://202.65.194.211/pc/audio/realtek-linux-audiopack-4.06a.tar.bz2](ftp://202.65.194.211/pc/audio/realtek-linux-audiopack-4.06a.tar.bz2)

Once I installed I restarted. After I restarted I used synaptic to install backport. Search backport and install the one named linux-backports-modules. After install restart once more and you should have sound.

---

### Post by mrshmizzie on 2008-03-26
Oh yea...have to give thanks to those who helped even though they probably don't know. I used this website to find the backport solution, 

[http://www.blog.hemminga.net/index.php/tutorials/?title=ubuntu-on-acer-aspire-7520](http://www.blog.hemminga.net/index.php/tutorials/?title=ubuntu-on-acer-aspire-7520)

---


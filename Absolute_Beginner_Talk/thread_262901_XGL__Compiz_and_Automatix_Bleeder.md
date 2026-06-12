---
title: "XGL / Compiz and Automatix Bleeder"
date: 2006-09-22
forum: Absolute Beginner Talk
---

### Post by MarkSparks on 2006-09-22
I spent all night last night trying to do things the hard way, now I'm ready to get XGL / Compiz installed the easy way. 

I hear the Automatix Bleeder is the way to go for this installation, but for the life of me I can't find installation instructions. The only thing I could find was this :

[http://ubuntuforums.org/showthread.php?t=225967](http://ubuntuforums.org/showthread.php?t=225967)

But I was getting the same problems that the guys listed, but then again, I'm foolish enough to try to use the amd64 version. 

Tonight I'm going to fixmbr from my ARC and start again, anyone have suggestions on how to get this going so I can start messing around with XGL / Compiz? I'm geeking to get that spinny cube desktop thing a whir. 

Oh, to add to this all, I made sure that I updated the Nvdia driver and that in the [Devices] section it was Nvidia and not nv. I could do the glxgears and it showed fine. The only weirdness that I ran into is that I had to re-run my xconfig so I could get 1900x1200 enabled on my Dell 2405fpw. Seems there is no native support for it in Ubuntu. 

Any help would be appreciated. Thanks!

mark.

---

### Post by Brunellus on 2006-09-22
you need to install the nvidia binary drivers-- 'nvidia' rather than 'nv.'  They are 'native,' but closed-source and thus not part of the default ubuntu setup.

---

### Post by MarkSparks on 2006-09-22
I did install them. That was the first step I did in fact. I made sure that the [Devices] stated Nvidia, NOT nv.. I know nv listed drivers are the default ones without acceleration. 

Once I re-ran the x configurator, I told it not to autodetect the driver and made sure I kept the Nvidia driver in there instead of nv.

---

### Post by MarkSparks on 2006-09-22
Anyone have any thoughts on this?

---


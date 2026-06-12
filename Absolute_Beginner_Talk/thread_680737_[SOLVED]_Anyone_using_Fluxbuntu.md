---
title: "[SOLVED] Anyone using Fluxbuntu ?"
date: 2008-01-28
forum: Absolute Beginner Talk
---

### Post by WorldTripping on 2008-01-28
I've just moved over to Fluxbuntu from 7.10, and have a couple of what I think are straightforward Q's.

1. How can I make Fluxbuntu automount USB sticks ? They are all labelled, and I want them to mount when plugged in.

2. How can I get a blank CDR to mount ?

3. What is the command line to write an ISO to a blank CDR ? I've installed cdrecord, but can seem to get it to write an ISO image.

4. How do I unpack a *.tar.gz ?

5. How do I install a *.deb ? I have used "sudo dpkg -i *.deb", and it fails with a "not a debian format archive" error. I know this is untrue as I have had this app running in Ubuntu 7.10

6. Any ideas why conky now has a ']' at the end of each line. (Conky example below.)

> ${color 87CEEB}CPU ${hr 2}$color
${execi 1000 cat /proc/cpuinfo | grep 'model name' | sed -e 's/model name.*: //'}
${freq}MHz   Load: ${loadavg}   Temp: ${acpitemp}
CPU Bar:  $cpubar
Load Bar: ${cpugraph FFFFFF ffffff}

Any help would be appreciated.

Cheers.

---

### Post by espressopigeon on 2008-01-28
Here's answer to Q4:

```
tar -xzf *file.tar.gz*
```

But that's all I've got. :(

---

### Post by WorldTripping on 2008-01-28
Thanks for that.

Took me a moment or two to figure out that you can't extract to a different directory to the one that you are in.

But I got there, and now I have working fluxbox pixmaps.

Cheers.

---

### Post by corney91 on 2008-01-28
Could you post a screenshot of conky? It shouldn't show any ] according to your .conkyrc sample.
Oh and maybe the whole .conkyrc?

---

### Post by WorldTripping on 2008-01-28
Sorry for the slight delay, but I had to find out how to [_take a screenshot using the command line_]("http://tips.webdesign10.com/how-to-take-a-screenshot-on-ubuntu-linux")

I've been using conky for some time now, and I can not see anything wrong with the conky file.

Cheers.

---

### Post by eriqjaffe on 2008-01-28
> **WorldTripping said:**
> 1. How can I make Fluxbuntu automount USB sticks ? They are all labelled, and I want them to mount when plugged in.I use ivman to handle that in my Fluxbox install.

[http://ivman.sourceforge.net/](http://ivman.sourceforge.net/)

---

### Post by WorldTripping on 2008-01-28
OK.

So I got ivman running.

USB's are now mounting to /media

Any idea if it can put a link on the desktop like Ubuntu does ?

Cheers.

---

### Post by corney91 on 2008-01-28
> **WorldTripping said:**
> Sorry for the slight delay, but I had to find out how to [_take a screenshot using the command line_]("http://tips.webdesign10.com/how-to-take-a-screenshot-on-ubuntu-linux")

I've been using conky for some time now, and I can not see anything wrong with the conky file.

Cheers.
That's weird - I can't see anything wrong with your .conkyrc. What version of conky are you using?
You could give reinstalling it a shot...

---

### Post by WorldTripping on 2008-01-28
conky -version tells me that it's:

'Conky 1.4.5 for Linux 2.6.15.7'

Seeing as I'm running 2.6.22.14 I think you might be right

{off to look for a newer Conky}

Thanks for the pointer.

---

### Post by corney91 on 2008-01-28
The latest one is 1.4.9 - I think it's in the repos. It may have been a bug in the old conky but I don't remember it...

---

### Post by Jerry N on 2008-01-28
I never did get Fluxbuntu to load (several weeks ago) and there were others on the forum having the same problem.  I have had a lot better luck with LinuxMint Fluxbox (Ubuntu 7.10 based).  

Jerry

---

### Post by WorldTripping on 2008-01-28
I've got it loaded and running, and it's lightening quick.

I've got all the apps I need running, Seahorse, acidRip, rhythmBox mPlayer etc etc..

I've just got a few issues to resolve before I can say that I'm totally happy with it.

The automounting was bothering me, but it was work-roundable.

Not being able (not knowing how) to mount and burn a CDR is a bit more of an issue.

corney91, thanks for that, I'll grab it when I get a spare moment.

Jerry, I'm liking the look of LinuxMint, I'll have a download tomorrow.

Thanks people.

---

### Post by eriqjaffe on 2008-01-28
> **WorldTripping said:**
> OK.

So I got ivman running.

USB's are now mounting to /media

Any idea if it can put a link on the desktop like Ubuntu does ?

Cheers.I don't think it can be done automatically, but you could always make a perma-link on the desktop to either the individual USB device or (more reasonably) the entire /media directory.

[http://wiki.fluxbuntu.org/index.php?title=Rox#Desktop_icons](http://wiki.fluxbuntu.org/index.php?title=Rox#Desktop_icons)

I don't use Rox, personally, but I don't see why that wouldn't work.

---

### Post by WorldTripping on 2008-01-29
OK,

So I got everything resolved.

I ditched Fluxbuntu and loaded LinuxMint Fluxbox.

Everything works as I expect it to, but it is a tad less responsive.

Ah well.

Thanks to everyone who helped.

Cheers.

---


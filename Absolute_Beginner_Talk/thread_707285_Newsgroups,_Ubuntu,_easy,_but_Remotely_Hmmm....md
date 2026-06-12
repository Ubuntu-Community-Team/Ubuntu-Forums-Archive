---
title: "Newsgroups, Ubuntu, easy, but Remotely? Hmmm..."
date: 2008-02-25
forum: Absolute Beginner Talk
---

### Post by firebee on 2008-02-25
**Hi folks**,

there is probably a better section for this, but I am a n00b here so my post will go here!

And yeah, I have read the other posts that relate to this, but can't seem to find the answer I'm looking for.

So here goes...

I just got myself a seedbox (dedicated remote server) for *ahem* sharing stuff, and have managed to get LAMP sorted OK, and torrentflux up and running within an hour or so, not bard for a first timer I thought!

So anyway, I regularly use newsgroups for getting my releases from, on my PC and Mac, but I want to know how to do this on my remote Ubuntu server.

[tangent]* I tried to install x-window, and it installed OK but I can't seem to get it to actually start, probably because when I enter terminal, it goes into the root folder, not into the overarching folder where x-window is installed, so commands don't work.*[tangent over]

**So** do I need to get the GUI working (if so, help!) to get any kind of newsgroup action happening or can it be done (easily) through terminal?

**Also**, what programme should I use for this, it is not for reading posts, it is simply for downloading large amounts of data as rar files (btw, I'll also need to be able to verify these files using par).

So maybe, if any of you are feeling generous, you could give me a hand?

The spec for the server is;

**Software**
L=Ubuntu 6.0.6.1
A= Apache 2
M= MySQL 5.0
P= PHP5

**Hardware**
AMD Athlon&#8482; 2000+
1024MB DDR-RAM
1x80+GB 7.2K RPM IDE-HDD
1x40+GB 7.2K RPM IDE-HDD

Hope you can help,

*a struggling(ish) n00b*

---

### Post by northern lights on 2008-02-25
There is a command line parity checker, it's called "par2repair". You can download it [here]("http://linux.softpedia.com/get/Desktop-Environment/Tools/par2repair-22969.shtml"), there also is a  [guide]("http://linux.com.hk/penguin/man/1/par2repair.html") on syntax.

As a newsreader, I'd try KLibido. Still, here's a [list of usenet clients with .nzb support]("http://docs.newzbin.com/index.php/Newzbin:NZB_Guide")

---

### Post by Cappy on 2008-02-25
hellanzb is what you want.
```
sudo apt-get install hellanzb
```

Then edit /etc/hellanzb.conf to your liking

You put a nzb in the specified folder and hellanzb will detect it, download it, par it, and unrar/reassemble it where you want.

It's simply awesome .. I use it on my desktop

---

### Post by firebee on 2008-02-27
Well that sounds exactly what I need, thanks for your help and responses, I'll edit this post when I've had a chance to try it out and see it working in action.

Thanks in advance!

---


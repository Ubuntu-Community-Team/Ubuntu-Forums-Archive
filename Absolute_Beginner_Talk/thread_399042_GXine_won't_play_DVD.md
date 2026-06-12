---
title: "GXine won't play DVD"
date: 2007-04-01
forum: Absolute Beginner Talk
---

### Post by SHilke on 2007-04-01
I need some serious help.  Get out your big crayons and get ready to spell things out Romper Room style.  I have an old Compaq Presario 1400, 566 MHz, with 320 meg of RAM.  I loaded Xubunto Edgy into it a few weeks ago with the intent of using this computer as a media player.  So far I've been trying to get GXine (came with the Xubuntu) to work playing DVD's.  It seems any DVD put out by a big studio (Disney, MGM, etc) won't play.  I've been trying to figure it out, dowloaded the Win32 codecs, the RealPlayer codecs, the CSS files, with absolutely no positive results.  I've removed and reinstalled GXine using Synaptic.  This really is a pain and very frustrating.  Will someone give me a single definitive answer as to the real way to download and configure Xine to work??!!  I have read about 50 forums about how to get Xine and Mplayer to work with these DVDs, and each one has a different way of doing it (and none of them work!).  

Here's what happens when I try to play a DVD.  The FBI message and usually the studio logo will play fine, including any music that might accompany it, but then I either get a Xine Engine Error that freezes up the machine (and I can't read the error because it freezes before the window finishes popping up), or I have been able to get a NAV error message.  Either way, the DVD does not play.

HELP!!  and thanks!

---

### Post by Perfect Storm on 2007-04-01
You have been on: [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats) ?
Another option is to use VLC (my favorite).

---

### Post by SHilke on 2007-04-01
I've been there and did what they suggested.  All it did was take up time.  I've tried MPlayer, with all the differing instruction that it comes with.  What will work with VLC?  Tell me exactly what you did to get it to work, step by step, as if I have no idea as to what I'm doing (oh, wait, I don't...)

---

### Post by Perfect Storm on 2007-04-01
Most things I throw at VLC it handles.
```
sudo aptitude install vlc libvlc0 libvcdinfo0
```
(requires universe enable in your repo.)

---

### Post by Maestro23 on 2007-04-01
Yep, VLC is a tough little guy.:guitar:

---

### Post by trent dillman on 2007-04-01
...

---

### Post by SHilke on 2007-04-02
Well, I tried the apt-get solution, no luck.  I tried to update my Synaptic Manager, but it won't accept two of the repositories.  Of course, those seem to be the two that I need to get VLC.  I went to the VideoLan site and tried to get it there, with the same problem.  I'm open to any other suggestions or fixes for Xine.

---

### Post by airtonix on 2007-04-02
forget xine get VLC.....

tell us what went wrong with setting up the repositories...

we are here to help

post your teminal results of :

> cat /etc/apt/sources.list

and to see waht errors are being pushed from the apt-get : 

> sudo apt-get update

---

### Post by SHilke on 2007-04-02
When I sudo apt-get updates, this is what I get as far as the repositories go:

Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/restricted Packages
  Sub-process gzip returned an error code (1)
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Packages [4655kB]
99% [6 Packages gzip 0]            
gzip: stdin: not in gzip format
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Packages
  Sub-process gzip returned an error code (1)
Fetched 6B in 3s (2B/s)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy/restricted/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy/universe/binary-i386/Packages.gz)  Sub-process gzip returned an error code (1)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

any ideas?

I wasn't able to find (or use) the cat/etc/apt/sources.list

as I said earlier, spell things out real simple, I'm a fast learner, but some of this is still really puzzling....

---

### Post by trent dillman on 2007-04-06
...

---


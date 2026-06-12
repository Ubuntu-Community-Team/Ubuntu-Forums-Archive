---
title: "Error with MPlayer"
date: 2006-12-19
forum: Absolute Beginner Talk
---

### Post by jefrat72 on 2006-12-19
I've tried to install mplayer from Synaptic and command line, I get this error:


W: Failed to fetch [http://3v1n0.tuxfamily.org/pool/dapper/3v1n0/mplayer_0.99+1.0-pre8-0ubuntu4_i386.deb](http://3v1n0.tuxfamily.org/pool/dapper/3v1n0/mplayer_0.99+1.0-pre8-0ubuntu4_i386.deb)
  302 Moved Temporarily


Any clue as to when it'll be back up or how else to install it?

---

### Post by Bachstelze on 2006-12-19
What's wrong with the mplayer from the repos ? I personnally use Xine but I think the mplayer from the repos works fine.

---

### Post by jefrat72 on 2006-12-19
> **HymnToLife said:**
> What's wrong with the mplayer from the repos ? I personnally use Xine but I think the mplayer from the repos works fine.

That's what I'm asking, I can't get it to install.

---

### Post by ajgreeny on 2006-12-19
There is a version of mplayer in the multiverse repos which I know works well (I use it often).  Disable temporarily at least the tuxfamily repos, make sure you have the universe and multiverse repos available and try again.  I think that should do the trick.

---

### Post by jefrat72 on 2006-12-20
Ok, got mplayer installed and working.  I also went here and downloaded the codecs:

[http://www4.mplayerhq.hu/homepage/design7/dload.html](http://www4.mplayerhq.hu/homepage/design7/dload.html)

However if I go to CNN.com I get the message saying it needs a plugin, Media Player 9 or above.  Does mplayer not cover Media Player, or did I not get the proper codecs?   I have this in /usr/lib/win32:

 wmv8ds32.ax
 wmv9dmod.dll
wmvadvd.dll
 wmvdmod.dll
i wmvds32.ax

Any help?

---


---
title: "can play SOME dvds..."
date: 2005-11-16
forum: Absolute Beginner Talk
---

### Post by linewb on 2005-11-16
After much trial and error I've managed to succesfully install libdvdcss2 and w32 codecs.  (Thank you, Frodon.)  The package manager clearly says they're both installed.  Still, I can only play some DVDs.  They are all from the same region (1), so that can't be the problem.  I've searched this site and not come up with a solution to this.  I'm running Hoary (5.04) on an AMD Athlon 1600+.  The dvd drive is LITEON DVD-ROM LTD 1630.  Any solutions out there?

---

### Post by poofyhairguy on 2005-11-16
[QUOTE=linewb]After much trial and error I've managed to succesfully install libdvdcss2 and w32 codecs.  (Thank you, Frodon.)  The package manager clearly says they're both installed.  Still, I can only play some DVDs.  They are all from the same region (1), so that can't be the problem.  I've searched this site and not come up with a solution to this.  I'm running Hoary (5.04) on an AMD Athlon 1600+.  The dvd drive is LITEON DVD-ROM LTD 1630.  Any solutions out there?[/QUOTE]

What program do you use? 

For DVDs I like Gxine best, but totem-xine and vlc are good too. To get them all, use this command in terminal:

> sudo apt-get install gxine totem-xine vlc

---

### Post by linewb on 2005-11-16
Thanks.  I have xine and vlc both.  The both will play certain dvds and not others.  Like I said I know I have libdvdcss2 and w32 installed.  Could it be it needs some other codes I'm not aware of?  Could it be the hardware won't play certain DVDs?  The DVD-ROM is described above.  Many thanks to anyone who can help.

---


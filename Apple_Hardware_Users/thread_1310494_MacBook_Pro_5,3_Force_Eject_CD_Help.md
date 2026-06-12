---
title: "MacBook Pro 5,3 Force Eject CD Help"
date: 2009-11-01
forum: Apple Hardware Users
---

### Post by brucem91 on 2009-11-01
Hello. I need some help. I was burning Karmic x64 iso to a cd, when I accidentally told Disc Utility in OS X to quit. Now OS X nor Ubuntu Karmic Koala(32bit) recognize the CD at all. I am unable to eject the CD. Does anyone know how to force eject a cd, either in OS X (Snow Leopard) or Ubuntu 9.10? Here is what I have tried so far

Eject Key in OS X
Eject Key in Ubuntu
OS X - terminal "cd eject"
OS X -terminal "drutil tray eject"
Reboot and hold mouse button
Reboot and hold eject button


Thanks

Bruce

EDIT: Yay, I got the cd out. I shut down my mac for a little while, then turned it back on. I pressed down with my hand just over where the cd drive is, and then hit eject. It worked perfectly for me, now I put a new cd in and I am burning ubuntu 9.10 x64 now. Woot!

---

### Post by visitile on 2010-06-03
Wow, you're not kidding.  I tried everything under the sun no matter how silly.

I Tried Terminal using   ```
$ drutil list
```
 - causes the stuck WIN7 DVD disk to mount... spins up and then I see it Finder as WIN_7_HOMEPREMIUM my sidebar
 - keyboard eject button didn't work... it just vaporized from Finder

So I hit ```
$ drutil list
``` again, Tried the software eject button in Finder.. FAIL

So I hit ```
$ drutil list
``` one more time, this time, I clicked the Software eject button while generally pounding and causing as much ruckus as I could stomach on the area above the optical drive and BOOM out slides the disk.

I guess these old Macbook Pro1,1's just need a good spanking when they start to get too cozy with the windows paraphernalia.

---


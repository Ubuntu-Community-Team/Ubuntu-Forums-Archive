---
title: "debootrap warning: file xyz is corrupted"
date: 2007-05-29
forum: Absolute Beginner Talk
---

### Post by blahmeister on 2007-05-29
Hi folks,

I'm tryin to install xubuntu feisty fron the alternate cd. Problem is i keep getting the "debootstrap warning ... file blah.debu is corrupted".

Now, i no it's not corrupted, cos i d'led it from bittorrent (which iirc does a piecewise checksum as it goes), i burned it real slow, and did a verify after.

I know the drive isnt broken, because i did a whole xp install to test it while i was waiting for bittorrent.

Soooo, i figure it MUST be something wrong with my pcmcia bus. Any ideas of boot options i could use to clean it up?

Any help would be greatly appreciated as i need this laptop for the trip i'm leaving on in 13 hrs...

Cheers,
B.

---

### Post by dpont on 2007-12-13
Im having this same problem. Ive tried both ubuntu server alternative Cd, and xubuntu alternative CD now. I checked the md5 of the file that it says is corrupt, and the md5's match, so i know its not a burning problem (i also did a disk check, and it reported no problems).  Any ideas what could cause this ?

---

### Post by dpont on 2007-12-13
It turns out my problem wasnt the CD at all. I had tried to partition with windows paritioner first, and that must have caused a problem.  When i repartitioned my HDD, it worked fine.

---


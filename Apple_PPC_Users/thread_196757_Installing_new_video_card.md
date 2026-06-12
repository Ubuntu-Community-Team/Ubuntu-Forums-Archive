---
title: "Installing new video card"
date: 2006-06-14
forum: Apple PPC Users
---

### Post by hawkbane on 2006-06-14
I have a blue G4 with the standard video card that came with it.  I would like to upgrade to a 128 MB, but do not wish to pay more than I have too.  With Linux running on the PPC, do I still have to get a Mac specific video card or can I get a PC one and the Linux drivers would recognize and use it?  Any ideas?

Thanx!

---

### Post by taurus on 2006-06-14
After upgrading your graphic card, you probably need to reconfigure your X again by running this from a terminal...
```

sudo dpkg-reconfigure xserver-xorg

```

---

### Post by hawkbane on 2006-06-14
Thanx for the post, but I am not talking about getting the graphics to  work in X ... I am more talking if the OS will physically interface with a non-Mac compatible graphics card in the slot.  It is more of a hardware compatibility issue than an OS ... really.  I am asking if anyone knows if the linux drivers in the OS would bridge the hardware differences.

Thanx again guys!

---

### Post by imacQ on 2006-06-18
there is something about "flashing" pc video cards and the rom in order to work with mac. see here: [http://strangedogs.proboards40.com/index.cgi](http://strangedogs.proboards40.com/index.cgi)  
i haven't done it so that's all i can tell you. good luck.

---


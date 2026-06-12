---
title: "is there anything like screenvideo?"
date: 2007-03-21
forum: Absolute Beginner Talk
---

### Post by da1nonlymikeo on 2007-03-21
just like take a screen shot featured in ubuntu, is there anything that would take a video of your desktop??

---

### Post by cowlip on 2007-03-21
[http://liquidat.wordpress.com/2007/03/13/desktop-recording-on-fedora-core-6/](http://liquidat.wordpress.com/2007/03/13/desktop-recording-on-fedora-core-6/)

It's for Fedora but I'm sure some of these apps are for Ubuntu too

---

### Post by Aliarse on 2007-03-21
[http://xvidcap.sourceforge.net/](http://xvidcap.sourceforge.net/)

Does screen shots and video, and has lots of options for you to play around with. :)

---

### Post by da1nonlymikeo on 2007-03-21
thanks guys! I'll check these out and see what happens:)

---

### Post by da1nonlymikeo on 2007-03-21
how in the hel are you supposed to install that xvid cap? haha is there anything a bit more simple like a sudo apt-get install "desktop recorder thing?"

---

### Post by cowlip on 2007-03-21
Add asher256's repository, they have it: [http://asher256-repository.tuxfamily.org/index.php?page=faq&lang=en](http://asher256-repository.tuxfamily.org/index.php?page=faq&lang=en)

---

### Post by da1nonlymikeo on 2007-03-21
after i add that to my sources list. what do i look for?

---

### Post by cowlip on 2007-03-21
you can look in either Synaptic for "Xvidcap" or whatever packages you want.  or maybe the add/remove programs (I don't know if it'll show up there).  

The list of packages is here: [http://asher256-repository.tuxfamily.org/index.php?page=packages&lang=en](http://asher256-repository.tuxfamily.org/index.php?page=packages&lang=en)

Or you can do "sudo apt-get install xvidcap" or whatever recording program you want..

---

### Post by da1nonlymikeo on 2007-03-21
eh cant seem to find xvidcap..

---

### Post by cowlip on 2007-03-21
Ok I guess he removed it sadly; i was going by this package list, but you're right it doesn't seem to be in the main package list anymore: [http://asher256-repository.tuxfamily.org/ChangeLog](http://asher256-repository.tuxfamily.org/ChangeLog)

[http://downloads.sourceforge.net/xvidcap/xvidcap_1.1.5rc1_i386.deb?modtime=1170981826&big_mirror=0](http://downloads.sourceforge.net/xvidcap/xvidcap_1.1.5rc1_i386.deb?modtime=1170981826&big_mirror=0)  

Did you try this .deb file?  You just have to double click it to install..

Iarwain [below me]: you're right..last update for it was June 2006 from that changelog.  I wonder why it's gone now?

---

### Post by Iarwain ben-adar on 2007-03-21
hiya cowlip,

Just to inform you,
xvidcap is not in asher256's repo.


Iarwain

---

### Post by ppatalano on 2007-03-21
How about Istanbul for capturing screencasts....

---

### Post by da1nonlymikeo on 2007-03-21
ah that worked. but i dont know how to use this? it looks a little confusing. after i record, where dose it save the video file to so i can view it?

---

### Post by cowlip on 2007-03-21
I'm not using Ubuntu right now so I hope someone else can step in here :)  Just a completely wild guess and I'm pretty sure it's wrong, but you could check ~/.xvidcap to see if it records anything there.

---


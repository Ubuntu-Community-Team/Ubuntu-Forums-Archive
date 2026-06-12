---
title: "Can someone explain the magic that is LVM?"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by jaw1959 on 2007-06-13
I'm trying to figure out how to combine 2 physical hard drives in my machine so they act like 1 large hard drive.  I had a setup like this going before, but it was setup by a guru friend of mine.  Can anyone point me in the direction of a decent how-to, or decent documentation on LVM?

---

### Post by ncappel1 on 2007-06-14
I had this set up when I first installed ubuntu. I had two hard drives, and at install what I did was just set up the extra one as one huge ext3 partition. I then added the drive to automount at start up, and it shows up as an extra drive on the desktop which I can go into and play around in.

---

### Post by phr0ze on 2007-06-14
Of course you could just mount the drive to a location like \home\extra. But LVM is different. I also find it to be risky. I found wikipedia has some decent links in it for LVM resources. Is there a particular reason you want an LVM setup?

---

### Post by jaw1959 on 2007-06-16
I just want to have the 60GB, 120GB, and the remaining 20GB of my 40GB drive (that my OS is installed on) to be used as one drive to store media.  I use this machine as a Twonkymedia server, and IMO, it's easier to organize things in a directory structure that is similar to the menu structure I will use on the D-LINK DSM 520 I will be streaming to.  I realize this isn't absolutely necessary, and I realize that the zillions of linux users out there would all do it differently, but this is how I'd like to do it (and isn't that what using Linux is all about?).  I had a similar setup before, and it worked well, but the upgrade from Edgy to Feisty wasn't without it's complications (it worked, but the edgy install was my first ubuntu install ever, and I made plenty of mistakes, so I wanted to make sure I was working from a clean slate), so I decided to start over from scratch (I also removed the windows partition I had on the machine).  

I have a new question now.  I found some decent documentation for LVM (via wikipedia), and it seemed like I had the setup I wanted, but it didn't work when it rebooted (it seemed to work fine BEFORE I rebooted).  I did all the vgcreate vecreate, and yadda yadda yadda.   I assume there is something I have to do to make recognize the LVM  setup at startup that I missed in my documentation.  


I'm not married to LVM to make this work, but it seems like the only way to do what I want with the hardware I have.  I'm just storing movies and music on this machine (and I have a backup on an external hd).  If it fails and I lose my movies, It's not going kill me, I still have the originals as well.  I'm not worried about absolute security, and from my experience the last several months running with a similar setup, it will work just fine for my needs, that is as long as I can get the initial setup right.

Any help or advice would be appreciated

Josh

---


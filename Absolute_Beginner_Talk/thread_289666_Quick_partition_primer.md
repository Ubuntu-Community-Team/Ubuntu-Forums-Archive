---
title: "Quick partition primer"
date: 2006-10-31
forum: Absolute Beginner Talk
---

### Post by other guy on 2006-10-31
I am about to partition out an 80 gig drive. This will be a non-dual boot machine and standalone. I will later on, be using a second drive for all my media and general storage.

I am rather stuck right now about the strategy of how to break up the single drive for an install. Soon as I got the basic idea, Ubuntu will go in.

I am comfortable using gparted, to a reasonable degree. I am just stuck figuring out what would be a good start. Then later on *if need be* reconfigure the partitions. A quick primer to get started is about all I need for a good start. I can get the rest as I use the machine and taylor it for my needs.


Was I close in my guess of a good layout? Any other partitions I should have or would benifit the performance?

/swap 1 gig (primary)
/root 10 gig (primary)
/usr remaining space (primary)

Thank you

---

### Post by daou on 2006-10-31
You probably don't want to give so much space for /usr. /home is where all your personal stuff is stored, and I would suggest you give this as much space as you can. I recommend you give maybe 15GB for /root, keep swap as it is, and the rest to /home. Meaning no additional partition for /usr.

---

### Post by other guy on 2006-10-31
Just to make sure I got this.. I think. ;)

/swap 1 gig (primary)
/root 15 gig (primary)
/usr 15 gigs (primary)
/home remaining space (primary)

---

### Post by ReaderRat on 2006-10-31
Usually, all I do is partition the / and /swap, and let the installer configure the rest. If you want, con figure a /home partition, instead of /usr. If you are comfortable with gparted, you can get the most up-to-date copy here:
[**Gnome PARTition EDitor = gparted**](http://gparted.sourceforge.net/index.php)

---

### Post by daou on 2006-10-31
No extra partition for /usr. This is mostly for applications and Linux applications have the unfortunate :rolleyes: property of being very small. Unlike their Win cousins that suck up a couple gigs of hdd space.

---

### Post by other guy on 2006-10-31
Got the idea now. I was thinking of a simple / & /swap, but in my readings. It showed a number of partition options. The install I was testing worked ok, it had only an / & /swap but was deleted whilst I made my mind up on removing the Redmond stuff.

Usually I read before making threads. Since each install is unique, I figured this would be best.

Your input put me on a happy path. Now I can get to doing  this.

I am on the latest offfering of 32bit LiveCD. So no installs until it is in. 

Thank you for the input. :cool:

---


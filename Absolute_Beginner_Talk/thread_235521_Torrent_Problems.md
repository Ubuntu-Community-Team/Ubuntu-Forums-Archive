---
title: "Torrent Problems"
date: 2006-08-13
forum: Absolute Beginner Talk
---

### Post by justinlb on 2006-08-13
I have had Ubuntu installed for a couple of months and for the past month or so I have been downloading torrents through Azureus or Bittotorrent without any problems, but in the last week, everytime I start or resume a torrent the program says it either times out or it can't connect to tracker. I didn't have this problem when I used to use Windows and as I said it is only a recent occurrence. I have installed and tried many different torrent managers since these problems started and there has been problems with them all. Any help would be appreciated.

---

### Post by Ziox on 2006-08-13
> **justinlb said:**
> I have had Ubuntu installed for a couple of months and for the past month or so I have been downloading torrents through Azureus or Bittotorrent without any problems, but in the last week, everytime I start or resume a torrent the program says it either times out or it can't connect to tracker. I didn't have this problem when I used to use Windows and as I said it is only a recent occurrence. I have installed and tried many different torrent managers since these problems started and there has been problems with them all. Any help would be appreciated.

your problem has nothing to do with your torrent clients or your computer.  As the warning says, the tracker is down.  I'm not sure where the tracker is located, but it isn't on your computer, so there isn't anyway to "solve" the problem.

You can either wait for the tracker to be back online (which could be never), or you can try a similar torrent file.

---

### Post by justinlb on 2006-08-13
I thought that might have been it so I tried many various torrents from various sites/sources and each time it came back with the same problem.

---

### Post by Ziox on 2006-08-13
> **justinlb said:**
> I thought that might have been it so I tried many various torrents from various sites/sources and each time it came back with the same problem.

I'm assuming that if most of the torrents are hosted by the same tracker and all of them are down, then perhaps the "server" is down? :confused: That's my assumption.  Have you tried downloading Ubuntu torrents, just to test your computer/torrent-client out?

[http://ubuntu-releases.cs.umn.edu//6.06/ubuntu-6.06.1-alternate-i386.iso.torrent](http://ubuntu-releases.cs.umn.edu//6.06/ubuntu-6.06.1-alternate-i386.iso.torrent)

---

### Post by EdThaSlayer on 2006-08-13
Maybe your internet service provider blocked the port that you were using to download the torrents...

---

### Post by justinlb on 2006-08-13
No luck again, the same problem happened with all 3 torrent managers I tried the Ubutnu iso with.

The one I'm using at the moment is Tribler and have got these two messages when I have tried to start the torrents.

"00:32 - Problem connecting to tracker - (-3 'Temporary failure in name resolution')"

"00:33 - Problem connecting to tracker - timeout exceeded"

---

### Post by Ziox on 2006-08-13
> **justinlb said:**
> No luck again, the same problem happened with all 3 torrent managers I tried the Ubutnu iso with.

The one I'm using at the moment is Tribler and have got these two messages when I have tried to start the torrents.

"00:32 - Problem connecting to tracker - (-3 'Temporary failure in name resolution')"

"00:33 - Problem connecting to tracker - timeout exceeded"

Are you using various ports for download? Trying using differents ports, especially ports that are really, really high (i use 48000+)

---

### Post by kinematic on 2006-08-13
using high ports would also be my advice.
i've setup bittornado to use a random port between 53000 and 55000 and i've never had any problems.

---

### Post by justinlb on 2006-08-13
I tried those exact settings in bittornado and it still came back with the problem.

"00:32 - Problem connecting to tracker - (-3 'Temporary failure in name Resolution')"

---


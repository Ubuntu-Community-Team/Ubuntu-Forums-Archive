---
title: "inconsistent download speeds with Azureus"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by Redbomber on 2007-06-07
I'm downloading at the moment and the download speed is mostly really slow.  But then It'll jump up to 100kb/s for 10 seconds and then back down to 800b/s.  Ports are forwarded in my router and in Firestarter, and test ok in Azureus.  A 300MB tv show with 1668 seeds and 630 peers shouldn't take almost 24 hours to download on my 1.5MB connection.  It takes me at the most 3 hours in Windows using Azureus.  Is there some settings I might be missing.  I have already played with a lot of them, but no difference.  Help would be appreciated.  Thanks.

---

### Post by Golyadkin on 2007-06-07
I have the same problem with Azureus, all NAT and DHT lights are green, forwarding works but randomly the speed drops entire to 0 for several minutes, and then picks up again at 900 kB/s to 1100 kB/s... in Windows the speed stays constantly at the 900 - 1100 range. I am on a little over 8 MBit/s connection.

---

### Post by coxy on 2007-06-07
Do you have any other torrents running? If you do, you need to open and forward a port for each download. They start at 6881 and move up in increments of one.

---

### Post by Redbomber on 2007-06-07
I have done that with Firestarter (as it defaults to that when you open ports).  I'll forward more ports on my router and let you know.

---

### Post by Alterax on 2007-06-07
Remember that the connection on your end may not be the bottleneck.  It could be a lack of resources or taxed connections on the other end of the download.  Or it could be your ISP.  Comcast for example is notorious for limiting bandwidth, even if they won't actually admit to it.

--Alterax

---

### Post by Redbomber on 2007-06-07
Yeah, open ports on my router has no effect.  Never had to do that before anyway.  I understand what you're saying about bottlenecking and bandwidth limiting.   I have been downloading torrents for 4 years and been with the same ISP for that long.  Never been a problem before.  Just as a matter of interest, I'll install Azureus on my Windows partition and check the speed.

---

### Post by RomeReactor on 2007-06-07
Hi. I've been using Azureus for all of 1 day (couldn't make it work on Edgy, crashed all the time); one thing I've noticed is that, to get better download speeds, you have to set up a balance of download and upload speeds. For example: I have 1024/128 DSL, or in other words, I download at 1024 **kilobits** (around 112 **kilobytes**), and upload at 128 kb (12 kB). My Azureus connection is setup at **95kB down/12 kB up**, and it seems to go fine, so you have to play with the speeds a bit (by right-clicking on the blue arrows--up and down--at the bottom right of Azureus). Also, by default, [Azureus uses only one port for both TCP and UDP]("http://azureuswiki.com/index.php/Port_forwarding"), so I don't think port forwarding is the issue here. From the wiki:
> Azureus listens to one port for torrents and another for the embedded tracker. Two protocols, TCP and UDP, use the same port, unless specified otherwise. Thus, you need to forward one listening port for Azureus and tick both the TCP and the UDP boxes, or make an extra rule, one for each protocol.

---

### Post by Redbomber on 2007-06-07
Well just another additional - I  followed the wiki guide here - [http://www.azureuswiki.com/index.php/NAT_problem#Port_Forwarding_on_Linux.2C_specifically_Ubuntu]("http://www.azureuswiki.com/index.php/NAT_problem#Port_Forwarding_on_Linux.2C_specifically_Ubuntu") again.  Right away my downloads rocketed up to decent speeds, but I noticed NO UPLOADS.  Then after a five or so minutes my downloads dropped down 0.  I used the port number 49125 for both TCP and UDP.  I'm not sure if they have to be different - I wouldn't think so.  Any ideas gentleman?

---

### Post by pappapump on 2007-06-07
Azureus is a bomb, it crashes for no real reason and just won't come up.
Then other times it works fine, but when its dead its real dead.
Thats why i gave up and went with Ktorrent.

---

### Post by Redbomber on 2007-06-07
Thanks Pappapump.  Working for me! :D   144kb/s is what I'd expect.

---


---
title: "dvd backup"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by KezzerDrix on 2008-01-20
In windows I used #1 dvd ripper, to rip dvd to xvid so I could put it on my media server.  These are dvd's that I own and I feel I have the right to watch them :)  I downloaded dvd::rip and acidrip but they just errored out.  I figured that they must not be able to rip copyrighted dvd's so the question is what do you use in the linux world and how do you use them.

Also what do you use to watch said dvd movies straight from the disk?

---

### Post by FuturePilot on 2008-01-20
Did you install libdvdcss2? Acidrip works fine here
For watching DVDs I use Totem. It works very good provided you ditch the gstreamer backend and use xine instead. VLC is also a good player.

---

### Post by JoshuaRL on 2008-01-20
Try K9Copy.  It's what [https://help.ubuntu.com/community/WindowsApplicationsEquivalents](https://help.ubuntu.com/community/WindowsApplicationsEquivalents)  suggests.

---

### Post by Dr Small on 2008-01-20
> **JoshuaRL said:**
> Try K9Copy.  It's what [https://help.ubuntu.com/community/WindowsApplicationsEquivalents](https://help.ubuntu.com/community/WindowsApplicationsEquivalents)  suggests.
+1
Try k9copy. It works perfectly every time for me ;)

---

### Post by KezzerDrix on 2008-01-20
I installed the ubuntu restricted extras from the repo.  It states that it will grant me dvd playback but dvd does not play.  I did a search for libdvdcss2 in the repo and came up with nothing.  I have all the repos checked.

---

### Post by FuturePilot on 2008-01-20
You need to add the Medibuntu repository. libdvdcss2 isn't in the Ubuntu repos for legal reasons.
[https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

---

### Post by rosegarden78 on 2008-01-20
Could be like a double-sided or double-density or high-speed disc.  You know like when using older laptops or when you rent scratched discs from the local library?  I think I had to mount the DVD drive from terminal in one case.  In another I had to use VLC media player.  Another time I used the Medibuntu repositories.  It's been ages since I watched a DVD!

---

### Post by Emerzen on 2008-01-20
libdvdcss2 is a requirement.  If you have trouble following FuturePilot's link, you could use [Automatix]("http://www.getautomatix.com/") to install it directly.  Once that's done, ensure that you have DVD playback...if you do, then you should be able to rip as well.  k9copy is good, DVD::rip is also a good tool.  My personal favorite is [Handbrake]("http://handbrake.fr/") though.  It's very fast and it's been flawless for me.  I rip my dvd's to PS3 compatible mp4 files (ffmpeg/faac.mp4) and I stream with Mediatomb.  My 2nd choice would be avidemux (in the repo's).  I've found Handbrake a little faster, but avidemux has a nice frontend.

---

### Post by KezzerDrix on 2008-01-20
do  any on these remove the region code, and the copyright protection like #1dvd ripper?  I am trying to put my movies on a media server.

---

### Post by Emerzen on 2008-01-21
I'm not certain, but I don't think Xvid stores region codes and copy protection will definately be gone.

---


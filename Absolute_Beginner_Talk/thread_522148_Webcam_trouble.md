---
title: "Webcam trouble"
date: 2007-08-10
forum: Absolute Beginner Talk
---

### Post by DaH-RaT on 2007-08-10
i'm almost there, i got my webcam working almost instantly after some settings configuration ( creative pro notebook cam)  with kopete. i got it working once, but after that i send my webcam to everyone and the connection does not shake hands, think its my router? the cameracan't webcam  works great! good quality but just  can't webcam chat. ( tried kopete, amsn )

---

### Post by Pragmatist on 2007-08-10
> **DaH-RaT said:**
> i'm almost there, i got my webcam working almost instantly after some settings configuration ( creative pro notebook cam)  with kopete. i got it working once, but after that i send my webcam to everyone and the connection does not shake hands, think its my router? the cameracan't webcam  works great! good quality but just  can't webcam chat. ( tried kopete, amsn )
Can you see their webcam?  The problem is likely the firewall.  This is a very common problem and it is easy to fix:  you configure your firewall and open some ports.
Unfortunately, neither of these seem too helpful:
[http://ubuntuforums.org/showthread.php?t=409143](http://ubuntuforums.org/showthread.php?t=409143)
[http://ubuntuforums.org/showthread.php?t=274620](http://ubuntuforums.org/showthread.php?t=274620)

I was just working on this myself just a couple of days ago, and I tried amsn, kopete, and, eventually, gyache.  I think gyache is MUCH better than the others.  You can download the .deb file here:
[http://gyachi.sourceforge.net/download.shtml](http://gyachi.sourceforge.net/download.shtml)
Then, if you install gdebi from the repositories (I use synaptic), you can type this in a terminal:
```
gdebi filename.deb
```

---

### Post by DaH-RaT on 2007-08-11
yes its definitely the firewall on the router and some ports, i fixed that after someone else helped me through the process, and still installed the deb packages for  that instead lol. If you use kopete youll have to have the recipient ask to view your cam isntead of sending it, it will msotly work that way.
thanks for those links too they did help in some areas where a question mark was placed :)

---

### Post by punong_bisyonaryo on 2007-08-11
Personally, I preferred Kopete for webchatting Yahoo users, but since it didn't support voice + webcam, I just convince people to use Wengo instead.

Here is a thread discussing webcam + chat + voice software in Linux [http://ubuntuforums.org/showthread.php?t=484398](http://ubuntuforums.org/showthread.php?t=484398)

---


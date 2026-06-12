---
title: "Shutdown doesn't"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by DaDave on 2007-03-30
My wife liked Xubuntu on my Mac so much that she wanted it on her PC. Like the Mac, everything installed without problem and seems to be running fine. However, the shutdown isn't working. Logoff is fine, but shutdown does not shutdown the computer, she has to do it herself. The desktop shutsdown, but the computer doesn't. Any suggestions? (not a dual boot maching).

Okay, this isn't a major problem, just a little inconvenient. We just want to make sure it isn't a symptom of a larger problem.

Thanks!!

---

### Post by dstew on 2007-03-30
What are the specifications of the computer?

---

### Post by wonton180 on 2007-04-02
I have the same problem on a older Dell GX1 desktop.  poweroff feature used to work fine on my older non-Ubuntu linux distro on this machine.  i'll post my systems spec and log details shortly.

---

### Post by FotiX on 2007-04-02
I had the exact same problem, but on Kubuntu.
We discussed it here:
[http://www.ubuntuforums.org/showthread.php?p=2392614#post2392614](http://www.ubuntuforums.org/showthread.php?p=2392614#post2392614)

---

### Post by The other One on 2007-04-04
I'm also having this problem since upgrading to Edgy on my x64 ATI machine. I'll try the driver reinstall in the link above and see how I go

---

### Post by confused57 on 2007-04-04
See if this might work:
[http://ubuntuforums.org/showpost.php?p=1714220&postcount=9](http://ubuntuforums.org/showpost.php?p=1714220&postcount=9)

---

### Post by dstew on 2007-04-06
Just to let you know, I installed Edgy on an HP XE3 laptop. It worked perfectly except it did not shut down. I added the apm power_off=1 to the /etc/modules file as mentioned in the previous post and that solved the problem.

---

### Post by DaDave on 2007-04-06
> **confused57 said:**
> See if this might work:
[http://ubuntuforums.org/showpost.php?p=1714220&postcount=9](http://ubuntuforums.org/showpost.php?p=1714220&postcount=9)

Yep. This solved the problem. The old PC shutsdown every time. THANKS!!

---

### Post by The other One on 2007-04-10
> **confused57 said:**
> See if this might work:
[http://ubuntuforums.org/showpost.php?p=1714220&postcount=9](http://ubuntuforums.org/showpost.php?p=1714220&postcount=9)

I tried this and thought it hadn't worked, but tried shutting down again tonight and noticed that the HDD LED was still flashing, so I waited a bit and bam! she shut down, \\:D/

---

### Post by spydon on 2008-01-02
Thx, I had this problem too and now it works perfect :).

---


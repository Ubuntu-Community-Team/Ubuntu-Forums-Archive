---
title: "Sometimes wireless drops out"
date: 2007-12-03
forum: Absolute Beginner Talk
---

### Post by systemintheglitch on 2007-12-03
It doesn't happen when im in windows.. But periodically the network connection drops out and has to reconnect.

---

### Post by bren on 2007-12-04
on my laptop strength of network detected in linux is not as good as in windows.... for example if i go far away in the house windows wireless is ok (but low signal strength) but linux loses the connection....

i heard that a new kernel version has big wireless upgrade and this will come down the hill to us in Ubuntu land in a while (maybe hardy heron)...

periodic drop out where signal strength is good sounds like maybe a different problem...

bren

---

### Post by dimbulb1024 on 2007-12-04
Personally, I've had this happen in both XP and Ubuntu.

---

### Post by drcranium on 2007-12-04
What wireless card do you have?  Are you using ndiswrapper or driver support from the kernel.  I know there are sometimes problems from just using the kernel for wireless support.

---

### Post by systemintheglitch on 2007-12-05
How hard is it to use ndiswrapper..

I have a weird problem where when I hibernate or sleep networking gets all messed up on resume.. Maybe ndiswrapper would be better..

Where can I get some more info?

---

### Post by bren on 2007-12-08
search for ACPI and your <your computer model name> and linux

---

### Post by kra007 on 2008-02-01
This is not only on wireless connections.
I see the same thing even if connected with a cable.
However I see a pattern here.
There are ~8 minutes of receiving data followed by ~2 min receiving nothing.
So there is a 10 minutes window.

I run XUbuntu 7.10 and I love it. The network-manager handles my wireless
connections for me just out of the box.

The problem I have is the connection is dropped for 2 min every 10 min while
doing update. (I have  0.250 MB connection with ADSL modem).

Now, this is strange. While the System-monitor shows the drop I can still surf with
Firefox. But update-manager doesn't seem to care. It waits for 2 min before it
continues receiving the missing packages.

I have other issues, but I may put them in a thread where it belongs.

---


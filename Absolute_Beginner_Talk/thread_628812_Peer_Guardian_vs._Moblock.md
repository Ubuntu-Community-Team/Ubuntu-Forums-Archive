---
title: "Peer Guardian vs. Moblock?"
date: 2007-12-01
forum: Absolute Beginner Talk
---

### Post by BassKozz on 2007-12-01
I use Peer Guardian for my XP machine, and I like how it works but while searching the forums for information on Peer Guardian in *buntu I came across this thread: [ Moblock (peerguardian linux alternative)](http://ubuntuforums.org/showthread.php?t=192559)

But which is better **Peer Guardian** vs. **Moblock**?

---

### Post by ekimregnirps on 2007-12-01
Hi, i have been down that road before. I suggest a superior alternative IMHO.....

   [http://ubuntu-utah.ubuntuforums.org/showthread.php?t=530183](http://ubuntu-utah.ubuntuforums.org/showthread.php?t=530183)


it uses the same sources to block IPs, but it can be configured with iptables, so you can have a firewall too!

---

### Post by BassKozz on 2007-12-01
Does this automatically update the lists once installed?
P.s. I am a newb, I downloaded the [package for Gusty from SourceForge](https://sourceforge.net/project/showfiles.php?group_id=198679) and installed the package is that it?

---

### Post by FuturePilot on 2007-12-01
> **B/-\ssKozz said:**
> Does this automatically update the lists once installed?
P.s. I am a newb, I downloaded the [package for Gusty from SourceForge](https://sourceforge.net/project/showfiles.php?group_id=198679) and installed the package is that it?

Yes, just click the Update button. It works almost exactly like Peer Guardian.

---

### Post by BassKozz on 2007-12-01
Thx, just installed it and was messing around (starting/updating/restarting/etc..) and now I get the following error message everytime I try and start it:> iptables: Chain already exists
What gives? Anyone know how to fix?

---

### Post by FuturePilot on 2007-12-01
Yeah, I got that once. A reboot should fix it. Just make sure that you manually run the update before Enabling it. That seems to be a glitch or something.

---

### Post by BassKozz on 2007-12-01
RE-Booted and enabled, and now the whole damn WAN is down...
I can't even "ping google.com"

Something isn't working right?

---

### Post by BassKozz on 2007-12-13
Why is IPBLOCK better then MoBlock?

---

### Post by jre on 2007-12-21
> **B/-\ssKozz said:**
> Why is IPBLOCK better then MoBlock?

MoBlock 0.8 either ACCEPTs packages or DROPs them, but it doesn´t sllow to process themwith following iptables rules. So it´s incompatible with most firewalls.
This will be changed in MoBlock 0.9

If something is boocked you have to whitelist it. For MoBlock: /etc/moblock/moblock.conf. For IPllist I don´t know.
greets
jre

---


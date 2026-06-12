---
title: "Driver help"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by Bofur on 2007-06-13
I'm trying to install a wireless driver, but am having trouble. I have an Intel Pro/Wireless 3945ABG card. I stumbled across this website [http://ipw3945.sourceforge.net/](http://ipw3945.sourceforge.net/) which I'm guessing gives me the drivers. Under requirements it tells me what I need but I'm kind of lost heres why:
I got both binarys from #1 and #2 downloaded, but when I try installing the ieee80211 subsystem it doesn't work.

I downloaded the newest .tar file, but I'm having trouble installing it here what it says when I try doing it as the instructions say:
```
root@ubuntu:/home/justin/Desktop/Drivers/ieee80211-1.2.17# tar xzvf ieee80211-1.0.1.tgz
tar: ieee80211-1.0.1.tgz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

```
For the 4th step I'm guessing since I have Fiesty Fawn that will suffice for the kernel part.
5th and 6th step no idea there.

If anyone could take the time to help me out I would REALLY appreciate it. Or, if someone knows a quick way to install the correct drivers for this card that would work too. Thanks guys.

---

### Post by danny_kay1710 on 2007-06-13
i just posted elsewhere about this and it can probably help you - if you have the windows drivers you can use a tool called ndis-wrapper

i aint too sure what cards are supported or how well it works but you could give it a shot

```
apt-get install ndiswrapper-utils 
```

Hope it helps
danny_kay1710

---


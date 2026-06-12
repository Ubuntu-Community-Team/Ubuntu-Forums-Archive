---
title: "ubuntu router instructions broke the internet"
date: 2008-03-07
forum: Absolute Beginner Talk
---

### Post by 3jd8 on 2008-03-07
I was trying to setup one of my computers as a wireless router.   I was following the instructions at

[https://help.ubuntu.com/community/Router](https://help.ubuntu.com/community/Router)

Things got ugly and i couldn't connect to the internet.  I tried to revert what i had done, and went back to using a wired router.  All my other machines worked fine with the wired router (so i know it's not the problem) but the machine i was trying to turn into a wireless router couldn't connect to the net.  All i want to do now is get my machine back up and running with the wired router.

Everything seemed to break when i ran the firewall.sh script.   I removed everything from /etc/network/interfaces except the eth0 section.  When i checked eth0 ip address, it was 192.168.0.101, which i assume means it was being assigned by the router.   I could ping 192.168.0.1, i assume this means i can talk ot the router. 

I removed everything from iptables (i found some instructions online).   When i type iptables -L -v it returns just the column headers, with no rules.  I assume this means i've turned off the firewall.  

I've run out of ideas for how to trouble shoot this.  Does anyone have any ideas?

---

### Post by DonnOMalley on 2008-03-07
What does your routing table look like? run "route" from the terminal and post results

---

### Post by steveneddy on 2008-03-07
> 
ubuntu router instructions broke the internet


Nope. Internet still works here.

Sounds like a local issue.

---

### Post by 3jd8 on 2008-03-08
I have to appologize.  I got my wired network working.  Not exactly sure, but when i booted up the machine this morning, it seemed to be working.   After some testing i see that it doesn't like when i have both a wired and a wireless network going.  Perhaps i will leave the wireless network well enough alone and just buy another network cable.

---

### Post by steveneddy on 2008-03-08
> **3jd8 said:**
> I have to appologize.  I got my wired network working.  Not exactly sure, but when i booted up the machine this morning, it seemed to be working.   After some testing i see that it doesn't like when i have both a wired and a wireless network going.  Perhaps i will leave the wireless network well enough alone and just buy another network cable.

That....odd...my Linksys router allows wireless and wired connections simultaneously

Some settings may not be correct.

Have you tried a traditional router?

You may have better luck posting in the networking forums.

---

### Post by halitech on 2008-03-08
were you trying to run a wired and wireless connection on the same computer? or are you referring to the router not liking both?

---


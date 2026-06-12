---
title: "firefox issue"
date: 2008-02-22
forum: Absolute Beginner Talk
---

### Post by articwolf939 on 2008-02-22
ok well when i go to certain sites like burton.com and limewire.com and a few other that i should be able to go to i get a error and it wont let me go the error is problem loading page any ideas?

---

### Post by Presto123 on 2008-02-22
Maybe your browser is not allowing cookies. Check that in Firefox: Edit/Preferences/Privacy. If it is enabled, check the exceptions.

---

### Post by articwolf939 on 2008-02-22
nope its not that im not sure why its doing this

---

### Post by Presto123 on 2008-02-22
I see one thing that is common between the two sites: they use heavy doses of Javascript. Do you have Java?

---

### Post by articwolf939 on 2008-02-23
yea i believe so i have download the ubuntu-restricted- so i think i have javascript is there anther way to get it?

---

### Post by Presto123 on 2008-02-23
If you have it and neither fix works, I do not know what to tell you.

---

### Post by ShodanjoDM on 2008-02-23
Can you ping both sites?
open terminal and type:

ping [www.burton.com](www.burton.com)

or

ping [www.limewire.com](www.limewire.com)

---

### Post by articwolf939 on 2008-02-23
this is what i get when i try to ping them

 kyle@kyle-laptop:~$ ping [www.burton.com](www.burton.com)
PING burton.com (208.39.45.172) 56(84) bytes of data.
From kyle-laptop.local (192.168.0.198) icmp_seq=1 Destination Port Unreachable
From kyle-laptop.local (192.168.0.198) icmp_seq=2 Destination Port Unreachable
From kyle-laptop.local (192.168.0.198) icmp_seq=9 Destination Port Unreachable
From kyle-laptop.local (192.168.0.198) icmp_seq=10 Destination Port Unreachable
From kyle-laptop.local (192.168.0.198) icmp_seq=11 Destination Port Unreachable
From kyle-laptop.local (192.168.0.198) icmp_seq=16 Destination Port Unreachable
From kyle-laptop.local (192.168.0.198) icmp_seq=27 Destination Port Unreachable
From kyle-laptop.local (192.168.0.198) icmp_seq=28 Destination Port Unreachable

--- burton.com ping statistics ---
28 packets transmitted, 0 received, +28 errors, 100% packet loss, time 43493ms

---

### Post by Fred_E _krugar on 2008-02-23
Are you running any kind of IP blocker??

---

### Post by articwolf939 on 2008-02-23
yea i am im running IPblock

---

### Post by ImThatNerd on 2008-02-23
Open up FireFox.
In the URL box put 'about-config' (without quotes)
Scroll down until you find the line 'network.dns.disableIPv6'
Under value you will see it says false. Double click that so it says true.
Reboot firefox

---

### Post by articwolf939 on 2008-02-23
i cant i still get that cant load page error even when i type
 about-config

---

### Post by Presto123 on 2008-02-23
It's actually about:config

Just know that you will be disabling your blocker with his tip.

---

### Post by ImThatNerd on 2008-02-23
> **Presto123 said:**
> It's actually about:config

Just know that you will be disabling your blocker with his tip.

Ah yes, it is about:config. Man it is too late for me.. lol

---

### Post by articwolf939 on 2008-02-23
will it still block for deluge or will it disable it for firefox only or all together?

---

### Post by kooolrock on 2008-02-23
reinstall firefox

---


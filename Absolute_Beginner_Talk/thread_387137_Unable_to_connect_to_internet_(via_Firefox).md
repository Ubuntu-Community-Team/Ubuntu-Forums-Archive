---
title: "Unable to connect to internet (via Firefox)"
date: 2007-03-17
forum: Absolute Beginner Talk
---

### Post by alfonsos on 2007-03-17
I just installed Ubuntu 6.06 on my Windows xp computer (dual boot) from a live CD (Canonical). The live CD itself connected fine to the web. However, after I installed the OS onto my computer from the same CD, Ubuntu would not connect to the internet.(!) How can it connect via the CD live but not from the installed OS from the selfsame CD? How do I fix it? Reinstall?

---

### Post by Efwis on 2007-03-17
dont' reinstall, click on System=>Administration=>Networking

you will probably have to put your password in to gain access, next highlight eth0 and make sure it is activated, if you see the activate button greyed out than it is already activated. If you still don't have access, click on properties, and see if it is set to dhcp or static ip, Thats a drop down box, if it is set to dhcp, then choose static IP and enter the info from either your ISP information, of if you are dual booting with Windows you can get this information from the networking tab.

If you still don't have internet connection let us know so we can try to help you.

---

### Post by pt123 on 2007-03-17
what response do you get when you go to your terminal and type:
ping [www.google.com](www.google.com)

---

### Post by freebird54 on 2007-03-17
If it worked OK off the live CD, then it might just be the ipv6  problem - even on Dapper.  You might want to try entering this in your terminal window (Applications->Accessories-<Terminal)

```
gksudo gedit /etc/modprobe.d/blacklist
```

and enter this  into the file:

```
blacklist ipv6
```

Save the file and reboot your computer. 

You could also enter an address of about:config into Firefox, search for 'network', then double click on   **network.dns.disableipv6**  to enable this option.  SHOULD get you going if you haven't changed too much else! :D

---

### Post by alfonsos on 2007-03-18
> **Efwis said:**
> dont' reinstall, click on System=>Administration=>Networking

you will probably have to put your password in to gain access, next highlight eth0 and make sure it is activated, if you see the activate button greyed out than it is already activated. If you still don't have access, click on properties, and see if it is set to dhcp or static ip, Thats a drop down box, if it is set to dhcp, then choose static IP and enter the info from either your ISP information, of if you are dual booting with Windows you can get this information from the networking tab.

If you still don't have internet connection let us know so we can try to help you.

Hi Efwis. I tried that (changed DCHP to static ip and supplied the required additional info) - no soap, didn't work. I looked at the network properties with the live CD and it is also set to dhcp. Likewise Windows xp. So, I'm thinking the problem lies elsewhere as dhcp appears to be the proper setting.

---

### Post by alfonsos on 2007-03-18
> **pt123 said:**
> what response do you get when you go to your terminal and type:
ping [www.google.com](www.google.com)

I get: "Unknown Host"

---

### Post by alfonsos on 2007-03-18
> **freebird54 said:**
> If it worked OK off the live CD, then it might just be the ipv6  problem - even on Dapper.  You might want to try entering this in your terminal window (Applications->Accessories-<Terminal)

```
gksudo gedit /etc/modprobe.d/blacklist
```

and enter this  into the file:

```
blacklist ipv6
```

Save the file and reboot your computer. 

You could also enter an address of about:config into Firefox, search for 'network', then double click on   **network.dns.disableipv6**  to enable this option.  SHOULD get you going if you haven't changed too much else! :D

Hi Freebird. I implemented your suggestion thru the Firefox route (about:config). I changed the true/false binary from false to true, rebooted, checked to make sure the value didn't default to false (it hadn't). No joy - still no connection. I'm assuming the above directions (via terminal) would accomplish the same thing. It still seems crazy to me that I have a network connection with the live CD but not with an install from the same CD.

---

### Post by freebird54 on 2007-03-18
IF ipv6 is the problem, you should try the blacklist edit.  This will avoid the module being activated system-wide.  Only some people have found the Firefox fix to be enough.  Essentially, with many routers sold for home use, there are many useless attempts to resolve addresses by ipv6 methods.  In some cases, it is also necessary to upgrade the firmware of your router to cancel out the unnecessary DNS requests.  (Something about giving up the 'lease' from the ISP too soon, and re-requesting another).


However, the only other thing I can suggest is to retry the Live CD, and try to identify in which settings it differs from the actual install.  If blacklist doesn't go, we'll have to try that route I guess - or get someone with more experience than I have on this problem...   Let us know how it goes!

---

### Post by carusoswi on 2007-03-18
I experienced this same problem this morning.  Info in this post pointed me in the right direction to solve the problem (problem is now solved).  When I went through System-->Administrator-->Networking, I found my wired connection shown as "not configured".  I configured it by switching to Static IP address, then entered my ip and subnet mask addresses (I found those by first booting into my XP OS and copying the settings from view network connections - ubuntu would not accept the last .2 of my windows subnet mask address but it worked anyhow).  I then switched back from Static IP to auto configure (DHCP).

I do not know why what I did worked - someone more knowledgeable than I can explain it - whether I really needed to enter those addresses or just switch to auto configure - I tend to lose track of how many things I tried while troubleshooting this - but, none of them worked until I did what I describe above.

FWIW, my internet connection was not working from either the LiveCD or the installed OS.  Everything is working now.

Thanks for pointing me in the right direction.  Hope my contribution helps someone else out of this problem.

Caruso

---

### Post by alfonsos on 2007-03-18
> **freebird54 said:**
> IF ipv6 is the problem, you should try the blacklist edit.  This will avoid the module being activated system-wide.  Only some people have found the Firefox fix to be enough.  Essentially, with many routers sold for home use, there are many useless attempts to resolve addresses by ipv6 methods.  In some cases, it is also necessary to upgrade the firmware of your router to cancel out the unnecessary DNS requests.  (Something about giving up the 'lease' from the ISP too soon, and re-requesting another).


However, the only other thing I can suggest is to retry the Live CD, and try to identify in which settings it differs from the actual install.  If blacklist doesn't go, we'll have to try that route I guess - or get someone with more experience than I have on this problem...   Let us know how it goes!

Freebird, I did the blacklist edit. I edited the file and tried to match the format of the file entries (# explanation to myself, with command ("Blacklist ipv6') immediately underneath). I'm telling you all this because when I (after rebooting) checked "network.dns.disableipv6" in firefox the value was still false; I would have expected it to flip to true inasmuch as the blacklist command is global. So, I can't rule out that the command did not "take" for some reason. Maybe I got the format wrong? Anyway, as you've probably guessed, it didn't work. Thanks for the effort. Al

---


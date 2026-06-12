---
title: "connection problem"
date: 2007-07-08
forum: Absolute Beginner Talk
---

### Post by pascalosti on 2007-07-08
Ive had ubuntu for about 1month now, it immediately connected to the net.

About 5 days ago playing Warcraft 3 my wired connection stopped working.

I can still connect leeching of someone else's wireless.  When i connect to wired it says its connected, modem say s there is pc activity, but I get an error message from the browser.

I thought at first it was the cable company ( shaw), so I took it to school and same thing (wired does not work).  I also heard that network cards don't really burn out.  The cable company is coming by 10 days from now.  

Is there something specific I can try before I go out and buy another laptop or wireless modem.

I have not adjusted anything on the network.

---

### Post by trinaryouroboros on 2007-07-09
> **pascalosti said:**
> Ive had ubuntu for about 1month now, it immediately connected to the net.

About 5 days ago playing Warcraft 3 my wired connection stopped working.

I can still connect leeching of someone else's wireless.  When i connect to wired it says its connected, modem say s there is pc activity, but I get an error message from the browser.

I thought at first it was the cable company ( shaw), so I took it to school and same thing (wired does not work).  I also heard that network cards don't really burn out.  The cable company is coming by 10 days from now.  

Is there something specific I can try before I go out and buy another laptop or wireless modem.

I have not adjusted anything on the network.

I worked for Cablevision as a high level tech for a few years, I might be able to help from the ground up in this case.

If you tried using the laptop at someone else's house, were you using a different Ethernet wire? If not, I would swap that Ethernet wire firstly. They can get faulty, and I usually check that foremost if possible.

Otherwise, if I were you and I was sure the wiring wasn't the issue at all, I would try a BartPE CD, or some other bootable OS that supports networking - to see if there's a problem.

If no problem exists when using a portable OS, then it would be prudent to start digging through the forums on here regarding networking issues in general.

However, if the network card still exhibits similar problems using a BartPE CD (or otherwise) then you know the hardware is the problem...

Again, all this is just base hardware stuff. I can't tell you what to look for in your Ubuntu networking files.

Also - I'm not sure if you installed the "Firestarter" program, the Ubuntu recommended firewall, but, it's possible that the wired and wireless network connections are conflicting. You might want to see if you can disable it to see if there's any results. If it does work, you might have to adjust your specifics in System -> Admin -> Networking, so as to disable the Wireless connection when you're Wired.

---


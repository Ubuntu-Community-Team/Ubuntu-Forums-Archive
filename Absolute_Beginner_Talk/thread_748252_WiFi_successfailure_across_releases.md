---
title: "WiFi success/failure across releases"
date: 2008-04-07
forum: Absolute Beginner Talk
---

### Post by brahnn on 2008-04-07
Not sure where this post should go, but having just installed Ubuntu last week for the first time, this one seems appropriate. (Suggestions on reposting any of the info welcome.) The short version is that I finally found a solution that works (after days of forum searches, head scratching/pounding), but after relaying my odyssey & discoveries I have a remaining question.

I decided to build a dedicated Ubuntu laptop. I started with Ubuntu7.10, and a new hard drive on a 6-year-old Sony laptop. Love it, everything seemed to work fine. I'm using a PCMCIA WiFi card (801b, Realtek 8180 chipset). Worked great on WinXP throughout Mexico, Central, & South America where I was voyaging on my sailboat. However, in returning to the US and with my friend's 2WIRE 1701 router, I had to stop using Realtek software and only use Windows connectivity software to get a WEP-based login. Ubuntu 7.10 recognized the card, talked to the local systems, even recognized that I needed a 128-bit WEP passcode and asked me for it. Upon hitting Enter, the computer/system froze. Only functional key was the power button. The 'link' light on the WiFi card did come on, but not much good at that point.

I don't generate enough of a signal to reach the other nets in this area (no crashes during the attempts) so I went to a local brew pub (tough working environment, I know, but I was that dedicated to get it working), connected perfectly without a password and happily surfed the net over a few beers, uhhh, hours. Downloaded and installed lots of cool Ubuntu stuff.

Started surfing this forum. Tried editing files (network/interfaces), installing ndiswrapper with XP and Win98 drivers, and most other stuff I could find. No luck. A hard-wired connection (eth0) works fine through the same router and computer (all versions of Ubuntu).

Tried upgrading (run-window update manager command) to Ubuntu 8.04 beta. With kernel release 15, the WiFi card isn't even powered up. No wlan0 acknowledgment at all in any hardware list I can find. With beta release 14 the card powers up, communicates with the local nets, but again the computer/system seizes after entering the WEP passcode.

Today, went backwards and tried Ubuntu 6.06 from CD and finally: seamless, effortless WiFi connectivity, WEP password and all. Took a little activation/configuration through standard windows.

But after 'tasting' the newer releases, I'm hooked. I WANT a current Ubuntu computer!

Question (finally): Is there an upgrade path that will allow me to keep the WiFi functionality?

---

### Post by VncentVega on 2008-04-07
Just my .02 cents but I wouldn't recommend upgrading quite yet. Sure the new upgrades may have some features that are nice , but I'm of the school of thought , if it ain't broke don't fix it. Wait until the stable versions come out.

---

### Post by brahnn on 2008-04-09
Thanks VncentVega. Since I'm starting from scratch I can choose what I want. I was mainly exploring rebuilding my computer from scratch and dropping windows, but functionality I want (eg, WINE) isn't listed in the 6.06 package manager and other things I now consider standard weren't standard in 2006. Looks like I'll go dual boot for now.

---


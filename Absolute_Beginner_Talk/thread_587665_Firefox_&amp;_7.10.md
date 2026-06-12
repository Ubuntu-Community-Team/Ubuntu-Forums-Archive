---
title: "Firefox &amp; 7.10"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by Suncoaster on 2007-10-22
I have just completed the upgrade to 7.10 and everything seems to be working fine except I cannot access the internet with either Firefox or Evolution.  The network card is working fine as I can access other machines on my network and I can ping places outside my network such as "Google.com".

I am a total noob with Ubuntu can someone help me please.

---

### Post by mikeyphi on 2007-10-23
> **Suncoaster said:**
> I have just completed the upgrade to 7.10 and everything seems to be working fine except I cannot access the internet with either Firefox or Evolution.  The network card is working fine as I can access other machines on my network and I can ping places outside my network such as "Google.com".

It's possible that, following the 'upgrade', the internet settings for Firefox and Evolution were corrupted - open Preferences in both and enter correct settings.
Hope that helps!

---

### Post by alienexplorers on 2007-10-24
Go to Firefox>preferences>advanced>network and select Direct connection or proxy if using a proxy.

---

### Post by Suncoaster on 2007-10-24
Thanks for your help but these settings were ok.  I seem to have fixed the problem, it appears to be a problem with ipv6.  As soon as I disabled that it all started to work.

Dave

---


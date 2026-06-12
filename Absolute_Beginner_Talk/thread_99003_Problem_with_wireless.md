---
title: "Problem with wireless"
date: 2005-12-04
forum: Absolute Beginner Talk
---

### Post by Goonie on 2005-12-04
Hi all

I just installed 5.10 today and everything works fine except my wireless connection. I first installed Warty a while back and wireless worked flawlessly (using ndiswrapper). Then I upgraded to Hoary and it no longer used ndiswrapper, but switched to the ipw2200 module. I started to get alot of random errors related to ipw2200 at boot time and got disconnected alot. No I do a fresh install of Breezy and wireless doesn't work at all. Here are a few points to consider:

1. iwconfig and ifconfig both recognize my card

2. I can activate it and configure it in the gnome network configuration tool but I can't get an IP from my dhcp (tried static as well).

3. All the info is correct in /etc/networking/interfaces

4. lspci sees the card correctly

5. Hardware is working fine, works well on windows (dual boot) and has worked on previous Ubuntu installations.

6. iwlist eth1 scan shows my network correctly as well as a few others around me.

7. lsmod shows that ipw2200 is loaded and used by 0 processes

Ok so what is the deal? I read that Ubuntu comes with an ancient version of the ipw2200 driver installed (0.19 when the latest stable is 1.0.0). And all possible solutions I've read about are not really for newbies like me. Is there a way to fix this easily? Is there an official Ubuntu how-to on this subject?

I refuse to believe that I have to turn away from this distro because it gets less compatable with my laptop in every new release. 

I hope someone can walk me through this as I need this problem fixed so I can continue my love affair with this distro.

Thx for listening

Gunnar

---

### Post by mlomker on 2005-12-04
Breezy includes the latest version of the driver, afaik (I use that driver).  Do you have any kind of security enabled on your access point that might be preventing you from connecting?  A good test is to temporarily disable all security settings and make your access point open.

---


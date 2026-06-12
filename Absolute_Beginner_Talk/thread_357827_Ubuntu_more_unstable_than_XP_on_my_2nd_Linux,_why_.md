---
title: "Ubuntu more unstable than XP on my 2nd Linux, why is that?"
date: 2007-02-10
forum: Absolute Beginner Talk
---

### Post by jingo811 on 2007-02-10
I've been using Ubuntu for about 1 year now and feels pretty much comfortable about where to look if I want to make the ordinary things work like Internet,office and media stuff.
So with that confidence I figured that it would be a cakewalk to install Ubuntu on my parents PC and try to convert them from using Windows XP.

So using the same Install CD that've used for my own PC I installed Ubuntu on my parents PC.
It got installed with a little patience the new Live Boot Ubuntu Install concept always malfunction midways but I'm used to that by now.  You just need to reboot 3 times in order to properly install Linux.

Since Ubuntu got confused by my parents PC which has 2 built-in NICs nobody used Ubuntu on that PC for some month.  Now after a 800 post thread Internet kind of works but it's still not stable.......
But today I wanted to check up on it and logged in but was faced with no Desktop.  I rebooted my parents PC and logged in again still the same no Desktop.  Why is this?

How come the same Ubuntu Installations differ so much apart between my own and my parents PC.  I've used the same CD the same methods to setup Ubuntu, still Ubuntu feels MUUUCH more unstable than Windows XP when running on my parents PC :( compared to my first Ubuntu install on my own PC.

---

### Post by firefly2442 on 2007-02-10
Did you go under System -> Administration -> Networking to check on the two NIC cards?  One will be eth0 and the other eth1 probably.  Did you install Edgy, the latest version?  Can you give some more details on why you think it's unstable?

---

### Post by Maestro23 on 2007-02-10
System specs on both machines as well.

---

### Post by NeoGreen on 2007-02-10
If you used the same cd that you used when you installed Ubuntu, it is probably outdated.  I tried to install Ubuntu Breezy Badger on my sisters PC and had the same problems.  I don't know why but it did.  All I can say is that maybe your parents computer is much newer than yours and that may be a problem.  Another thing check the processor, is it Intel or AMD. There are some distros that run on certain processors.

---

### Post by jingo811 on 2007-02-10
> Did you go under System -> Administration -> Networking to check on the two NIC cards? One will be eth0 and the other eth1 probably. Did you install Edgy, the latest version? Can you give some more details on why you think it's unstable?
I can't no more when I login there's no Desktop just a brown background.  There's no way for me to navigate.
I don't think you guys need to worry about the Networking stuff I already have 900 ppl working on it I hope
[http://www.ubuntuforums.org/showthread.php?t=346229](http://www.ubuntuforums.org/showthread.php?t=346229)
But if you feel like it jump to page 4 on that thread I summarized my whole networking madness.
I dunno why its unstable, yesterday I logged in fine and Synaptic installed some minor updates as usual, today Desktop just isn't there anymore?

**My first Ubuntu install PC - stable Ubuntu for 1 year and counting...**
AMD Athlon 2.2 Ghz something, 1 Gb RAM, ATI Radeon 128 Mb (Graphics card)
Ubuntu 6.06 Draker, (Long Term Support)

**My parents and my second Ubuntu install PC - unstable Ubuntu since beginning**
AMD Sempron 1.5 Ghz something. 512 Mb RAM, Nvidia Geforce 64 Mb (Graphics card)
Ubuntu 6.06 Draker, (Long Term Support)

---

### Post by NeoGreen on 2007-02-10
Have you tried to press ESC at the startup, this will give you options to check and fix your distro.

---

### Post by jingo811 on 2007-02-10
ESC didn't work at any stage however I tried running Recovery Mode from the Grub menu, then when I got to the prompt I entered: exit
Then it rebooted and I started Ubuntu as normal, logged in and Desktop was fine again.
Networking was not however which leads me to believe that the Desktop vanishing trick was an effect of me tampering with the interfaces list last night.
> sudo gedit /etc/network/interfaces
> 
#auto lo
#iface lo inet loopback

auto eth0
iface eth0 inet dhcp

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

#auto wlan0
#iface wlan0 inet dhcp 
It didn't like that I #commented# out "lo inet loopback" it was something really important I guess coz it added a line on the bottom list when I disabled it last night.

Well now that the Desktop problem is solved I guess I'm going back to the HEXed Networking thread again.  Tnx ppl and check out that thread if you have time.

---


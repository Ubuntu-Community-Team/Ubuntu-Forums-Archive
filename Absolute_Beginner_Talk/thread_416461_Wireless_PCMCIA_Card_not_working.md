---
title: "Wireless PCMCIA Card not working"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by -=-=-Clicky-=-=- on 2007-04-21
I cant get my wireless netgear WG511 v2 card to work. Its a PCMCIA card that I put in my laptop. 

I've installed the inf windows 2000 driver using ndwiswrapper.

Ubuntu does not detect it at all. No lights show up on the card.

What can I do?

---

### Post by johnny4north on 2007-04-21
check out this post- [http://ubuntuforums.org/showthread.php?t=109419&page=2&highlight=wireless+netgear+WG511+v2](http://ubuntuforums.org/showthread.php?t=109419&page=2&highlight=wireless+netgear+WG511+v2) 

 wwood Re: netgear wg511 v2 YAWQ
Perhaps mainly for myself, here's a history dump what I did from start to finish to enable my wireless card I talked about above

First I got all the other repositories running; ndiswrapper is in universe or multiverse I think.

Installed ndiswrapper-utils-1.8 using synaptic.

unpacked the tar.gz file in my post above into the folder t in my home directory.

<code>
1 lspci
2 uname -a
3 cd t
6 sudo ndiswrapper -i WG511v2.INF
7 ndiswrapper -l
10 sudo depmod -a
11 ifconfig
13 sudo modprobe ndiswrapper
14 dmesg |grep ndiswrapper
15 ifconfig
</code>

are u using ndiswrapper 1.8?

---


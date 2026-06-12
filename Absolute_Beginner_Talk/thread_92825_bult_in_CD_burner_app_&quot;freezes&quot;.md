---
title: "bult in CD burner app &quot;freezes&quot;"
date: 2005-11-20
forum: Absolute Beginner Talk
---

### Post by red_Marvin on 2005-11-20
When trying to burn with the built in (breezy) cd burning app, the computer starts
lagging enormously (4spf or something) and then seems to freeze totally
(no ctrl-alt-del or anything) when looking at tty1 (is it that that is a virtual console?)
I get the following messages once/ seconds or something: (numbers change, a timestamp?)

[seven-digit-number.six-digit-number] hdd: drive not ready for command

when pressing ctrl-alt-del here it starts rebooting (sending TERM signal and so on)
but continues to give the error messages until the final bunch of reboot messages
arrive.

A search on the forum turned up that it might be a problem with automounting
but there wasn't much to work with there for me.

K3B does also lag/freeze so it's probably not a bug in the burning program at least...

---

### Post by apjone on 2005-11-20
how mauch ram you got? and speed of cpu?

---

### Post by red_Marvin on 2005-11-20
2,6GHz P4 and 512Mb RAM + 1.5Gb Swap

---

### Post by wobster on 2006-04-24
I just had a fresh installation of Ubuntu. Afterwards I also encountered freezes when trying to record a cd. 
Since I found several entries in this board concerning this, I simply wanted to drop a note: 

Make sure the recoder's DMA (hdparm -d1) is enabled. Otherwise there is an immediate lock-up on access. 

That's it. Thank you.

---


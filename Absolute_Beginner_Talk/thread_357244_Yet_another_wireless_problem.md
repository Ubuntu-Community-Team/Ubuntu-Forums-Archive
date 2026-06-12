---
title: "Yet another wireless problem"
date: 2007-02-09
forum: Absolute Beginner Talk
---

### Post by akao79 on 2007-02-09
So i installed 6.10 yesterday. Wireless out of the box working great, got onto a network and ubuntu lets me know that i need to update.  After running update wireless is dead.  I'm using a toshiba portege 3500 and it seems that the wireless card it uses is either a generic brand or an intel chip.  Looking around the forums and online the only problem i can potentially find is that the 3500 wireless card does not like orinoco.  Any suggestions?

I can run the usual lspci etc.. if needed.

Thanks in advance

Update:

Well it looks like i can find the wireless card in the device manager. The odd part is that under info.bus str=pcmcia when it should be a pci device.   It comes up as a wireless Lan card under eth1.  When i try to enable it under networking the enable doesn't stick, it won't let me check or uncheck the wireless device. It just indicates that the device needs to be configured.

---

### Post by akao79 on 2007-02-09
Shameless bump

Update:

[Tried solution]("http://ubuntuforums.org/showthread.php?t=357284") but it didn't appear to do the trick.  Running out of ideas here. Might just reinstall ubuntu and try to keep the update that screwed up my wireless card out.

---


---
title: "PowerBook G3 Lombard PCMCIA slot for wireless card"
date: 2008-02-25
forum: Apple PPC Users
---

### Post by enelson72 on 2008-02-25
I recently installed Feisty on my G3 Lombard, and purchased a WPC11V3 Linksys wireless card for the PCMCIA slot. The card will light up, but I do not see it listed in the Network Manager. Am I missing a step?  Any help will be greatly appreciated.

Thanks!

---

### Post by enelson72 on 2008-02-26
I should be able to use the Orinoco driver in /usr/src in order to ge the card to be recognized correctly, right? Any thought on why it would not recognized by lshw?

---

### Post by stream303 on 2008-02-26
Have you tried adding this at the boot prompt:

pci=assign-busses

If it works, we can add it to the append= line of the /etc/yaboot.conf and do a sudo ybin -v

---

### Post by enelson72 on 2008-02-26
I will give it a shot tonight. I am a total noob with Linux, but I love what I can do with this old Powerbook I inherited, now that I have Ubuntu installed.

---


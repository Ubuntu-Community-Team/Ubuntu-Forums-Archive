---
title: "Linksys WPC11 ver3 on powerpc"
date: 2005-10-23
forum: Apple PPC Users
---

### Post by lazerdye on 2005-10-23
I just downloaded and started up my PowerPC G4 laptop using the live PowerPC version of Kubuntu, and I love it! However, before I install the full thing, I have one show-stopper, and that is a problem with my Linksys WPC11 wireless networking card. Since the built-in wireless of the laptop is not (yet?) supported, I have the wpc11 card as an alternative. However, when I insert the card into the PCMCIA slot, the green light comes on, then after about 3 seconds the machine beeps, the green light goes out. In dmesg I see:

cs: pcmcia_socket0: time out after reset.

Is there anything I might be able to do to help resolve this situation, or any more inforamation I can give?

---

### Post by b4t3m4n on 2006-03-26
I have the exact same wireless card, and I get the exact same error.  I am on an intel laptop though, which makes me think its more card specific.  When I initially installed a few days ago using latest ubuntu download, it was working.  I went away from the laptop for a few hours, when I came back, I realized it tried to hibernate.  I have had other linux distros on my laptop before, and everytime linux tries to hibernate my machine, its locks up, I have learned to accept it.  I have 8 hours of battery life, so normally I just disable all powersaving features but hadn't looked into it with ubuntu yet (part of me hoped it would just work I guess).  Anyway, after that, my wireless card stopped working, I noticed it had also upgraded the kernel, so I put the install disc back in to see maybe the old kernel on the disc would still work, but it didnt anymore.  Makes me think something is fundamentally wrong with card or my pcmcia now.

---


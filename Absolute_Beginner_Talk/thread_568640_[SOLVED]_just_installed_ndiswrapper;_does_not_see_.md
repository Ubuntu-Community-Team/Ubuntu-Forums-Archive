---
title: "[SOLVED] just installed ndiswrapper; does not see card"
date: 2007-10-06
forum: Absolute Beginner Talk
---

### Post by mandrill on 2007-10-06
followed instructions until.........driver installed, then..... nothing....(feisty 7.04, netgear wpn311), ran reports from wiki, (forgot to save them) says hardware not present? still have wireless connection from ubuntu drivers, but is  poor (why I was installing ndiswrapper)  :confused:

:~$ ndiswrapper -l
wpn311 : driver installed
        device (168C:0013) present (alternate driver: ath_pci)

---

### Post by ronocdh on 2007-10-06
> **mandrill said:**
> followed instructions until.........driver installed, then..... nothing....(feisty 7.04, netgear wpn311), ran reports from wiki, (forgot to save them) says hardware not present? still have wireless connection from ubuntu drivers, but is  poor (why I was installing ndiswrapper)  :confused:

:~$ ndiswrapper -l
wpn311 : driver installed
        device (168C:0013) present (alternate driver: ath_pci)
It is always good form to link to the exact set of instructions used for a procedure. Perhaps you forgot to **sudo modprobe** the ndiswrapper? I know that for me it's been problematic in the past if I didn't do the extraction and installation from the /src directory.

All in all, I would try posting this question on the Networking and Wireless forum, as those chaps read many posts on ndiswrapper every day. Of course, remember to search there before posting, in case someone's already been through this same thing!

---

### Post by mandrill on 2007-10-06
> **ronocdh said:**
> It is always good form to link to the exact set of instructions used for a procedure. Perhaps you forgot to **sudo modprobe** the ndiswrapper? I know that for me it's been problematic in the past if I didn't do the extraction and installation from the /src directory.

All in all, I would try posting this question on the Networking and Wireless forum, as those chaps read many posts on ndiswrapper every day. Of course, remember to search there before posting, in case someone's already been through this same thing!

I really appreciate your reply - Thank you.

Yes, I do believe I forgot to do that. Is it possible to do it now? 

But yes, I will try the other forum, thank you.

---

### Post by Griffiss on 2007-10-06
This might help:

[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,troubleshooting/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,troubleshooting/)

it says what to do when you get the 'alternate driver' message from ndiswrapper -l. substitute 'ath_pci' for 'bcm43xx'

---


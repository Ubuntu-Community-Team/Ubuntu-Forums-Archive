---
title: "How to troubleshoot revive from suspend issues in 12.04?"
date: 2013-05-19
forum: Apple Hardware Users
---

### Post by este.el.paz on 2013-05-19
Folks:

Starting a new thread since my last two posts on "Testers wanted for 12.04" remain un-responded to . . . .  I'm looking to see if it's possible to get reviving from suspend to be more dependable . . . I looked over some of the wiki on the topic but nothing seemed to apply without doing something to the system that "could do damage to the order of your system" . . . .  I searched the /sys/power  thing and saw that there is no "pm_trace" file but there is another "pm" file and there is "resume" . . . after that, I would need some guidance . . . .

> I'm replying to this thread . . . to myself or my last post in this  thread, because this thread had dropped to page 4 and the problem as I  described with the reviving from suspend issues . . . continues.  It is  not a total failure to revive, most times I get the log in window, I can log back in,  the desktop is "populated" but clicking on tabs or on icons does nothing  . . . only option at that point is to shut the unit down, this happens about 6 times in ten attempts to wake from suspend.  

This is the rsavge version of Xubuntu 12.04 for PPC on iBook 933 MHz  with 640 RAM, and I added the LXDE DE, which brings a non-working  Openbox.  I might have had Lu 12.04 loaded before, and probably the  suspend issue was a problem there, in this version sometimes it works  but many times it doesn't.  Any thoughts appreciated, perhaps removing  the LXDE DE?

e.e.p.

---

### Post by este.el.paz on 2013-06-06
Folks:

Brief update on the situation, but first I'd like to say thanks to all those who offered some insight or help into this issue--I didn't get the memo, but thanks for trying . . . .

Anyway, it seems like there might have been some change in the last week or so, possibly in an update or change of kernel, that has brought a more consisten revive from suspend to the G4 iBook.  I'm running the rsavage version of Xu 12.04, **but** apparently the Xubuntu DE was too much effort to revive and I'd be forced to shut the computer down and restart each time; so rather than deleting the LXDE DE it seems that it is more consistently reviving from suspend using the LXDE . . . DE.  That makes this system much more useable . . . lets hope it continues.  Perhaps the computer has "figured out" how to revive from suspend on its own, apple units are pretty good that way.  Thanks for listening.

e.e.p.

---


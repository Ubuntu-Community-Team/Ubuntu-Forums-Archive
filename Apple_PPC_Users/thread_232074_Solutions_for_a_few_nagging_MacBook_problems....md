---
title: "Solutions for a few nagging MacBook problems..."
date: 2006-08-08
forum: Apple PPC Users
---

### Post by hajk on 2006-08-08
Several people have reported on wireless problems with the latest 2.6.15-26-686-smp kernel. The madwifi-ng kernel modules are loaded, but the ath0 interface won't come up, at least not easily; network-manager/nm-applet don't even see any wireless networks. This is how I make it work (assuming that ath0 has already been configured): after booting, open System-Administration-Networking, deactivate and reactivate ath0, and wait till the interface finally seems to have come up. Then quit, and in a terminal try "ping www.yahoo.com" to show that atho has not in fact come up.
Now do "sudo ifup ath0" and (YEAH) there it is! Works everytime, but I have no explanation as to why this precise course of events is needed...

Another issue is that sound settings in Ubuntu will carry over to Mac OS X!
After installing Ubuntu Dapper to my HD (see [http://www.xs4all.nl/~hajk]("http://www.xs4all.nl/~hajk") for a full report) I noticed that the sound in Mac OS X had become very faint, despite all the volume sliders being at 100%. I didn't see any way to get to the sound card settings in Mac OS X, so I rebooted into Ubuntu and installed Gnome AlsaMixer. The mixer showed PCM volume already at 100%, but the Front slider at about 50%. Moving the Front slider also to 100% immediately put the volume up to normal, a setting that carried over into the next reboot into Mac OS X...

Have fun!

---

### Post by leonedo on 2006-08-13
Dude.... thanks...  the gnome-alsamixer...  nice.

---


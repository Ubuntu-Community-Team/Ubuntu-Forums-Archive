---
title: "Lin box hijacked to spam slave?"
date: 2007-01-13
forum: Absolute Beginner Talk
---

### Post by konungursvia on 2007-01-13
I'm not sure what happened. This Dell linux box runs dapper fine. It's now also downloading a HD movie from torrent. On the same IP, I set up my acer laptop to run dapper too. It ran well for a day, downloading easy ubuntu and all kinds of updates. Then it slowed down. Now on that Acer box it only seems to run in recovery mode, but there it's super slow. I type "ls" and the characters appear three seconds later. I used gparted off the cd and formatted hd2 and hd5, then re-installed dapper. The acer still runs like that, super slow as soon as the kernel loads, and freezes while loading hardware profiles every time. 

My question is, do these symptoms mean someone attacked and took over that lin box? I did leave it on all night without firestarter, while my IP address was out there torrent getting a movie from the same local network. Firestarter tells me, on the Dell, which always ran the fireall, that it has received dozens of attacks/queries, so someone is trying to look.l I'm confused. :-k

---

### Post by Chachee on 2007-01-13
Well.. if it was a spam bot your network would be really slow also.  I don't think the box would be hammered.  IF it's an older machine, maybe the default interface is too heavy for it?  Did it try to load a binary graphic driver?  That could be a problem.  Should show in startup or in your logs.

JT

---

### Post by konungursvia on 2007-01-13
Thanks! I don't think I tried that. Would that problem have peristed even after reformatting /root (hd2) and /swap (hd5) and re-installing dapper? and gnome ran beautifully for a day.

---

### Post by Pobega on 2007-01-13
I doubt it was a spam bot, if it was that would just be your connection. It *may* have been attacked, but that's highly unlikely since older computers do occasionally just die sometimes.

---

### Post by Tomosaur on 2007-01-13
Could be anything - bad memory, bad hard drive. Without running a full test it's difficult to really get an idea of what could be wrong. Does the disk churn or anything?

---

### Post by konungursvia on 2007-01-13
The disk doesn't churn, and the windoze partition runs xp just fine as well. I never uninstalled it, just got rid of some big apps like Illustrator and M$ Office before defragmenting and stuff like that. Hm.... I'm so dumb. Memory test seemed fine too. 74.101.38.252 keeps trying hits on my Dell box, and firestarter stops it. Does that help?

---

### Post by konungursvia on 2007-01-13
WEll I'll try re-instaling Dapper on the Acer with a different password. I did make a text file on this Dell with that Acer's user and pass in it to try and mount the local network, maybe that text file wasn't secure enough..... (?)

---

### Post by Tomosaur on 2007-01-13
It may be something just messed up and Linux was trying to do something in the background. If you manage to boot into a terminal, type 'ps' or 'top' and see what the program using most resources is.

---

### Post by konungursvia on 2007-01-13
> **Tomosaur said:**
> It may be something just messed up and Linux was trying to do something in the background. If you manage to boot into a terminal, type 'ps' or 'top' and see what the program using most resources is.

Yeah, maybe I ran out of HD space in the primary lin partition. Thanks for the help, I'll keep trying.

---

### Post by Circus-Killer on 2007-01-13
well, it sounds like its a problem with support one of the hardware pieces in your laptop. i seriously doubt it was an attack. firstly, remember that firestarter doesnt have to be running to mean your firewall is protecting you. firestarter is nothing more than an easy configuration interface for iptables, the actual firewall. so whether you start firestarter or not doesnt make a difference really. iptables starts up by default (in ubuntu), whether or not you have even installed firestarter.

secondly, you said you tried formatting and reinstalling dapper, which i doubt the bot would of survived. what i suspect is dapper not having full hardware support for your laptop. maybe try out edgy, or you just might even have to wait for feisty. (suppose you could try out Herd 1 when it comes out, check the forum front page for details, in that green box).

anyways, hope you have better luck in the future.

---

### Post by konungursvia on 2007-01-13
Thanks very much for the ideas. BTW, does Edgy have better hardware support for a 1998 Acer laptop than Dapper does?

---

### Post by konungursvia on 2007-01-13
I thinkyou guys were right, it seems to be a problem with the hard drive. I reinstalled dapper <again> and saw that when it loaded on startup, it seemed to go into fchdisk for a long long time (and still is there after 15 or 20 minutes) with a black screen. Will try Edgy and see if the install image doesn't have better partition and disk management.

---

### Post by konungursvia on 2007-01-13
After a super-slow disk check, it reads:

* INIT: Entering runleve: 2

cat: /var/lib/acpi-support/system-manufacturer: No such file or directory

and three more similar lines, with no "bios verson, system-version, or product name"

Then it spent several minutes saving the VESA state, and now it's spending many many minutes loading the ACPI modules.

Does this help identify the problem?

---


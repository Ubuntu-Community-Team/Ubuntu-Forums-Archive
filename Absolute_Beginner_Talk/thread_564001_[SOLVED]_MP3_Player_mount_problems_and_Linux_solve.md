---
title: "[SOLVED] MP3 Player mount problems and Linux solved"
date: 2007-09-30
forum: Absolute Beginner Talk
---

### Post by zero244 on 2007-09-30
Well its been 10 months and I finally have all my mp3 players working in Linux. In fact no distro after 2.4 would work.
I have three Panasonic SV-MP020 players that would mount in XP instantly, but not linux.
I tried every mount command known to man kind, I tried to edit the Fstab file. Searched the web for months no help.
The closest Ive ever come to the player mounting was, Ubuntu would see the drive for a few seconds and then eventually throw up the error "Not a valid block device".
I pretty much gave up till I did a search on google again and it lead to some obscure forum somewhere. And they suggested a terminal command that workeddddddddddddddddddd.
The fix is not the most glamorous but it does work like a charm on all my flash players of different brands, including the ipod.
It seems kernel versions later than 2.4 have a compatibility issue with some USB 2.0 devices.
Ok so here is the fix.
In terminal copy and paste:

sudo rmmod ehci_hcd
password:
Then plug in your mp3 player and I bet it will mount.
Apparently what this does is turn off USB 2.0 and reverts to USB 1.1.
Though my players seem to transfer just as fast, some people have said that there ipods slowed up.
Also apparently this command goes away on reboot, so you will have to use it whenever you want to mount your players.
I created a launcher and put it on my desktop.
Now I know all you Ubuntu veterans will say, hey Ive known about this for years. Well why didn't you say something......>Ive posted a question about this matter twice and got no answer or not the right answer.
I know a lot of people are having probs with mp3 players and cameras etc. I haven't tried this with my camera yet.......it might work for that too.
So give it a try guys........now that my players work the only reason I need XP now is for games and my scanner. 
One less reason to keep  XP.
Good Luck!

---

### Post by mlentink on 2007-09-30
> **zero244 said:**
> now that my players work the only reason I need XP now is for games and my scanner. 
One less reason to keep  XP.
Good Luck!

Is that by any chance a HP scanner?... ;-)

Thanks for reporting back. It's really great to see someone who's obviously gone through a lot of trouble come back and share with the rest of us. It's truly in the spirit of this community. 
I'm sure lots of us will appreciate your effort.
thx again.

---

### Post by zero244 on 2007-09-30
Hello My scanner is a Canon 4200F. I have looked around and everyone says its not compatable and Canon says there will be no Linux drivers ever available for this model.
But thats ok in the future I will only buy hardware that is Linux compatable.
So even if the time comes and I cant use XP even for gaming then I will just forget about Windows and move completely to Linux.

---

### Post by idr on 2008-01-15
Have tried the above and am getting 'ERROR: Module ehci_hcd does not exist in /proc/modules'.  Any ideas? Thanks

---


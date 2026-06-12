---
title: "Yaboot driving me mad!"
date: 2010-10-06
forum: Apple Hardware Users
---

### Post by jonnny_j22 on 2010-10-06
Hi all,

My desktop sadly, has not survived a recent house move, and until funding can be arranged, I have fallen back on an old G4 emac. the good news - ubuntu runs great on it! - the bad - I just can't seem to get yaboot to tripple boot my osx , ubuntu and gentoo installs.

dual booting either linux and osx is fine, but trying to get the three has eaten up 4 days now and I have finaly found myself threatening my computer with ice cubes in the cd drive!

I installed gentoo second as this takes the longest and theirs more chance of stuffing things up, and yaboot was a pain in the behind then, but got it working. ubuntu was a sinch as always, but didn't configure it's yaboot install for the gentoo apartition like with a grub and i have been editing the yaboot.conf ever since.

if there is any help you can give, it'd be greatly apreciated as at the moment I have two linux in there.. i just can't get to them!

my bootstrap is /dev/hda2
gentoo root is /dev/hda5
ubuntu root is /dev/hda7

Thank you so much in advance, i'm really missing grub2 atm!

---

### Post by linuxopjemac on 2010-10-07
you have to find out where your yaboot.conf resides. From that partition you have to issue ybin later if yaboot.conf is fine:

[http://mac.linux.be/content/yaboot](http://mac.linux.be/content/yaboot)

---


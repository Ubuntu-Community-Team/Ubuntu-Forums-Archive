---
title: "Wireless"
date: 2006-10-07
forum: Absolute Beginner Talk
---

### Post by MrKlean on 2006-10-07
Hi Guys,  I'm trying to set up my WG311v3 card in Edgy.  I had it werlin in Badger, but I can't get it now ; (  I know it's something I'm doing or not doing..but I'm stuck ; (  I know I need ndiswrapper..have the latest..something sticks in my mind about kernal headers or something, but I can't find anything on it.  You're help would be greatly appreciated. I tried the new Mandriva and ..well..it ain't Ubuntu LOL!!

Thanks ; )

---

### Post by motstudios on 2006-10-07
well, im dont know too much about getting wireless cards working in ubuntu but ill give it a shot to help.

well, for one try the network manager in ubuntu. if the card "is" listed then it may just need configuring and activating.

if u MUST use ndiswrapper, i believe its in the repository (correct me if im wrong) so u would need to sudo apt-get install ndiswrapper

you "can" compile ndiswrapper from source but u will need the kernel sources, build-essential and your windows version of the driver. the sources and build-essential are in the repository i know cuz i installed them. cant remember if u have to edit the repos or not though.

theres a ndiswrapper tutorial here: [http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation)

hope this helps. my belkin wifi card "just worked" when i installed ubuntu but i had to use ndiswrapper in slackware.

---

### Post by MrKlean on 2006-10-07
Thanks for the reply..I'm trying every thing I'm reading. What kind of belkin do you have..might be easier to get a new card LOL!!

---

### Post by motstudios on 2006-10-07
im not too sure what chipset my card uses but its a "belkin wireless g" card and uses the atheros driver that ubuntu comes with. i believe theres a user on this forum who knows "the best" wifi card to get that "just works". maybe they will come by and post a link

---


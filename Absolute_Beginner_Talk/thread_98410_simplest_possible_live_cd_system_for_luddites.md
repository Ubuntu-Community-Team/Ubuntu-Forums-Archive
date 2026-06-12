---
title: "simplest possible live cd system for luddites?"
date: 2005-12-03
forum: Absolute Beginner Talk
---

### Post by retep57 on 2005-12-03
hello, i am looking into  the simplest possible system for total luddites ( my parents - who hate computers!) i have given them disks with loads of family pics  but even there  "bew" dvd player cant read them :(

maybe a real cheap computer , hmmm  they are panicking about "what if it goes wrong?!"

maybe it is overkill but i am thinking of a  live cd setup so they wont have a chance to mess it up..

prob a 2 cd system to put  jpegs in one and live cd in the other,  hmm surely that would work -- and be cheap...  (with options for upsizing should they get the bug)
 i cant see why this would not work, cheers there are other pic view options around  but i dont want to post sd cards etc etc thru the mail as they live many many miles away  cheers , 

any otehr ideas?

---

### Post by teaker1s on 2005-12-03
could use live cd or buy then a new cheap dvd player that reads jpegs

---

### Post by az on 2005-12-03
[QUOTE=retep57]hello, i am looking into  the simplest possible system for total luddites ( my parents - who hate computers!) i have given them disks with loads of family pics  but even there  "bew" dvd player cant read them :(

maybe a real cheap computer , hmmm  they are panicking about "what if it goes wrong?!"

maybe it is overkill but i am thinking of a  live cd setup so they wont have a chance to mess it up..

prob a 2 cd system to put  jpegs in one and live cd in the other,  hmm surely that would work -- and be cheap...  (with options for upsizing should they get the bug)
 i cant see why this would not work, cheers there are other pic view options around  but i dont want to post sd cards etc etc thru the mail as they live many many miles away  cheers , 

any otehr ideas?[/QUOTE]

The dissadvantage of a live cd is that it is slow.

Ubuntu is very focused on useability.  A default install is not that breakable.  I reccomend Ubuntu over proprietairy OSes to people who have never used a computer before because of the advanced useabilty it offers.

They would turn on the computer, put in the new cd filled with photos you sent them,click, import and view them.  As easy as that.

---

### Post by jbrader on 2005-12-03
Like one of the above posts I think your live c system would be too slow. I suggest buy a cheap small form factor pc from newwgg or someplace like that (you can get a pretty ok setup for about $400 us) then install Ubuntu and all the apps you think they might need although if they're really as anti-pc as you sau they probably won't need much. Set it up with a nice pretty interface theme with big shortcuts for all the important apps, remove all the links for the unimportent apps, don't tell them the root passwoed (cuz then they can't hose anything) load all your photos on it and give it to them.

---

### Post by ssam on 2005-12-03
live cd is slow. it means they cant save documents. no security fixes. they'll have to choose the language at every boot.

i'd recommend a normal ubuntu install, but dont put their user in the admin group. there is very little damage they can do without admin powers.

if there are specific admin tasks that you trust them with (changing the time), then work out an sudoers file with the correct allowences.

install and set up openssh server so that you can log in and fix anything/do upgrades. use keys rather than passwords to make it very secure. you'll need to work out a way for them to comunicate their ip address to you, maybe add a launcher button to the panel with
```
firefox http://www.whatismyip.com/
```

---


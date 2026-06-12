---
title: "Getting from Dapper to Edgy?"
date: 2006-10-11
forum: Absolute Beginner Talk
---

### Post by petersjm on 2006-10-11
Hi all,

Okay, so I'm sure this has been asked before but I just can't find anything relevant when I search. I was wondering, if I continue to update my Dapper system daily (or whenever updates are made available) will I eventually have a shiny new Edgy system? Or do I have to download the 700mb ISO and re-install? Or can I do a sudo dist-upgrade when the time comes?

Basically, do I need to do something to my system when Edgy is released (other than update as and when), or can I sit back and watch my Drake morph into an Eft without intervention from me?

---

### Post by PriceChild on 2006-10-11
Dapper is a stable system.

Only bugfixes and security updates are applied.

Packages that won't break things will be backported.

And finally check out [https://help.ubuntu.com/community/UpgradeNotes](https://help.ubuntu.com/community/UpgradeNotes) for help upgrading.

---

### Post by ReddoC on 2006-10-11
Hello,

I did yesterday an dist-upgrade to edgy. I didn't get any problem.

to do it: "sudo gedit /etc/apt/sources.list" and replace dapper to edgy.
then sudo "apt-get update", sudo "apt-get dist-upgrade" and follow instruction.

Regards,

ReddoC

---

### Post by petersjm on 2006-10-11
Many thanks, guys. So it's not something that will happen eventually unless I dist-upgrade. I see. Think I'll upgrade later in the month, once Edgy is officially released. Although if I'm feeling brave, I might just go ahead and do it at the weekend. Thanks again :)

---

### Post by petri on 2006-10-11
When you upgrade take at look at this [https://help.ubuntu.com/community/EdgyUpgrades](https://help.ubuntu.com/community/EdgyUpgrades)

There is a nice way to change the repositories to edgy :cool:

---

### Post by petersjm on 2006-10-11
Thanks, Petri. So do you reckon Edgy is stable enough now to upgrade to? Or would I do so at my own risk?

---

### Post by petri on 2006-10-11
... at your own risk :D

I did a clean install of Dapper last week and upgraded it to Edgy as in wiki... and did not succeed. I have always had problems with my ATI card in windows and in Ubuntu so I didn't care that much :rolleyes: but then that partition was just for testing, too ;) 

I have an install from Edgy CD Knot 3 for a long time now and ATI works fine, no 3D though, and Edgy has been stable in my machine from the beginning (Knot 3).

---

### Post by petersjm on 2006-10-12
Thanks Petri. Okay, I've got one more question (I'm thinking of upgrading this evening when I'm home). When I *do* upgrade, will Ubuntu retain all my themes, GDM, cursors, etc, or will I have to reinstall them all? I'm going to backup my /home to a second HDD. Is there anything else I should worry about?

---

### Post by Ben Sprinkle on 2006-10-12
```
sudo apt-get dist-upgrade
```

---

### Post by petri on 2006-10-12
If you do an upgrade then you should have everything your special stuff left. Once I did upgrade from Breezy to Dapper I had everything from Breezy and the new stuff from Dapper. After that I moved my /home to it's own partition (see my sig) and did an clean install with Dapper. 

After clean install I did have to reinstall programs but their configuration was waiting in my /home partition and that made it easier, I didn't have to configure anything and installing programs in Ubuntu is so easy... :mrgreen: 

P.S.If you follow the /home partition link you will find a lot of usefull information about Ubuntu as for example why you should use **aptitude** instead of **apt-get** or why you have to use **gksudo** (kdesu in Kubuntu) with graphical programs.


EDIT: There is of course a little problem with upgrade like this. For example all of your themes does not work in Edgy, I think. But the themes remains in your /home/.themes (In Nautilus and your home catalogue toggle Ctrl + H and you will see the hidden files which have a dot (.) before their name)

---


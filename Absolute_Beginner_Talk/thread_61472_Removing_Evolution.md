---
title: "Removing Evolution"
date: 2005-08-31
forum: Absolute Beginner Talk
---

### Post by sophtpaw on 2005-08-31
Went into Synaptic to have Evolution removed but message came back saying Ubuntu desktop would be removed aswell?? Why Ubuntu Desktop? and what is ubuntu desktop? Gnome?

If someone could explain that to me. I want to have Thunderbird as my email/usenet group client, and want to have my system as uncluttered of unused applications as possible.


--
sophtpaw

---

### Post by macgyver2 on 2005-08-31
[QUOTE=sophtpaw]Went into Synaptic to have Evolution removed but message came back saying Ubuntu desktop would be removed aswell?? Why Ubuntu Desktop? and what is ubuntu desktop? Gnome?[/QUOTE]
ubuntu-desktop is a meta-package that basically depends on all the default desktop stuff.  You can remove it with no problems...except that if you're upgrading from one release to another (like if you want to upgrade to Breezy in October) you should then reinstall it (sudo apt-get install ubuntu-desktop) to make sure there aren't any problems.

---

### Post by Fluffy, the jolly sheep on 2005-08-31
You can go on and remove ubuntu-desktop, it's just a meta-package. This means that it depends on other software but doesn't really contain any software itself. 
The ubuntu-desktop package depends on all software that's by default in an ubuntu installation. So when you install ubuntu-desktop, synaptic will install all other default ubuntu packages like gnome, firefox etc. But if you'ld remove ubuntu-desktop, the software on which ubuntu-desktop depends won't be removed, only the empty meta-package will be deleted.

---

### Post by sophtpaw on 2005-08-31
[QUOTE=Fluffy, the jolly sheep]You can go on and remove ubuntu-desktop, it's just a meta-package. This means that it depends on other software but doesn't really contain any software itself. 
The ubuntu-desktop package depends on all software that's by default in an ubuntu installation. So when you install ubuntu-desktop, synaptic will install all other default ubuntu packages like gnome, firefox etc. But if you'ld remove ubuntu-desktop, the software on which ubuntu-desktop depends won't be removed, only the empty meta-package will be deleted.[/QUOTE]


Thank you Guys,

but i'd like to be clear what else i will be losing if i remove ubuntu desktop. I want to lose Evolution, but what else will i lose withthe desktop?

Mcgyver, i hear that i wiil need teh ubuntu desktop to upgrade to breezy which of course i will :)  so when i reinstall Ubuntudesktop agues Evolution will only come back again. 

Sounds like the best is just to learn to live with it? Does seem silly to have more than one email client kicking around especially if one of them is one that one doesn't like or wont want to use,

thx again for the info,

--
sophtpaw

---

### Post by rpgcyco on 2005-08-31
You will lose nothing else when you remove ubuntu-desktop. It's safe, however, like it's already been mentioned, you'll need to reinstall it when you upgrade to Breezy, which will reinstall Evolution.

But, once upgraded to Breezy, you can just repeat the process of removing Evolution again. :)

- Rpg Cyco

---

### Post by macgyver2 on 2005-08-31
[QUOTE=sophtpaw]but i'd like to be clear what else i will be losing if i remove ubuntu desktop. I want to lose Evolution, but what else will i lose withthe desktop?[/QUOTE]
You will not be losing anything else.  You can double-check that, also, to ease your mind.  Both in Synaptic and on the commandline with apt-get you usually have to confirm your action (unless you've manually turned off the confirmation option) and with the confirmation is a list of *all* the packages involved.  So just double-check that.  If you're just removing evolution you should just see evolution, ubuntu-desktop, and maybe one other evolution-<something> package (not sure about the last one...it's been a little while since I did it).

[QUOTE=sophtpaw]Mcgyver, i hear that i wiil need teh ubuntu desktop to upgrade to breezy which of course i will :)  so when i reinstall Ubuntudesktop agues Evolution will only come back again. [/QUOTE]
Yes, during the upgrade to Breezy when you reinstall ubuntu-desktop evolution will come back again.  However, after the upgrade is finished you can remove it again.  Yes, it adds a couple of steps to the upgrade process, but then again you only do that upgrade once every 6 months, so I don't think it's a much of a hassle to go through to keep your system rid of the stuff you don't use...  In fact, if you start getting rid of more stuff (I ditched the gnome-games and a few other default packages, too) you can keep a little one-command shell script around that you add to everytime you decide to uninstall a default package.  Call the script [font=Courier New]no_bloat[/font] or something.  Mine would look like this:
```
#!/usr/bin/env bash

sudo apt-get remove --purge evolution gnome-games-data gnome-games
```
Then after the Breezy upgrade is finished you just run your pre-fabricated script and it should get rid of everything again.  Saves you from having to remember what you don't want. :)

---

### Post by sophtpaw on 2005-09-01
thx Cyco and Macgyver for reassuring me about the exact implications.

Well...Evolution has been devolved! I didn't mind the email client so much, but i thought the usenet aspect really sucked. Thunderbird does the two in one in an uncomparable style

Now this sounds interesting too.

.... you can keep a little one-command shell script around that you add to everytime you decide to uninstall a default package.  Call the script [font=Courier New]no_bloat[/font] or something.  Mine would look like this:
```
#!/usr/bin/env bash

sudo apt-get remove --purge evolution gnome-games-data gnome-games
```
Then after the Breezy upgrade is finished you just run your pre-fabricated script and it should get rid of everything again.  Saves you from having to remember what you don't want. :)[/QUOTE]


i'd like to have a go at this. But i would need you to tell me in smaller steps how to do this. How do i create a script?

thx a million


--
sophtpaw

---


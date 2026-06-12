---
title: "Upgrade Breezy to Dapper"
date: 2006-05-22
forum: Absolute Beginner Talk
---

### Post by Clay85 on 2006-05-22
I burnt a live CD for Dapper so I could check it out. Looks cool, but now how do I Install it? The CD brings up a bunch of options, but none of them say 'install dapper'. o.O

---

### Post by gommle on 2006-05-22
[QUOTE=Clay85]I burnt a live CD for Dapper so I could check it out. Looks cool, but now how do I Install it? The CD brings up a bunch of options, but none of them say 'install dapper'. o.O[/QUOTE]

You must download the install cd and boot it :P

The live cd is purely for testing.

---

### Post by aysiu on 2006-05-22
Upgrading or installing?

You can't upgrade with the live CD.

You can install it, however, following these directions (just skip the first half of the page): [http://www.psychocats.net/ubuntu/windowstoubuntu.html](http://www.psychocats.net/ubuntu/windowstoubuntu.html)

[quote=gommle]You must download the install cd and boot it :P

The live cd is purely for testing.[/quote] Actually, the Dapper live CD can install Ubuntu. In the past (Breezy, Hoary, Warty), the live CDs were only live. Now, the live CD is also an installer CD. It cannot be used as Synaptic/apt-get source, though.

For that, you need the text-mode installer CD.

---

### Post by Clay85 on 2006-05-22
Where can I get an install ISO? All I can find is the Live ISO. (Hence my confusion.)

Edit:
text-mode installer CD? Is this going to be hard? I could just write zeros to disk and install Dapper if that'd be easier.

---

### Post by nanotube on 2006-05-22
check this link:
[http://ftp.acc.umu.se/mirror/cdimage.ubuntu.com/releases/dapper/flight-7/](http://ftp.acc.umu.se/mirror/cdimage.ubuntu.com/releases/dapper/flight-7/)
the "desktop cd" is the livecd, the "textmode install cd" is the install disk that can be used to upgrade. 

just to make sure though - do you want to upgrade from breezy to dapper, or do you just want a fresh install?

---

### Post by aysiu on 2006-05-22
[QUOTE=Clay85]Where can I get an install ISO? All I can find is the Live ISO. (Hence my confusion.)[/QUOTE] Can I be clear about what you're trying to do exactly?

Are you trying to *install* Dapper (as your post suggests) or *upgrade* to Dapper (as your subject heading suggests)?

If you're trying to install Dapper, just boot the live CD and there is an "Install" icon on the desktop.

If you're trying to upgrade to Dapper, you don't need to get a CD to do it. Just follow these directions: [http://www.psychocats.net/ubuntu/dapper](http://www.psychocats.net/ubuntu/dapper)

---

### Post by Clay85 on 2006-05-22
I was hoping to just upgrade. 

If I install Dapper I'd have to burn all my files to a CD, write zeros, then install Dapper, right? 

If I upgrade Breezy to Dapper it would be like magic, presto-chango, right?

Or would it be easier to burn my files to CDs, write zeros on the disk, then install Dapper?

---

### Post by Clay85 on 2006-05-22
Sorry, I didn't realize I was being confusing. 

My question is which would be easier? (Ubuntu is really easy to uninstall and reinstall [compared to windows!].)

---

### Post by tony_tj3 on 2006-05-22
I have personally found it easier to upgrade, it allows you to keep most of what you have done on Breezy.

---

### Post by nanotube on 2006-05-22
well, the easiest would probably be to wait until dapper is released, and then the option to upgrade to dapper will appear in your update manager.
if you really don't want to wait, this ubuntu wiki page shows how to do it:
[https://wiki.ubuntu.com/DapperUpgrades?highlight=%28upgrade%29](https://wiki.ubuntu.com/DapperUpgrades?highlight=%28upgrade%29)

aysiu's link shows another way that also works.

at any rate, make sure to back stuff up. it's always good practice to do that before doing major things to your system. :)

---

### Post by Clay85 on 2006-05-22
Upgraded from Breezy to Dapper and it was a breeze, thanks for pointing me in the right direction! :D

There were a couple errors. I saw the word failed once, but the screen scrolled by too quickly to read. I haven't noticed anything bad happening yet. Is there a logfile of the installation that I can skim through?

---

### Post by Sef on 2006-05-23
> There were a couple errors. I saw the word failed once, but the screen scrolled by too quickly to read. I haven't noticed anything bad happening yet. Is there a logfile of the installation that I can skim through?

System > Administration > System Log

---

### Post by confused57 on 2006-05-23
I'm considering upgrading also, I was wondering which method you used:

Aysiu's psychocats method or the Wiki method?

Thanks

---

### Post by Sef on 2006-05-23
**Back up** your data before any upgrades.

Download and burn a iso of Dapper, if you do a clean insall or a dist-upgrade.

A clean install is the least problematic way to upgrade.  Though after you have to reinstall the codecs, application settings, etc.

A dist-upgrade keeps your settings though it is more likely to not work afterwards than a clean install.

Any other way should not be done as the system is likely to break.

---

### Post by sophtpaw on 2006-05-23
[QUOTE=confused57]I'm considering upgrading also, I was wondering which method you used:

Aysiu's psychocats method or the Wiki method?

Thanks[/QUOTE]

I recommend a little more patience, yes, a little more...
Like you, when i want something, i want it yesterday. God, knows i'm itching to get Dapper on my system...BUT, unless you really know your way around computers, what if something happens? It can. I know for alot of people Dapper is already working fine. But there have been threads of people having problems with Dapper still, i.e partitioning etc

Just hang in there a few days, and wait for the final and full release - much safer. Even then i shall be waiting a few days for the dust to settle.

As exciting as a fresh install of the latest version can be the opposite is equally true. 
Regretting installing can be real aweful...

---

### Post by confused57 on 2006-05-23
[QUOTE=sophtpaw]I recommend a little more patience, yes, a little more...
Like you, when i want something, i want it yesterday. God, knows i'm itching to get Dapper on my system...BUT, unless you really know your way around computers, what if something happens? It can. I know for alot of people Dapper is already working fine. But there have been threads of people having problems with Dapper still, i.e partitioning etc

Just hang in there a few days, and wait for the final and full release - much safer. Even then i shall be waiting a few days for the dust to settle.

As exciting as a fresh install of the latest version can be the opposite is equally true. 
Regretting installing can be real aweful...[/QUOTE]

Good advice...patience, patience, patience...Thanks for reminding me.

---


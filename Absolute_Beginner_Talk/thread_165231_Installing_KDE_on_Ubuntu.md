---
title: "Installing KDE on Ubuntu"
date: 2006-04-24
forum: Absolute Beginner Talk
---

### Post by SteveRwanda on 2006-04-24
I have installed Ubuntu breezy, and want to add KDE 3.5.2. I'm wondering if there's any way to do this without access to the internet (so the usual apt-get commands won't work), i.e. some deb files or other that I can bring across on a USB disk?

Cheers,
Steve.

---

### Post by gingermark on 2006-04-24
I wouldn't recommend it, especially as Dapper will be released soon (you could upgrade from the install CD).

I suppose you could download all the debs found [here](http://kubuntu.org/packages/kde352/pool-breezy/) (and I'm not even sure that's all of em), copy them all into a single directory and do 'sudo dpkg -i *.deb' but I think it's likely to get very messy dependency-wise.

I'd download the final Dapper install CD when it's released, and either do a fresh install, or upgrade with that CD as the only source. Even then, I think you might end up losing GNOME, as you won't have a Dapper version of that. I'm not certain though. I guess you could always them grab a Ubuntu install cd and reinstall ubuntu-desktop from that.

At any rate, I would sit tight until Dapper. If you decide to experiment, make sure you back up any data you need that's on the same physical partition, as I wouldn't be surprised if a reinstall will be called for.

---

### Post by ossi on 2006-04-24
I guess the best way to get 3.5.2 would be to install kubuntu-desktop first and then upgrade by adding these repositories to  /etc/apt/sources.list:

# kde 3.5.2
deb [http://kubuntu.org/packages/kde352](http://kubuntu.org/packages/kde352) breezy main
deb-src [http://kubuntu.org/packages/kde352](http://kubuntu.org/packages/kde352) breezy main

However, like the guy before me I would suggest, that its probably more clever to wait about a month. Ive installed kubuntu and updated it without problems, but unless you do not have a internet connection to solve problems while updating, things become quite tricky.

---

### Post by Sokraates on 2006-04-24
I'm using KDE 3.5.2 in Breezy and Dapper and haven't noticed any changes, which would make it necessary to install 3.5.2 ASAP (on Breezy, that is).

If you have no other choice, then to download the files, better wait for Dapper to be released. Unless you desperately need something, that has been introduced/changed in KDE 3.5.2. Is there anything special you need KDE 3.5.2 for?

Appart from that, some KDE 3.5.2 apps have already been included in the regular repositories as well.

---

### Post by SteveRwanda on 2006-04-24
The main reason I need 3.5.2 is that I'm working on the localisation project for the Kinyarwanda language, and there's a strange feature that items in the main KDE menu are got from .desktop and .directory files rather than from gettext po files as most of KDE is. These are transferred over on the KDE server using some script which pulls out "Name=xxxx" type strings from .po files and puts them into the .desktop file as "[rw]=xxxx". Older versions of KDE won't have the relevant files updated but 3.5.2 does and it's a pain for me to try and do it all at my end.

We were hoping to start using this stuff in earnest from the beginning of May so it would be a pain to have to wait another month, but I do see how it would be better to use Dapper...

Steve.

---

### Post by Sokraates on 2006-04-24
It won't be better when using Dapper. It will only be easier to update to KDE 3.6.2 without an internet-connection, since Dapper-CDs will include KDE 3.5.2.

A possible solution would be to update your system without applying the updates. Then you see, which packages will be installed and you can burn those to a cd.

---


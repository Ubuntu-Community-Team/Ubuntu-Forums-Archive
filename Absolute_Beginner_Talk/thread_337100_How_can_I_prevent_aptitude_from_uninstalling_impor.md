---
title: "How can I prevent aptitude from uninstalling important program (rtorrent)?"
date: 2007-01-12
forum: Absolute Beginner Talk
---

### Post by jdimas on 2007-01-12
Hi!
I installed rtorrent and libtorrent compiled from source 'cause I wanted the last versions...
I configured, built the debs and then intalled.
I prefer aptitude cause I install and uninstall a lot of programs, so I ran 
```
sudo aptitude upgrade
```
and now aptitude wants to remove rtorrent everytime I run upgrade or dist-upgrade (just rtorrent, not libtorrent). It says rtorrent is UNUSED!
Is there a way to prevent aptitude from uninstalling rtorrent everytime I upgrade the system?
apt-get and synaptic doesn't have any problem, but I don't like them pretty much...
Tried to pin the rtorrent package but it seems to have nothing to do with my problem.

Thanks in advance!

---

### Post by orb9220 on 2007-01-12
I think it is called pinning in synaptic. Go to synaptic and find installed programs look for yours and it is either in the menu or a righ-click option to pin version.

I am pretty sure that's is what it is for.
Search forums on pinning for more info.

---

### Post by jdimas on 2007-01-13
Thanks, but I still didn't solve my problem...
And pinning is for apt-get, aptitude and synaptic (confirmed by me later).

There was a newer version of wine on the repositories, so I made a test: I pinned the wine package to stay on version 0.9.28, and ran "upgrade" on synaptic, apt-get and aptitude. The result was the same: as the package was pinned, these tools didn't try to upgrade it (still, aptitude tried to remove rtorrent :mad: ).
Without pinning wine, the three package management tools tried to upgrade the wine package AND aptitude told me the rtorrent package would be removed because it was unused, just as it happened.

The only conclusion I take from this is the aptitude attempt to remove rtorrent has nothing to do with the "/etc/apt/preferences" file... I don't understand why it tries to remove just rtorrent, as fluxbox and sylpheed-claws are compiled (the same way!) here in my pc...

Thanks, and sorry for my english!

---

### Post by Tomosaur on 2007-01-13
Could you not just let it remove it, then reinstall it? One possibility is that it's talking about the actual .deb package of rtorrent. If you compiled rtorrent from elsewhere, and used sudo make install, then this would have overwritten the files of the original rtorrent .deb package. It'll do no harm to just let it do what it wants to do, you can always reinstall.

---

### Post by neoflight on 2007-02-06
it happens because aptitude thinks that those applications are not what you wanted... may be installed by apt-get/ compiled/deb ?

```
aptitude keep-all
``` before you use aptitude... then use the command and it wont take ur things away....

---


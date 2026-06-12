---
title: "geforce 6600 PCIe in Feisty"
date: 2007-05-26
forum: Absolute Beginner Talk
---

### Post by ViceAdmiralBondo on 2007-05-26
I can't get the 8600 to work, so I shelved it until the drivers are released.  In the meantime, I installed an old 6600, and guess what, there are problems again.

I'm running Feisty on an AMD Athlon 64 3800 dual core with 1 gig of RAM in dual channel mode.  The card is PCI Express.

My first thought was to use the restricted drivers manager.  It recognizes the card just fine, but it gives me this error if I try to enable the card:

E: Type '&#8220;deb' is not known on line 44 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

I don't speak Linux yet, so that is gibberish to me.  Assistance would be appreciated.  This is a fresh install of Ubuntu with all the updates applied to it.

---

### Post by DSn0wMan on 2007-05-26
It is basically complaining about your list of repositories. There must be an error in there somewhere.

You can find a good example of how to edit your sources.list here:

[http://psychocats.net/ubuntu/sources#feisty](http://psychocats.net/ubuntu/sources#feisty)

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_extra_repositories)

---


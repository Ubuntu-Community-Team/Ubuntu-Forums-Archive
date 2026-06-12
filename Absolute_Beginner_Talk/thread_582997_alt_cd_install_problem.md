---
title: "alt cd install problem"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by cjnkns on 2007-10-20
I am upgrading to the gibbon via alternate cd, but in the process of the upgrade I get an error 

Something to do with Failed to Fetch http:/medibunto.sos-sts.com/repo/dists/feistyfawn/free/binaray blah blah blah there are like 4 lines related to the same thing? What's this about?

---

### Post by PPAAUULL on 2007-10-20
That means that it failed to get something from the server that it needs to upgrade your system.

---

### Post by mikeyphi on 2007-10-20
> **cjnkns said:**
> I am upgrading to the gibbon via alternate cd, but in the process of the upgrade I get an error 

Something to do with Failed to Fetch http:/medibunto.sos-sts.com/repo/dists/feistyfawn/free/binaray blah blah blah there are like 4 lines related to the same thing? What's this about?

You've probably got some software from medibuntu and perhaps there are no 'Gutsy' equivalents yet?
Or it may be that the medibuntu source needs changing manually - but that would have to be done after the upgrade procedure.

---

### Post by cjnkns on 2007-10-20
Any suggestions on how to get around this?
I thought maybe I could just comment out those lines in the sources list but i don't want to mess anything up that way.

---

### Post by Sef on 2007-10-20
> Any suggestions on how to get around this?
I thought maybe I could just comment out those lines in the sources list but i don't want to mess anything up that way. 

That is exactly what is needed to be done.

---

### Post by nemarona on 2007-10-20
Installing Medibuntu repos via the official method (i.e. as given in [https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)) does not add any new line to the existing sources.list, but rather creates a new directory inside /etc/apt, called sources.list.d, where it puts a file medibuntu.list with the lines

## Medibuntu - Ubuntu 7.04 "feisty fawn"
## Please report any bug on [https://launchpad.net/products/medibuntu/+bugs](https://launchpad.net/products/medibuntu/+bugs)
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) feisty free non-free

I'm also planning on updating to gutsy, and guess the easiest thing to do would be to just remove this sources.list.d directory, upgrade, and then add the Medibuntu gutsy repos from scratch.

---


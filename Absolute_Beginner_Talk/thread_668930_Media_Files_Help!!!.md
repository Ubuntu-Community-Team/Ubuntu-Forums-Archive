---
title: "Media Files Help!!!"
date: 2008-01-15
forum: Absolute Beginner Talk
---

### Post by kolva on 2008-01-15
Alright.. i just reformatted from windows vista about 3 hours ago, after backing up all my downloaded divx and xvid movies, then i find out that i can't play them in linux without downloading some codecs... only problem is.. the computer ubuntu is installed on cannot connect to the internet.. so is there a way i could download a media player or codec from my other computer(this one) and install it on the ubuntu compy???

any help would be greatly appreciated.

---

### Post by nikoPSK on 2008-01-15
yes, grab the gstreamer debs on another pc and bring them over. :)

---

### Post by JoshuaRL on 2008-01-15
I've also heard that APT-on-CD is a really great and easy way to load programs, librarys, and codecs without the internet.

This post seems familiar somehow nikoPSK.

---

### Post by mikewhatever on 2008-01-16
> **kolva said:**
> ... so is there a way i could download a media player or codec from my other computer(this one) and install it on the ubuntu compy???

any help would be greatly appreciated.

Not without solving the dependencies manually. I would install Linux-Mint in your place.

---

### Post by JoshuaRL on 2008-01-16
> **mikewhatever said:**
> Not without solving the dependencies manually. I would install Linux-Mint in your place.

I don't know about that man.  I would try to install the ubuntu-restricted-formats package, as well as the xine extra codecs and either put the debs onto a CD or put it on APT-on-CD.  Either one of those should solve all the dependencies, since they are APT and .debs.

---

### Post by mikewhatever on 2008-01-16
> **JoshuaRL said:**
> I don't know about that man.  I would try to install the ubuntu-restricted-formats package, as well as the xine extra codecs and either put the debs onto a CD or put it on APT-on-CD.  Either one of those should solve all the dependencies, since they are APT and .debs.

You may know better. It would be good to know something can solve dependencies for off-line installation. ubuntu-restricted-formats is a package that pulls in some other packages, but one would need internet to download them.

---

### Post by ugm6hr on 2008-01-16
I would advise trying this first: [http://nonetdebs.homeip.net/](http://nonetdebs.homeip.net/)
Explained here: [http://ubuntuforums.org/showthread.php?t=572819](http://ubuntuforums.org/showthread.php?t=572819)

You should at least be able to update your Ubuntu there.

I think you are looking for win32codecs (from memory), but ubuntu-restricted extras should include it all also..

You can also use Synaptic's Download script option too - but your computer needs to be updated for that to work reliably.

---


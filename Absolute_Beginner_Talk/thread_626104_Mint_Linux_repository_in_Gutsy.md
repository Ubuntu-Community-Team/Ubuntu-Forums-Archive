---
title: "Mint Linux repository in Gutsy?"
date: 2007-11-28
forum: Absolute Beginner Talk
---

### Post by _sAm_ on 2007-11-28
Hi, I was reading on the Mint Linux page(witch are based upon Ubunut), that they are now using the same repository as Ubuntu(in Mint Linux), but they also have there own. I was wondering, would I get any trouble if I add the one from Mint into Ubuntu(Gutsy)? And they also have a site called "The Linux Mint Software Portal", much like getdeb.net Can we download and use those? 

This would bee nice if they had newer versions out(like of the Gimp) of programs then we have. 

Thanks for any answers

---

### Post by mikewhatever on 2007-11-28
> **_sAm_ said:**
> Hi, I was reading on the Mint Linux page(witch are based upon Ubunut), that they are now using the same repository as Ubuntu(in Mint Linux), but they also have there own. I was wondering, would I get any trouble if I add the one from Mint into Ubuntu(Gutsy)? And they also have a site called "The Linux Mint Software Portal", much like getdeb.net Can we download and use those? 

This would bee nice if they had newer versions out(like of the Gimp) of programs then we have. 

Thanks for any answers

Linux Mint has so far been compatible with Ubuntu repositories. It's not that they started just now. That does not mean they can not add their own stuff, hence the need of other repositories. I doubt adding them to Ubuntu is a good idea, as well as using Mint installers, but why don't you try.

---

### Post by laidback on 2007-11-28
It is my understanding that each Ubuntu release is designed to work with certain versions of the apps software. Ugrades come with new releases of Ubuntu rather than as one off upgrades to a specific app. I would be careful when considering a third party upgrade.

---

### Post by _sAm_ on 2007-11-28
> but why don't you try.
Cus I dont want to brake the system, tired of that:-D I was just wondering, guess I will leave it with that.

Thanks for your help

---

### Post by scorp123 on 2007-11-28
> **_sAm_ said:**
>  Hi, I was reading on the Mint Linux page(witch are based upon Ubunut), that they are now using the same repository as Ubuntu(in Mint Linux), but they also have there own.  Mint is based on Ubuntu just as Ubuntu is based on Debian. Some stuff is the same. Lots of other stuff is different now. If you mix the two it might work ... or it might not. In any case you're asking for trouble.

> **_sAm_ said:**
>   I was wondering, would I get any trouble if I add the one from Mint into Ubuntu(Gutsy)?  Yes. "clem" (the creator of Mint) uses his own library versions in some places. Chances are you might have odd situations where two packages which are both available from the Ubuntu and the Mint repos will try to overwrite each other.

> **_sAm_ said:**
>   And they also have a site called "The Linux Mint Software Portal", much like getdeb.net Not true. "Getdeb.net" and the "Mint Software Portal" are very different things. Getdeb.net offers standard *.deb packages which are easily installed via standard commands such as "dpkg". Mint's software portal uses *.mint packages which are in fact archive files (I think "cpio" format?) with an embedded installer script that will alter your sources.list behind your back and then download things for you. From that point of view it seems to have some similarities with "Automatix" which the admins here don't like at all because it tends to break a lot of stuff and may render a user's system unusable. I remember several postings back on the Mint forum where people all of a sudden had odd entries in their sources.list ... apparently left behind by *.mint package installations.
 
I personally can't tell how stable stuff from the "Mint" software portal is (I personally have never used it; I clearly prefer to handle packages via "apt"), but I guess you'd be running into lots of troubles if you try to run those packages on Ubuntu. So I don't recommend doing this.

And yes, I am the same "scorp123" as on the Mint forums. :lolflag:

---

### Post by _sAm_ on 2007-11-28
Thanks scorp123, I will stay clear. And thanks for the correction, I didn't know.

---

### Post by tgalati4 on 2007-11-28
Take a spare machine (or disk drive) and install Mint.  You may be impressed.

---

### Post by scorp123 on 2007-11-28
> **_sAm_ said:**
> Thanks scorp123, I will stay clear. And thanks for the correction, I didn't know. See tgalati4's posting above mine. If you want to try out those features the best thing would be to use a separate machine and try Mint ... and then decide what you like better: Mint, Ubuntu ... or something else.

Just don't mix them ... :-D

---

### Post by dpar on 2007-11-28
Thanks for that info on the Software Portal, Scorp, I didn't realize that.

---

### Post by bodhi.zazen on 2007-11-28
Just an informational posting :

You can run a mixed system, but you should understand pinnning

		[http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html#s-default-version](http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html#s-default-version)

		[http://jaqque.sbih.org/kplug/apt-pinning.html](http://jaqque.sbih.org/kplug/apt-pinning.html)

Yes, this can cause system breakage, so if you do this install only specific apps from the mint repos, do not "sudo apt-get update && sudo apt-get upgrade" a mixed system.

---


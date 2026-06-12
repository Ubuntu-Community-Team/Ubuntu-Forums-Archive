---
title: "apt-get or aptitude?"
date: 2006-12-02
forum: Absolute Beginner Talk
---

### Post by drito on 2006-12-02
What is the diference between sudo apt-get install and sudo aptitude install?

---

### Post by angkor on 2006-12-02
[http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)

---

### Post by Sef on 2006-12-02
aptitude is an better than apt-get.  Aptitude will remove all dependencies if you uninstall, having installed through it.   Apt-get will leave dependcies behind if you uninstall.

---

### Post by msak007 on 2006-12-02
> **Sef said:**
> aptitude is an better than apt-get.  Aptitude will remove all dependencies if you uninstall, having installed through it.   Apt-get will leave dependcies behind if you uninstall.
I still use aptitude, but a new apt-get feature called *autoremove* was implemented in Edgy. When you uninstall something using apt-get and it leaves behind dependencies, you are warned of these leftover dependencies and advised to run ```
sudo apt-get autoremove
``` to remove them. I haven't done extensive testing comparing the 2, but I have used autoremove and it seems to do a pretty good job. However, like I said I still use aptitude - just sticking with what I know works.

---

### Post by aysiu on 2006-12-02
msak007 is correct, but I still advise using *aptitude* because a lot of people are using Dapper at this point and haven't upgraded to Edgy.

By the way, I've also updated the *aptitude* page on Psychocats to reflect this change in *apt-get*'s abilities.

---

### Post by turbojugend_gr on 2006-12-02
I 'll second the benefits of attitude, but I 'll also need to inform you of sth.

It's just that, I always (breezy, dapper, edgy) end up with broken repos for aptitude, somehow apt-get never has an issue...??? I guess it is just sth I always do wrong with aptitude, but still this doesn't change the fact apt-get seems more stable to me.

And here comes the question (maybe aysiu can answer this, since he's been the one having the tolerance to answer such stupid questions all over..;)): How come since aptitude is said to be better (exept for my pc...) Synaptic is using apt-get backend? After all there are to many complaints, about synaptic not really unistalling stuff...

---

### Post by aysiu on 2006-12-02
I've never experienced the broken repo problem with *aptitude*, but I have experienced *aptitude* trying to be too "smart" and removing a whole bunch of packages that are seemingly unrelated to the package I wanted to remove--in those cases, I use *apt-get*.

And I have no idea why Synaptic isn't a frontend for *aptitude*.

---

### Post by msak007 on 2006-12-02
> **turbojugend_gr said:**
> It's just that, I always (breezy, dapper, edgy) end up with broken repos for aptitude, somehow apt-get never has an issue...??? I guess it is just sth I always do wrong with aptitude, but still this doesn't change the fact apt-get seems more stable to me.I've never had issues with broken repos using aptitude, but occasionally I do have a problem uninstalling or updating software because it does a check to see how bad it *may* break your system, and gives you a point value (usually negative lol) to tell you that you shouldn't do what you want. When I run into those instances and I know for a fact I know what I'm doing, I usually end up using apt to forgo the warnings and possible broken packages.

And aysiu, I still recommend aptitude as well and made sure to note that autoremove was only a feature in Edgy. But I'm also puzzled why, with the obvious benefits of aptitude, Synaptic and Adept have not been made front-ends for it instead of apt-get.

---

### Post by az on 2006-12-02
Apt-get is older and more used than aptitude.  Apt-get has more hooks and can better serve as a backend than aptitude AFAIK.

It is also important to mention that you can safely use either one to install packages - they both do the same thing.  You will not bork your system by installing a package with one of those tools rather than another.

---

### Post by turbojugend_gr on 2006-12-03
I c. Not what I looked for, but since that's the main reason... wat the heck!

Thank you azz, TJ.

---


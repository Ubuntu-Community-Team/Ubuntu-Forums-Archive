---
title: "Apt-get vs Aptitude"
date: 2007-04-16
forum: Absolute Beginner Talk
---

### Post by chris062689 on 2007-04-16
I heard that using apt-get remove (package name) leaves things on the system after you install, and that apptitude cleans everything up for you.

Is this true?  So which one is better to use to keep a tidy system?
Which does Add / Remove Programs (Package Manager) use?

---

### Post by Happy_Man on 2007-04-16
Apt-get will not uninstall dependencies along with a program, whereas aptitude will.

Aptitude is usually recommended, but I think the pachage manager uses apt-get.

---

### Post by Pikestaff on 2007-04-16
I would use Aptitude whenever possible: [http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)

---

### Post by chris062689 on 2007-04-16
I hear in the new package manager with Ubuntu 7.04 that you will be able to pull up a list of all un-used dependencies (which would be called "orphan packages?") and be able to uninstall those?

---

### Post by aysiu on 2007-04-16
I think *apt-get autoremove* is a little more conservative than *aptitude remove*, but then again sometimes *aptitude* is a little overzealous and wants to uninstall just about everything.

I used to be a strong advocate for *aptitude*, but now I use *apt-get* almost exclusively.

---

### Post by Paul41 on 2007-04-16
> **aysiu said:**
> I think *apt-get autoremove* is a little more conservative than *aptitude remove*, but then again sometimes *aptitude* is a little overzealous and wants to uninstall just about everything.

I used to be a strong advocate for *aptitude*, but now I use *apt-get* almost exclusively.

What made you start using apt-get. Is it just that aptitude can be "a little overzealous"?

---

### Post by aysiu on 2007-04-16
With the advent of *autoremove*, *apt-get* suits my purposes just fine. And, yes, *aptitude* is sometimes too smart for its own good.

---

### Post by mcduck on 2007-04-16
> **chris062689 said:**
> I hear in the new package manager with Ubuntu 7.04 that you will be able to pull up a list of all un-used dependencies (which would be called "orphan packages?") and be able to uninstall those?
You can do that in any Ubuntu version, just instal deborphan and then create a new filter in Synaptic to list only orphaned packages.

Also, since Edgy, apt-get and Synaptic have 'autoremove' function to remove packages installed as dependencies.

Like aysiu said, aptitude might keep your system clean with a bit less effort than doing the same thing with apt-get/Synaptic, but sometimes aptitude might act a bit strange and try to remove too many of your packages.. It's happened to me couple of times and then I decided to just use apt-get and check the orphaned/autoremovable packages every now and then myself. I rather use a tool I can trust not to uninstall half my system for no reason ;)

---


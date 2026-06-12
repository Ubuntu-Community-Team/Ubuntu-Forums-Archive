---
title: "Will aptitude keep you out of dependancy hell?"
date: 2006-09-12
forum: Absolute Beginner Talk
---

### Post by tobmeister on 2006-09-12
He all,

If I install an app using aptitude, will it search for all aplicable dependancies that I need to properly operate the app?

Thanks

Tobmeister

---

### Post by jordanmthomas on 2006-09-12
Yes, it will get the dependencies and install them for you.
In my experience, apt isn't near as prone to dependency hell as rpm is.

---

### Post by jimmygoon on 2006-09-12
> **tobmeister said:**
> He all,

If I install an app using aptitude, will it search for all aplicable dependancies that I need to properly operate the app?

Thanks

Tobmeister

um... apt-get is the same difference... what are you having problems with that makes you imagine "dependency hell"?

---

### Post by Anduu on 2006-09-12
> **jimmygoon said:**
> um... apt-get is the same difference... what are you having problems with that makes you imagine "dependency hell"?

Yup...if you are installing an app from ubuntus official repos you should have no problems whatsoever with dependencies.

On the other hand if you are using unofficial repos all bets are off.

---

### Post by aysiu on 2006-09-12
*apt-get* and *aptitude* and Adept and Synaptic will **all** fetch dependencies for you.

The only time you'll run into "dependency hell" is when you've enabled too many and/or conflicting repositories.

You can find a nice, safe sources.list here:
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

---


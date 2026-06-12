---
title: "aptitude -- how to alter Recommends  from being installed"
date: 2006-08-30
forum: Absolute Beginner Talk
---

### Post by kkruecke on 2006-08-30
I am about to install a package that will also cause a mail server to be installed because it is in the Recommends list. How to I tell aptitude that I want a different mail server package installed? Is there a way to prevent it, at least this one time, from also installing the Recommends packages along with the main package?

thanks.

---

### Post by Metacarpal on 2006-08-30
It should ask you, "Accept this solution?"
Tell it no.  It'll offer another solution.  Keep doing it until aptitude offers to install the program you want without the one you don't.

---

### Post by kkruecke on 2006-08-30
Is there a way to tell the aptitude full screen version to just plain not install a Recommends package--like M and m?
I think I going to just use apt-get to do the install because it won't install the Recommends packages.

---

### Post by bodhi.zazen on 2006-08-30
> **kkruecke said:**
> Is there a way to tell the aptitude full screen version to just plain not install a Recommends package--like M and m?
I think I going to just use apt-get to do the install because it won't install the Recommends packages.

```
aptitude  --without-recommends install <package_name>
```

---

### Post by kkruecke on 2006-08-30
Thanks!

---

### Post by Metacarpal on 2006-08-30
> **bodhi.zazen said:**
> ```
aptitude  --without-recommends install <package_name>
```

That is so much better than what I said.

And now I learned something, too! :)

---

### Post by kkruecke on 2006-08-30
I knew you could change the aptitude configuration file to make it always keep the Recommends packages by adding

Aptitude::Keep-Recommends "true"

but I didn't know about the command line --without-recommends.

---


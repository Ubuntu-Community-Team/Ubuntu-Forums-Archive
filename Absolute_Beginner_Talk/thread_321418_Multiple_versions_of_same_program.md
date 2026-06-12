---
title: "Multiple versions of same program"
date: 2006-12-18
forum: Absolute Beginner Talk
---

### Post by sumithar on 2006-12-18
In windows when I install a program (say firefox) it will ask me which directory I want to install in.  This enables to have multiple versions of same program.  I was running FF 1.5 and FF 2.0 Beta at the same time- I had different icons.
Is this possible in Ubuntu?

When I install an app either using Synaptic or by using the instructions to extract the tar or gzip or whatever it doesn't prompt me where it will be installed.  

Just wondering if it can be done..

---

### Post by aysiu on 2006-12-18
Sure.

For example, if you install Firefox 1.5 via Synaptic in Ubuntu Dapper, that will be one version of Firefox. If you then install Firefox 2.0 using [this script](http://www.psychocats.net/ubuntu/firefox), you can launch Firefox 1.5 with the command ```
firefox.ubuntu
``` and launch Firefox 2.0 with the command ```
firefox
```

---

### Post by sumithar on 2006-12-19
> **aysiu said:**
> Sure.

For example, if you install Firefox 1.5 via Synaptic in Ubuntu Dapper, that will be one version of Firefox. If you then install Firefox 2.0 using [this script](http://www.psychocats.net/ubuntu/firefox), you can launch Firefox 1.5 with the command ```
firefox.ubuntu
``` and launch Firefox 2.0 with the command ```
firefox
```

Thanks.  I was using FF only as an example.  My question was more geared towards, whether you can control which directory(ies) the program is installed in.

For instance in your illustration, where do the two different executables go?  Does one go into /usr/bin and another into, say, /usr/local/bin?

I am sorry if my windows analogies are inapt, but I have been using DOS/Windows for 15 years now, so can't help it ;-)

---

### Post by aysiu on 2006-12-19
If you're using the package manager, then, no--you won't control what directories the packages get installed to. The package manager is... managing that.

If you install from a .tar.gz that's a precompiled binary (like Firefox or Songbird or FirstClass or Google Earth), you can install it in whatever directory you want.

---


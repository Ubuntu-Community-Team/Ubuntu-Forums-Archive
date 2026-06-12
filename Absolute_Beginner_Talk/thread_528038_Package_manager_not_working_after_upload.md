---
title: "Package manager not working after upload"
date: 2007-08-17
forum: Absolute Beginner Talk
---

### Post by Otpadnik on 2007-08-17
Hi,

I need a help.

Two days ago I've done automatic update of system with installed Feisty.
But as it took incredible long time, I've restarted system, and again after trying 

```
sudo dpkg --configure -a 
```

I get this oputput:

```
Reading package info from "/usr/lib/haskell-packages/ghc6/lib/gtk-0.9.10.5/gtk.package.conf"...done.
building GHCi library //usr/lib/haskell-packages/ghc6/lib/gtk-0.9.10.5/HSgtk.o
```

And it just stands there... For a very long time (over night and still nothing).
And CPU usage is around 5%, but swap space and RAM are both aroung 95% usage (I've got 256MB RAM installed)...

So, I don't know if it is that I have too little RAM memory or something else?
Should I wait longer?

Thanks,
Otpadnik

---

### Post by overdrank on 2007-08-17
> **Otpadnik said:**
> Hi,

I need a help.

Two days ago I've done automatic update of system with installed Feisty.
But as it took incredible long time, I've restarted system, and again after trying 

```
sudo dpkg --configure -a 
```

I get this oputput:

```
Reading package info from "/usr/lib/haskell-packages/ghc6/lib/gtk-0.9.10.5/gtk.package.conf"...done.
building GHCi library //usr/lib/haskell-packages/ghc6/lib/gtk-0.9.10.5/HSgtk.o
```

And it just stands there... For a very long time (over night and still nothing).
And CPU usage is around 5%, but swap space and RAM are both aroung 95% usage (I've got 256MB RAM installed)...

So, I don't know if it is that I have too little RAM memory or something else?
Should I wait longer?

Thanks,
Otpadnik

HI this is just a thought, maybe go to synaptic manager and see if you have any broken packages, under edit, fix broken packages. Then reload.

---

### Post by Otpadnik on 2007-08-17
Hi,
Thanks for your reply!

Unfortunately, when I start package manager it tells me that I do have broken packages and that I should type sudo dpkg...
And also 
```
E:_cache->open() failed, please report
```

Any more ideas?
I could always try fresh install, but I'm rather interested in this.

And one more thing, before this update on boot time I could choose WinXP or ubuntu 2.6.20-15, and now I have both 2.6.20-16 and 2.6.20-15?

Thanks,
Otpadnik

---


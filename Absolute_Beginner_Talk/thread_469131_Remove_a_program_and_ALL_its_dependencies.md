---
title: "Remove a program and ALL its dependencies"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by tL0z on 2007-06-09
Hello,

I've installed Amarok but I no longer want it. How can I remove it and ALL the dependencies it installed (22 I think)?

Thanks

---

### Post by zvacet on 2007-06-09
You can do it with Adept if you mark package for** complete removal** or 

```
sudo apt-get --purge remove Amarok
```

---

### Post by CyberCr33p on 2007-06-10
After you remove the package do:

```

sudo apt-get autoremove

```

That command will remove packages that you don't need.

---

### Post by forestpixie on 2007-06-10
If you use autoremove you could end up with some problems - I have, for instance, installed openoffice from the openoffice site as opposed to from the one in the repos. sudo apt-get autoremove thinks it should get rid of my openoffice.

This person ended up with a LONG list of software to autoremove 
[http://ubuntuforums.org/showthread.php?t=465903](http://ubuntuforums.org/showthread.php?t=465903)

Just be careful and read what you're being prompted to remove.

:)

---

### Post by mcduck on 2007-06-10
> **forestpixie said:**
> If you use autoremove you could end up with some problems - I have, for instance, installed openoffice from the openoffice site as opposed to from the one in the repos. sudo apt-get autoremove thinks it should get rid of my openoffice.

This person ended up with a LONG list of software to autoremove 
[http://ubuntuforums.org/showthread.php?t=465903](http://ubuntuforums.org/showthread.php?t=465903)

Just be careful and read what you're being prompted to remove.

:)
The best way is to just use Synaptic to uninstall autoremovable packages. This way you can select which ones you wish to remove and which to keep..

---

### Post by forestpixie on 2007-06-10
LOL 

Yes I know was just giving tl0z a 'be careful' and example of what it could do.

---


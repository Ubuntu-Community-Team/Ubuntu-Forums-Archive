---
title: "Compiz advanced settings problem"
date: 2008-04-04
forum: Absolute Beginner Talk
---

### Post by Luffer on 2008-04-04
I have got some effects working after going to System->Preferences->Appearance->Visual Effects->Extra

But looking at this guide guide:

[http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion](http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion)

I should be able to run ccsm but it tells me:

```

The program 'ccsm' is currently not installed.  You can install it by typing:
sudo apt-get install compizconfig-settings-manager
bash: ccsm: command not found
```

I've tried that but keep getting this error:

```
james@james-laptop:~$ sudo apt-get install compiz compizconfig-settings-manager
Reading package lists... Done
Building dependency tree       
Reading state information... Done
compiz is already the newest version.
E: Couldn't find package compizconfig-settings-manager
```

As far as I know all the repositories are enabled in Synaptic, but searching it doesn't list the compizconfig-settings-manager.

Don't know what to try to get this working all the threads just tell people to install it, but I can't seem to do that.

---

### Post by talsemgeest on 2008-04-04
You can add a repo with the latest compiz and ccsm and everything compiz-related like emerald from here: [http://www.kwatrow.nl/repo/](http://www.kwatrow.nl/repo/)

Hope this helps :)

---


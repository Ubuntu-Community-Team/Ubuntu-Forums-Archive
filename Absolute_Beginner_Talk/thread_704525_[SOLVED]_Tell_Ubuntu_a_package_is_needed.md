---
title: "[SOLVED] Tell Ubuntu a package is needed?"
date: 2008-02-22
forum: Absolute Beginner Talk
---

### Post by nowhere@cox.net on 2008-02-22
Is there a way to manually flag a package as "needed" so that when I run 

```
sudo apt-get autoremove
``` 

it doesn't remove the packages that I need? An example is nspluginwrapper.  I had to install the flash plugin with a special script on my 64bit system and autoremove wants to remove this package. If I let it, it breaks flash and I have to reinstall flash.  I have tried out and removed a lot of software and so there are a lot of packages that don't seem to be needed.

This does, however,  beg another newbie question though. If one package is not flagged as needed, how many other ones are and how do I tell which ones?

Thanks,
Eric

---

### Post by kwilliam on 2008-02-22
To remove a package from apt's autoremove list, just install it.
```
$ sudo apt-get install nspluginwrapper
```
It'll say the package is already installed blaw blaw blaw.  But that flags it as being manually installed (or as you say, "needed").

As for other packages not being flagged as needed, probably as long as they're stuff that was installed the "normal" way via the apt packaging system, it should be safe to remove them.  If you've installed lots of stuff from scripts or Automatix or something, I would copy and paste the list of packages in the auto-remove list in a text file and save it as a backup, let apt remove them, and then if something gets broken, reinstall the packages by copying and pasting from the backup file.

Note: meta-packages cause some problems.  For instance, if you install "kde-games" and then uninstall a single game, the meta-package "kde-games" is removed, and all the other games in that package are marked as "automatically installed and no longer needed".  That is a problem, and hopefully they'll figure out a solution?

---

### Post by nowhere@cox.net on 2008-02-26
Hey thanks. I should have thought of that. So simple. I like it!

Eric

---


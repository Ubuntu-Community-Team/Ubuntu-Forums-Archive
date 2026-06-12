---
title: "[SOLVED] About removing Compiz Fusion in 7.04"
date: 2007-10-03
forum: Absolute Beginner Talk
---

### Post by Wikzo on 2007-10-03
Hi

I got Compiz Fusion up and running on my Ubuntu 7.04. I want to upgrade when 7.10 is released, and I have been told, that I should remove Compiz Fusion before upgrading to the next Ubuntu version.

I have installed it via this guide:
[http://news.softpedia.com/news/How-to-Install-Compiz-Fusion-on-Ubuntu-58113.shtml](http://news.softpedia.com/news/How-to-Install-Compiz-Fusion-on-Ubuntu-58113.shtml)

How **exactly** do I remove everything about Compiz Fusion? If I make a search "Compiz Fusion" in Synaptic I get a lot of files.

Which one do I have to delete?

If I try to remove the "Compiz" package, it tells me, that both "ubuntu-desktop" and "desktop-effects" will be removed too.

---

### Post by ThrobbingBrain66 on 2007-10-03
Just uninstall all the packages that you were told to install in the guide.  It may want to uninstall ubuntu-desktop and a few other packages, but just let it.  ubuntu-desktop is just a meta-package...it won't actually remove anything you absolutely need (it just sounds dangerous :)).

Then reinstall ubuntu-desktop and it'll bring back any missing dependencies.  After that, you should be all set to upgrade to 7.10

---

### Post by Wikzo on 2007-10-04
Will it be correct to remove these form Synaptic:

**compiz-core**
compiz
compiz-fusion-plugins-extra
compiz-fusion-plugins-main
compiz-plugins
compizconfig-settings-manager
desktop-effects
ubuntu-desktop
compiz-gnome
libdecoration0
libcompizconfig-backend-gconf
python-compizconfig

... or do I need to remove more/less files than that?

Also, does it matter that "compiz-core" is the only file that gonna be COMPLETELY removed and the other ones just removed?

---

### Post by ThrobbingBrain66 on 2007-10-04
That looks to be all the files you'll need to remove (I added emerald to the command below, just in case).

Open a terminal:
```
sudo apt-get remove --purge compiz-core compiz compiz-fusion-plugins-extra compiz-fusion-plugins-main compiz-plugins compizconfig-settings-manager desktop-effects ubuntu-desktop compiz-gnome libdecoration0 libcompizconfig-backend-gconf python-compizconfig emerald
```

That will completely remove everything compiz related.  Then:
```
sudo apt-get install ubuntu-desktop
```

This will reinstall the official Ubuntu compiz packages and any other missing dependencies.  Also, make sure to remove any 3rd-party repos from your sources.list file before you upgrade as well.

---

### Post by Wikzo on 2007-10-04
Thank you. I'll do that some days before Gusty Gibbons is released :)

---

### Post by Wikzo on 2007-10-05
"sudo apt-get install ubuntu-desktop"  tells me, that it will also install this:

compiz compiz-core compiz-gnome compiz-gtk compiz-plugins desktop-effects
  libdecoration0

I have removed my 3. part software lists and made a refresh. I don't want to install the Compiz all over again - just want the ubunu-desktop (so I can make distribution upgrade).

**EDIT:** Just forget about it. I have been told, that these files is default in Ubuntu 7.04 :)

---


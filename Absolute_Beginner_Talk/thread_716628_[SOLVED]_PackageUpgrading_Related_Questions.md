---
title: "[SOLVED] Package/Upgrading Related Questions"
date: 2008-03-06
forum: Absolute Beginner Talk
---

### Post by frosticle on 2008-03-06
Hello,

The problem that I am having is that I don't know how to update something without a repository. I understand the risk in using other repositories and with updated software, but I am willing to take on the risk for certain programs and to learn Ubuntu at a faster rate.

Anyway, on Windows I always loved Filezilla. With their WxWidgets, code from the ground up 3 series, I just had to try it out on Linux without Wine.  Having used 3 final on Windows, I know it lacks features and has plenty of bugs because of the new coding.

I couldn't find a repository that had the new one, though. My guess is that it has too many new dependencies to warrant using it.

Even though I only have used Linux for 2 days, I decided to take on the challenge, learn to compile and install software. So I went out and got a couple of updated programs then compiled and installed them, removing them from package manager easily. No conflicts there. I also found the WxWidgets repository on and lucked out there on a few upgrades.

Then came libgnutls. No repisotry and connected to half the files on my system. As a temporary fix, I installed it, then reinstalled the package one, which seems to have made the new one the first one checke (wouldn't work before that). Finally a clean install of Filezilla and it is working fine. I would like to go back and fix the problem though, if I could.

Is it possible to do one of the following?:

1. Install a program as an updated package, thus updating libgnutls in this case.

2. Uninstall a program without uninstalling dependencies?

3. Overwrite a program using sudo, kind of like a cheap upgrade (I doubt this would even be logical, but I don't know that much about linux).

Thanks in advance. Sorry for being a two day noob. My style is always to create a lot of havoc and learn from it. I mean I can't do any real damage because I can always reformat and I always learn faster by doing and asking where needed (When I can't google it.).

---

### Post by mikeyphi on 2008-03-06
You might try using Synaptic - it allows you to 'force' the OS to use a particular version of a package as long as you have different versions installed.
The force option is under the package drop-down menu

---

### Post by kesman on 2008-03-06
[http://packages.ubuntu.com/edgy/checkinstall](http://packages.ubuntu.com/edgy/checkinstall)

I'd suggest you to use that, it updates your compiled files as normal .deb-packages and doesn't ruin your dependecies, I think.

EDIT:
[https://help.ubuntu.com/community/CheckInstall](https://help.ubuntu.com/community/CheckInstall)
that's a better link =D

---

### Post by frosticle on 2008-03-06
> **mikeyphi said:**
> You might try using Synaptic - it allows you to 'force' the OS to use a particular version of a package as long as you have different versions installed.
The force option is under the package drop-down menu

When i was looking at that before, I was getting only the versions that were in that package manager already. Is there a way to have it check say the local area of a harddrive and have it consider these files versus packaged files?


[quote=kesman][http://packages.ubuntu.com/edgy/checkinstall](http://packages.ubuntu.com/edgy/checkinstall)

I'd suggest you to use that, it updates your compiled files as normal .deb-packages and doesn't ruin your dependecies, I think.

EDIT:
[https://help.ubuntu.com/community/CheckInstall](https://help.ubuntu.com/community/CheckInstall)
that's a better link =D[/quote]

Thanks. I was actually looking into this before, but I was unsure of one thing. Do these packages sync with current ones? I mean if I make a package of a compiled libgnutls, will it replace the one in the package manager or allow me to force it or will I end up with just another entry?

Also I read earlier, around the web, that people were recommending not to use check install because it cause problems in the package manager dealing with dependencies (Or cause the problems somewhere. I know the firsat day I installed Linux I looked at the program and people kept saying not to use it) and could cause various problems with your files. Is this true?

---

### Post by kpkeerthi on 2008-03-06
> I mean if I make a package of a compiled libgnutls, will it replace the one in the package manager or allow me to force it or will I end up with just another entry?
If you install using a deb (built using checkinstall or downloaded from somewhere) it would simply upgrade if the package (lower version) exists already. There will not be two entries in synaptic.

---

### Post by frosticle on 2008-03-06
Thanks guys.

Very helpful. Worked fine. Nice to have things in the package manager.

Thank you again.

---


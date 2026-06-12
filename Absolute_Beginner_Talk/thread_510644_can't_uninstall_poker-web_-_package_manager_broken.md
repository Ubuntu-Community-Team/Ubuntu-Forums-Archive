---
title: "can't uninstall poker-web - package manager broken - dpkg &amp; apt-get don't work"
date: 2007-07-26
forum: Absolute Beginner Talk
---

### Post by jonobo on 2007-07-26
Hi,

i've got a serious problem which i need to solve in the next 4 hours - any help appreciated ;)

A month ago or so, i tried to install "poker-web" for a friend who wanted to play poker online, i found a .deb somewhere, downloaded it and tried to install it via "dpkg -i poker-web-xyz.deb", it did not work.

Since then i can't get my automatic updates, if i try to start my synaptic-package manager i get an error message:
```

E: The package poker-web needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

```

Okay - i deleted the poker-web-xyz.deb after the unsuccesful install.

Isn't there a simple way to tell my system that it should forget about poker-web for always and ever ?

Here's a list of some things i tried:
```

root@ybox:/# dpkg -l | grep poker-web
iHR poker-web                                  1.0.32-1                             
root@ybox:/# dpkg --purge poker-web
dpkg: error processing poker-web (--purge):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 poker-web
root@ybox:/# dpkg -r poker-web
dpkg: error processing poker-web (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
Errors were encountered while processing:
 poker-web
root@ybox:/# apt-get remove --purge poker-web
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package poker-web needs to be reinstalled, but I can't find an archive for it.

```

Any ideas are welcome - i need to use my package-manager, but i absolutely don't care about poker-web ;)

I'll be on and checking for the next two hours, i absolutely need to get this done before tomorrow morning, you'll get three free virtual hugs for helping me out of the poker-web-error ;)

;j

---

### Post by jonobo on 2007-07-26
> root@ybox:/home/jobo/Desktop# dpkg -C
The following packages are in a mess due to serious problems during
installation.  They must be reinstalled for them (and any packages
that depend on them) to function properly:
 poker-web   

Okay - this machine has developed some kind of humor at least :)

Can anyone fix me ;?

---

### Post by forestpixie on 2007-07-26
try this

```
sudo dpkg --remove --force-remove-reinstreq poker-web
```

---

### Post by jonobo on 2007-07-26
Okay - after a quick "man dpkg"-scanning i suggest to myself trying this one:

remove-reinstreq: Remove a package, even if it’s broken and marked to require reinstallation. This may, for example, cause parts of the package to remain on the system, which will then be forgotten by dpkg.

Looks like a quick and dirty fix :]

---

### Post by jonobo on 2007-07-26
@forestpixie: ooooooops - you were faster ;) thank you a lot :] i'll give a try bruce-immediate-lee...

> root@ybox:/home/jobo/Desktop# dpkg --remove --force-remove-reinstreq poker-web
dpkg - warning, overriding problem because --force enabled:
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
(Reading database ... 
dpkg: serious warning: files list file for package `poker-web' missing, assuming package has no files currently installed.
133907 files and directories currently installed.)
Removing poker-web ...

Thanks - you saved my life :[]

I'm going to France in tomorrow morning in my 26year-old smurfing-van and i neeeeed some fresh packages before i leave, to make sure i have a system on board that provides what i need...

Forest for the Pixies ;!

Peace,

;j

---

### Post by forestpixie on 2007-07-26
man apt-get gives this for autoremove

          autoremove is used to remove packages that were automatically
          installed to satisfy dependencies for some package and that are no
          more needed.


try that afterwards 
```

sudo apt-get autoremove
```

but check what it thinks it's going to remove before you say yes

---

### Post by forestpixie on 2007-07-26
save journey and if you get to the coast wave to me over the channel :D

---


---
title: "update manager error"
date: 2007-09-04
forum: Absolute Beginner Talk
---

### Post by seanmbarrett on 2007-09-04
hey everyone,
    i have this error,  unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:The package kcometen3 needs to be reinstalled, but I can't find an archive for it.'

any ideas how to fix thanks sean

---

### Post by southernman on 2007-09-04
Try doing a 
```
sudo aptitude install kcometen3
```
first, if that doesn't work try...
```
sudo aptitude install -f
```

All of the above are meant to rum from a terminal window (Applications > Accessories > Terminal)

---

### Post by SOULRiDER on 2007-09-04
There doesnt seem to be a kcometen3 package in the repositories, do you remember where you got it from? Youre gonna ahev to find a deb package for it and compile it yourself, apt-get wont be able to fetch it for you.

---

### Post by seanmbarrett on 2007-09-04
hi 
just tried both of those and now i get this 
: I wasn't able to locate a file for the kcometen3 package. This might mean you need to manually fix this package. (due to missing arch)
E: Couldn't lock list directory..are you root?

i was in root i thought. any ideas, thanksfor the help. sean

---

### Post by SOULRiDER on 2007-09-04
I did a bit of googling adn there are a couple of packages here 
[http://www.kde-apps.org/content/show.php/KCometen3?content=30313](http://www.kde-apps.org/content/show.php/KCometen3?content=30313) but theya re for dapper and breezy.

If you want you can compile it from source and make a deb package for feisty or whatever youre running too:
[https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)

---

### Post by SOULRiDER on 2007-09-04
> **seanmbarrett said:**
> hi 
just tried both of those and now i get this 
: I wasn't able to locate a file for the kcometen3 package. This might mean you need to manually fix this package. (due to missing arch)
E: Couldn't lock list directory..are you root?

i was in root i thought. any ideas, thanksfor the help. sean

Did you forget to add sudo ?

---

### Post by southernman on 2007-09-04
Thanks soulrider. Obviously, I didn't take time to see if it was in the repos.

Cudos to you

---

### Post by seanmbarrett on 2007-09-04
hey all,
   it seems to be a KDE screen saver gone awry is there a away to remove it?
thanks sean

---

### Post by SOULRiDER on 2007-09-04
```
sudo aptitude remove kcometen3
```
You can also do Purge instead of remove so it removes any config files (if any)

---

### Post by seanmbarrett on 2007-09-05
i will try it, thanks for the help again. sean

---


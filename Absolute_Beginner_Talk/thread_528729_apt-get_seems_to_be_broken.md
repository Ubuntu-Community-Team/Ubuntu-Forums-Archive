---
title: "apt-get seems to be broken"
date: 2007-08-18
forum: Absolute Beginner Talk
---

### Post by SuperAndy on 2007-08-18
trying to compile pidgin from source, i get an error about not having the right c libraries installed.

so going sudo apt-get install build-essentials should work, but i get the following error from apt-get:

```

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  build-essential: Depends: libc6-dev but it is not going to be installed or
                            libc-dev
                   Depends: g++ (>= 4:4.1.1) but it is not going to be installed
E: Broken packages

```

i have tried manually installing the other packages, and i end up chasing an endless stream of dependencies. in the end i get to libc6, which is already installed.

there must be some simple way just to get apt-get to sort it all out for me, but i am at a loss of what to do.

any help would be greatly appreciated.

i have also tried sudo apt-get -f install, and nothing really happens

---

### Post by taurus on 2007-08-18
Try

```
sudo aptitude update
sudo aptitude install build-essential
gcc -v
```

---

### Post by SuperAndy on 2007-08-18
cheers, that works fine!

any reason why aptitude would work and apt-get wouldn't?

---


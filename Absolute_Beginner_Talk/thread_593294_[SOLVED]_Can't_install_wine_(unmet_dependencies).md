---
title: "[SOLVED] Can't install wine (unmet dependencies)"
date: 2007-10-27
forum: Absolute Beginner Talk
---

### Post by Brandito101 on 2007-10-27
When I type
sudo apt-get install wine

I get
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  wine: Depends: ia32-libs (>= 1.6) but it is not going to be installed
        Depends: lib32asound2 (> 1.0.14) but it is not installable
E: Broken packages

I'm also getting this error on a lot of things. I'm sure it's something simple I'm missing.

Thanks

---

### Post by Frak on 2007-10-27
run
```
sudo apt-get -f install
```

---


---
title: "libgtk2.0-dev unmet dependencies"
date: 2007-03-26
forum: Absolute Beginner Talk
---

### Post by BramKuijper on 2007-03-26
Hi all,

I tried to install gtk2.0 sources by installing libgtk2.0-dev on a Ubuntu Edgy 6.10 machine, but I get the following error:
```

 sudo apt-get install libgtk2.0-dev
Reading package lists... Done
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
  libgtk2.0-dev: Depends: libpango1.0-dev (>= 1.12) but it is not going to be installed
                 Depends: libcairo2-dev (>= 1.2.0) but it is not going to be installed
E: Broken packages
bram@bram-laptop:~$ 
```

Apparently, libpango and libcairo aren't installed, but when I try to do a sudo apt-get install libpango1.0-dev, it gives the following unmet dependencies:

```

The following packages have unmet dependencies:
  libpango1.0-dev: Depends: libfreetype6-dev (>= 2.1.3) but it is not going to be installed
                   Depends: libxft-dev but it is not going to be installed
                   Depends: libfontconfig1-dev (>= 2.1.91) but it is not going to be installed
                   Depends: libcairo2-dev (>= 1.2.2) but it is not going to be installed
E: Broken packages

```

So, then I try to install libfreetype6-dev, and I get the following error:

```

The following packages have unmet dependencies:
  libfreetype6-dev: Depends: libfreetype6 (= 2.2.1-5) but 2.3.1-0mlind1~edgy1 is to be installed
E: Broken packages

```

so what should I do? file a bug report about this libfreetype6 dependency or try something else? Anyone has a clue? btw. I did do an sudo apt-get update and sudo apt-get upgrade beforehand.

---

### Post by thom_raindog on 2007-04-15
I have the same issue trying to install libfreetype6-dev to compile wine...

Did you ever find the answer to your problem?

---

### Post by thom_raindog on 2007-04-16
Problem solved.
I had repositories in my sources.list that had updated my libfreetype6 but didn't provide the equivalent devs.
Going back to ubuntus original sources and using 
```
sudo apt-get install libfreetype6=*version needed*
```
helped.

---


---
title: "libglib2.0-dev wont install"
date: 2006-10-18
forum: Absolute Beginner Talk
---

### Post by DSn0wMan on 2006-10-18
libglib2.0-dev wont install.

```
sudo apt-get libglib2.0-dev 
```

produces the following error

```
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libglib2.0-dev: Depends: libglib2.0-0 (= 2.10.2-1ubuntu3) but 2.10.3-0ubuntu1 is to be installed
E: Broken packages

```

The dependency libglib2.0-0 is allready installed. I tried to fix broken packages, but no dice. Does any one know how to get this package to install?

---

### Post by public_void on 2006-10-18
Try 

```
sudo apt-get install libglib2.0-dev
```

---

### Post by DSn0wMan on 2006-10-18
Sorry about the typo in my post.

Edit: This was solved. I just needed to fix my sources.list

---


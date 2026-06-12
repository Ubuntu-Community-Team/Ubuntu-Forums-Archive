---
title: "Problem with libpng-dev"
date: 2007-12-21
forum: Absolute Beginner Talk
---

### Post by resprung on 2007-12-21
Hiya!

I am on Ubuntu 6.06
I have the regular libpng - But I need a matching libpng-dev, and cannot install it:

```
apt-get install libpng12-dev
Reading package lists... Done
Building dependency tree... Done
libpng12-dev is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  libpng12-dev: Depends: libpng12-0 (= 1.2.15~beta5-2ubuntu0.1) but 1.2.8rel-5ubuntu0.3 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

I've searched a lot for these very specific versions, so I can get something that will co-exist, but I'm totally stumped.

Please help, if you can :)

---

### Post by Cypher on 2007-12-21
Did you try the suggested "sudo apt-get -f install" command?

---

### Post by resprung on 2007-12-21
Ah yes.

sudo apt-get -f install
removed the libpng12-dev.

After this I re-ran
apt-get install libpng12-dev

And this time it installed with no errors.

I'm not sure what just happened, but... :)

---


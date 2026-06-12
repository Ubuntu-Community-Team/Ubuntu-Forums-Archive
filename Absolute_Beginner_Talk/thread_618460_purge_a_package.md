---
title: "purge a package"
date: 2007-11-20
forum: Absolute Beginner Talk
---

### Post by lex1 on 2007-11-20
if i want to purge package having made a mess but anther package is depedent on the package i am puring what are the options?

lex

---

### Post by Inxsible on 2007-11-20
purge both and then re-install both, I suppose.

or rather, purge the one you want to purge and only remove the other package. That way your settings will be saved for the second package.

---

### Post by stchman on 2007-11-20
> **lex1 said:**
> if i want to purge package having made a mess but anther package is depedent on the package i am puring what are the options?

lex

First thing ot do if you want to remove a package is to do this:

sudo apt-get autoremove <package name>

This command will remove the package and its dependencies.  Now if one of the dependencies is also being used by another application it will not be removed.  Apt takes care of it for you.

Once you have removed the package then make sure to remove the residual config in synaptic.

I hope this helped.

---

### Post by lex1 on 2007-11-20
the first package must be done with  dpkg --purge as it is a source package.

lex

---


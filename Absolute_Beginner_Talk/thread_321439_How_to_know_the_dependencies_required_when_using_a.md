---
title: "How to know the dependencies required when using apt-get"
date: 2006-12-18
forum: Absolute Beginner Talk
---

### Post by nyxynyx on 2006-12-18
Hello! How do you know the dependencies required when using apt-get to install something? When i see the howto's there are usually some apt-get command with a long list behind them. How do u figure out what's required? Thanks!

---

### Post by enopepsoo on 2006-12-18
Apt-get figures out its own dependencies.

---

### Post by macogw on 2006-12-18
The packages have a list in them that tells apt-get what it needs to pull in with it.  Those are marked as "required".  There's also suggested, conflicts, etc.  I think apt-get pulls in "required" and aptitude pulls in "required" and "suggested" while removing unnecessary packages.  Apt-get and aptitude will just show up "these packages are also needed...install? [y/n]" and you hit y.  You can also type "sudo apt-get install -y packageName" to make it automatically answer yes.

---

### Post by nyxynyx on 2006-12-18
Ic.. I think i must have gotten a little mixed up hehe. My question should have been: When I try to manually install from tarballs, how do i figure out the dependencies?

---

### Post by chalex on 2006-12-18
Each package has metadata fields like Conflicts:, Depends:, Recommends:, Suggests:, with lists of other packages.  apt-get/aptitude/synaptic will also download and install all packages listed in the Depends: field, along with the packages listed in those packages' Depends: fields and so on.

For example, type `apt-cache show vim-gnome` in a Terminal and you'll see all kinds of dependencies.

Have a look here: [http://www.debian.org/doc/debian-policy/ch-relationships.html#s-binarydeps](http://www.debian.org/doc/debian-policy/ch-relationships.html#s-binarydeps)

---

### Post by chalex on 2006-12-18
> **nyxynyx said:**
> Ic.. I think i must have gotten a little mixed up hehe. My question should have been: When I try to manually install from tarballs, how do i figure out the dependencies?

You'll have to carefully read the documentation, and look at the results of ./configure.  That's why we don't install from tarballs anymore :)  

I suggest searching for an unoffifial repository that you can add to your list, and pull the package from there so the package manager can figure all that stuff out.

---


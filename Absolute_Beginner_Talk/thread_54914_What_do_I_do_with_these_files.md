---
title: "What do I do with these files"
date: 2005-08-06
forum: Absolute Beginner Talk
---

### Post by cjoshuav on 2005-08-06
I've found a Bibus link for Ubuntu, and I downloaded the files here:

[http://ubuntu.zeno.co.nz/ubuntu/dists/hoary/bibus/](http://ubuntu.zeno.co.nz/ubuntu/dists/hoary/bibus/)

Unfortunately, I'm such a pathetic newb. that I don't know what to do with them.

Joshua

---

### Post by cjoshuav on 2005-08-06
OK, I figured out to use dpkg -i with the .deb files.

Now I'm stuck in some sort of endless loop of dependencies.  Here's what I did:

I type: sudo dpkg -i bibus_1.0.0-1_all.deb

and get

```
dpkg: dependency problems prevent configuration of bibus:
 bibus depends on wxpython2.5.3; however:
  Package wxpython2.5.3 is not installed.
dpkg: error processing bibus (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 bibus

```

so then I try:  sudo apt-get install wxpython2.5.3

which I thought was pretty clever and showed how much I've learned today, but I get:

```
The following packages have unmet dependencies:
  libsqliteodbc: Depends: libsqlite3-0 (>= 3.0.8) but it is not going to be installed
                 Depends: odbcinst1 but it is not going to be installed
                 Depends: odbcinst1 but it is not going to be installed
  wxpython2.5.3: Depends: libwxgtk2.5.3-python but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

For giggles, I try:  sudo apt-get install libsqlite3-0
and get:

```
The following packages have unmet dependencies:
  bibus: Depends: wxpython2.5.3 but it is not going to be installed
  libsqliteodbc: Depends: odbcinst1 but it is not going to be installed
                 Depends: odbcinst1 but it is not going to be installed

```

So I can't figure out what to apt-get in what order.

Any help appreciated!

- Joshua

---

### Post by johannes on 2005-08-06
I don't know if it makes any difference, but you might want to try using Synaptic to install the wxpython2.5.3 libsqlite3-0 and odbcinst1 packages. In the upper gnome panel, click Systems/Administration/Synaptic Package Manager, search for them, mark them and click Apply. Then dpkg -i the bibus package.

---

### Post by cjoshuav on 2005-08-06
Thanks very much.  Will try...

---


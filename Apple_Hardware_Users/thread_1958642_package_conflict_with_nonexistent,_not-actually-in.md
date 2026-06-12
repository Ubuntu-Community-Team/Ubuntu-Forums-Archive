---
title: "package conflict with nonexistent, not-actually-installed package"
date: 2012-04-14
forum: Apple Hardware Users
---

### Post by dri-ft on 2012-04-14
Hi, all!

I'm trying to install the latest version of  graphviz/libgraphviz, which I downloaded as a deb from their website. I  removed the package for the older version which I had installed from the  repo, and tried to install the new one with dpkg -i. To my puzzlement,  this results in the following 'conflict':

dpkg: regarding libgraphviz4_2.28.0-1_i386.deb containing libgraphviz4:
 libcdt4 conflicts with libgraphviz4
  libgraphviz4 (version 2.28.0-1) is to be installed.
dpkg: error processing libgraphviz4_2.28.0-1_i386.deb (--install):
 conflicting packages - not installing libgraphviz4
Errors were encountered while processing:
 libgraphviz4_2.28.0-1_i386.deb

However,  the offending package, libctd4, doesn't seem to actually be installed,  or even exist (although the older version of graphviz that I uninstalled  calls on it as a dependency). 'sudo aptitude remove libctd4' returns:

Couldn't find any package whose name or description matched "libctd4"
Couldn't find any package whose name or description matched "libctd4"
No packages will be installed, upgraded, or removed.
(etc)

and  'aptitude search libctd4' returns nothing. Anyone have any ideas how I  can get rid of this hallucinatory mirage of a package? Thanks!

---

### Post by kc1di on 2012-04-14
couple things you might try:

1.  would be to ```
dpkg --force <package> 
``` (that will force it to ignore conflicts.)

2. would be to ```
sudo apt-get purge libctd4
``` (which will remove it if it's there.)

good luck

---


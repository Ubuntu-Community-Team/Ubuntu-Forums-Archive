---
title: "Printing to a remote box over the internet"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by wormser on 2007-06-05
I am looking for a way to print to a remote *nix box running cups over the internet.  They are 2 stand alone computers not part of any domain.  Is there a way to do this via ssh or another secure method?  

Thanks

---

### Post by Daishiman on 2007-06-05
Not completely sure, but you can set up an SSH tunnel to forward whichever port CUPS uses to communicate to the print server, then use the KDE printing wizard to set things up.

---

### Post by wormser on 2007-06-05
Does anybody have a guide or something to get me in the right direction?

---


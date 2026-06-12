---
title: "Problem installing software"
date: 2007-04-15
forum: Absolute Beginner Talk
---

### Post by jacatone on 2007-04-15
I've been trying to install some software using apt-get and I keep getting the following error message: 

Errors were encountered while processing:
 fuse-utils
 ntfs-3g
 ntfs-config
jacatone@jacatone-desktop:~$




 How do I fix this? Thanks.

---

### Post by Seisen on 2007-04-15
Is that all it says or is there more above that? If there is please post it.

---

### Post by N Clement on 2007-04-15
What were you trying to get?  If you can, you may just want to try synaptic (System->Administration->Synaptic) or Applications->Add/Remove..

---

### Post by jacatone on 2007-04-16
I think I've been able to install these programs using aptitude but where are they? I don't see them in Applications or elsewhere. Thanks.

---

### Post by zvacet on 2007-04-16
```
whereis program_name
```

This command will tell you in wich directories your installed program is.

---


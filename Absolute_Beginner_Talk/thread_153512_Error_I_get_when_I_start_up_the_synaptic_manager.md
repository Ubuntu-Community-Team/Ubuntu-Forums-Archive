---
title: "Error I get when I start up the synaptic manager"
date: 2006-04-01
forum: Absolute Beginner Talk
---

### Post by pkroks on 2006-04-01
I get the following errors when I start up the Synaptic Package Manager.

```
W: Couldn't stat source package list http://antesis.freecontrib.org breezy/free Packages (/var/lib/apt/lists/antesis.freecontrib.org_mirro..._devnotpublic_dists_breezy_free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://antesis.freecontrib.org breezy/non-free Packages (/var/lib/apt/lists/antesis.freecontrib.org_mirro..._devnotpublic_dists_breezy_non-free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://antesis.freecontrib.org breezy/free Packages (/var/lib/apt/lists/antesis.freecontrib.org_mirro..._devnotpublic_dists_breezy_free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://antesis.freecontrib.org breezy/non-free Packages (/var/lib/apt/lists/antesis.freecontrib.org_mirro..._devnotpublic_dists_breezy_non-free_binary-i386_Packages) - stat (2 No such file or directory)
```

What should I do?

---

### Post by dcstar on 2006-04-01
[QUOTE=pkroks]I get the following errors when I start up the Synaptic Package Manager.

```
W: Couldn't stat source package list http://antesis.freecontrib.org breezy/free Packages (/var/lib/apt/lists/antesis.freecontrib.org_mirro..._devnotpublic_dists_breezy_free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://antesis.freecontrib.org breezy/non-free Packages (/var/lib/apt/lists/antesis.freecontrib.org_mirro..._devnotpublic_dists_breezy_non-free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://antesis.freecontrib.org breezy/free Packages (/var/lib/apt/lists/antesis.freecontrib.org_mirro..._devnotpublic_dists_breezy_free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://antesis.freecontrib.org breezy/non-free Packages (/var/lib/apt/lists/antesis.freecontrib.org_mirro..._devnotpublic_dists_breezy_non-free_binary-i386_Packages) - stat (2 No such file or directory)
```

What should I do?[/QUOTE]
Change that Repository URI in Synaptic to:

[http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/)

---

### Post by moffa on 2006-04-01
Comment them out from your /etc/apt/sources.list file.
To comment them you need to add a # at the beginning of every line you want to comment.

dcstar's response is better

---

### Post by Princey on 2006-04-01
[QUOTE=pkroks]I get the following errors when I start up the Synaptic Package Manager.

```
W: Couldn't stat source package list http://antesis.freecontrib.org breezy/free Packages (/var/lib/apt/lists/antesis.freecontrib.org_mirro..._devnotpublic_dists_breezy_free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://antesis.freecontrib.org breezy/non-free Packages (/var/lib/apt/lists/antesis.freecontrib.org_mirro..._devnotpublic_dists_breezy_non-free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://antesis.freecontrib.org breezy/free Packages (/var/lib/apt/lists/antesis.freecontrib.org_mirro..._devnotpublic_dists_breezy_free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://antesis.freecontrib.org breezy/non-free Packages (/var/lib/apt/lists/antesis.freecontrib.org_mirro..._devnotpublic_dists_breezy_non-free_binary-i386_Packages) - stat (2 No such file or directory)
```

What should I do?[/QUOTE]

You can clear out your sources.list and replace it with a clean one. Here's how to: [http://www.ubuntuforums.org/showpost.php?p=857427&postcount=4]("http://www.ubuntuforums.org/showpost.php?p=857427&postcount=4")

---

### Post by pkroks on 2006-04-01
Ok. thanks

---


---
title: "Problem with Add Applications"
date: 2006-03-21
forum: Absolute Beginner Talk
---

### Post by lyndon on 2006-03-21
The 'Add Applications' feature has worked fine for me until this evening when, having brought up the Add Apps screen, I was presented with the following error message:

W: Couldn't stat source package list [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Packages (/var/lib/apt/lists/ftp.free.fr_pub_Distributions%5fLinux_plf_ubuntu_plf_dists_breezy_free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Packages (/var/lib/apt/lists/ftp.free.fr_pub_Distributions%5fLinux_plf_ubuntu_plf_dists_breezy_non-free_binary-i386_Packages) - stat (2 No such file or directory)

I haven't made any changes to the system as far as I'm aware - what can have happened, and how can I restore things to the way they were?

Lyndon

---

### Post by taurus on 2006-03-21
Try putting # in front of the line(s) for [ftp://ftp.free.fr](ftp://ftp.free.fr) in /etc/apt/sources.list!!!

---

### Post by lyndon on 2006-03-22
[QUOTE=taurus]Try putting # in front of the line(s) for [ftp://ftp.free.fr](ftp://ftp.free.fr) in /etc/apt/sources.list!!![/QUOTE]

Thanks - it worked. Presumably the # turns the lines into comments - but I'd be interested to know in that case where those lines came from and/or why the message hadn't popped up before.  Can other apps add entries to sources.list?

---


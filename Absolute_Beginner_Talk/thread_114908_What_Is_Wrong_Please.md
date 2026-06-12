---
title: "What Is Wrong Please?"
date: 2006-01-09
forum: Absolute Beginner Talk
---

### Post by Dr Von Bon Bon on 2006-01-09
Whenever I try and install anything this happens:


```
W: Couldn't stat source package list http://public.planetmirror.com breezy/free Packages (/var/lib/apt/lists/public.planetmirror.com_pub_plf_ubuntu_plf_dists_breezy_free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://public.planetmirror.com breezy/non-free Packages (/var/lib/apt/lists/public.planetmirror.com_pub_plf_ubuntu_plf_dists_breezy_non-free_binary-i386_Packages) - stat (2 No such file or directory)

```

What do I have to do to fix this please?


Thank you very much

---

### Post by Arktis on 2006-01-09
1.)  Open a terminal.
2.)  Enter the following command:```
sudo gedit /etc/apt/sources.list
```
3.)  Find any lines that have public.planetmirror.com in them and put a **#** in front of them.
4.)  Save and exit.  Open up synaptec and refresh your package information with the reload button.  You may have to refresh at least twice before the error message stops appearing.  It's been my experience anyways.

---

### Post by Dr Von Bon Bon on 2006-01-09
Aha,


That has sorted it.


Cheers

---


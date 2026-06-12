---
title: "synaptic/installer error"
date: 2006-04-15
forum: Absolute Beginner Talk
---

### Post by rameez on 2006-04-15
whenever I use synaptic to install anything or open Software Updates it give me this error:```
W: Couldn't stat source package list http://kubuntu.org breezy/main Packages (/var/lib/apt/lists/kubuntu.org_packages_kde351_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
```
I am running ubunto with gnome, can anyhel help me remove this error.

Thanks

---

### Post by trent dillman on 2006-04-15
Open your apt sources list

```
sudo gedit /etc/apt/sources.list
```

Then comment out any references to kubuntu.org (add a # at the beginning of the line).

Then, reload your sources...

---

### Post by localzuk on 2006-04-15
Can you post the contents of your /etc/apt/sources.list file here?

---

### Post by rameez on 2006-04-15
thanks i commented it and its ok now.

---


---
title: "Open office 1 to 2 ?"
date: 2005-09-02
forum: Absolute Beginner Talk
---

### Post by weasel fierce on 2005-09-02
I just installed open office 2, but can I safely remove the one that comes with Ubuntu ? When I tried to do so in synaptic, it also stated it would remove some other packages, including one titled ubuntu desktop, which made me rather wary

---

### Post by Knome_fan on 2005-09-02
Removing ubuntu-desktop should be no problem.
It's a meta packages, its sole purpose is to depend on all the packages making up a default ubuntu install.
So if you uninstall it, the default applications will all still be there, only the meta-package that was responsible for getting them installed will be gone.

One note of caution though, if you plan on upgrading your install to breezy when the time comes, it is probably a good idea to reinstall this meta-package again.

Hope this helps!

---

### Post by Frederi on 2005-09-02
The problem is that when you remove OpenOffice, you are forced to remove ubuntu-desktop.
And when you try to reinstall ubuntu-desktop, you are forced to reinstall OpenOffice...

---

### Post by Knome_fan on 2005-09-02
[QUOTE=Frederi]The problem is that when you remove OpenOffice, you are forced to remove ubuntu-desktop.
And when you try to reinstall ubuntu-desktop, you are forced to reinstall OpenOffice...[/QUOTE]
Yes, but as I said, removing ubuntu-desktop is not problem. You don't need it.
The only instance where it is probably a good idea to have it installed is when you upgrade to the next release.

---

### Post by benplaut on 2005-09-02
[QUOTE=Frederi]The problem is that when you remove OpenOffice, you are forced to remove ubuntu-desktop.
And when you try to reinstall ubuntu-desktop, you are forced to reinstall OpenOffice...[/QUOTE]

pretty much, ubuntu-desktop is a blank package- it's sole purpose is to make it easier to reinstall all of the packages the system had installed by default. if you remove it, nothing will happen  :)

---

### Post by weasel fierce on 2005-09-02
ahh, well, that makes me feel better :)

---


---
title: "Can I restore the default packages in Synaptic?"
date: 2007-02-27
forum: Absolute Beginner Talk
---

### Post by kittyhawk63 on 2007-02-27
I accidentally :confused: selected "**mark for complete removal**" when I really should have selected "**mark for removal**" from the list of of packages in use. I didn't know the difference at the time. Still learning. 
Is there a way to restore the default packages without, of course, re-installing the program.
Thanks for any assistance. :)
KH

---

### Post by louis_nichols on 2007-02-28
I'm not sure what you mean by "restoring a package" vs "installing a program". There is no real difference between the two. I mean, a package can be either installed or not. The difference between *remove *and *completely remove* is simply that the latter will also erase some configuration files that belong to that program. However, the program is not on your system in either case.

As for restoring default packages... that can be done by installing the package [ubuntu-desktop]("http://packages.ubuntu.com/edgy/metapackages/ubuntu-desktop").

---

### Post by kittyhawk63 on 2007-02-28
> **louis_nichols said:**
> I'm not sure what you mean by "restoring a package" vs "installing a program". There is no real difference between the two. I mean, a package can be either installed or not. The difference between *remove *and *completely remove* is simply that the latter will also erase some configuration files that belong to that program. However, the program is not on your system in either case.

As for restoring default packages... that can be done by installing the package [ubuntu-desktop]("http://packages.ubuntu.com/edgy/metapackages/ubuntu-desktop").

Your last statement "may" have answered my question. I want "all" the packages that Synaptic originally had when I first installed Ubuntu. I had accidentally deleted some packages "off" the **default **list. I hope that clears things up some. Will using **ubuntu-desktop** as you've suggested remove any additions or changes I have made to the desktop? Or does it just add back the "default" packages that I had deleted accidentally in Synaptic?

KH

---

### Post by louis_nichols on 2007-02-28
The latter version is correct. ubuntu-desktop will only be aware of what is missing, but it can not detect extra packages. Those will not do any harm, though. Well, most of times... :) What you could do, is to first install ubuntu-desktop and then manually start removing them, making sure you never uninstall ubuntu-desktop in the process.

Another thing I recommend is to install and use the package [gtkorphan]("http://packages.ubuntu.com/edgy/admin/gtkorphan"). This uninstalls all unneded libraries from your system.

---

### Post by kittyhawk63 on 2007-02-28
> **louis_nichols said:**
> The latter version is correct. ubuntu-desktop will only be aware of what is missing, but it can not detect extra packages. Those will not do any harm, though. Well, most of times... :) What you could do, is to first install ubuntu-desktop and then manually start removing them, making sure you never uninstall ubuntu-desktop in the process.

Another thing I recommend is to install and use the package [gtkorphan]("http://packages.ubuntu.com/edgy/admin/gtkorphan"). This uninstalls all unneded libraries from your system.

Two things:
1. Should I be in Ubuntu? I am now in Xubuntu.

2. How do I go about using ubuntu-desktop? Is it in Synaptic? I am still a newbie.

---

### Post by louis_nichols on 2007-02-28
wow! then it means my info is incorrect. I assumed you were using Ubuntu, which I shouldn't have. No big difference, though. :) It just means that instead of ubuntu-desktop you have to unstall xubuntu-desktop.

ubuntu-desktop and xubuntu-desktop are indeed packages you can find in synaptic. Actually, they are not packages by themselves. They just contain references to other packages that need to be installed in order to have a complete desktop of that kind (ubuntu or xubuntu - there are also kubuntu, edubuntu etc.). So, you don't really "use" them. You just mark them to be installed, then confirm that you also want to install their dependencies and click apply. In your case, only xubuntu-desktop applies.

---

### Post by kittyhawk63 on 2007-02-28
Well, you're not that far off, if any. I mainly use Ubuntu. I am just investigating the features of Xubuntu. I will probably go back to Ubuntu as my regualr desktop. Someone mentioned that they thought Xubuntu worked a little faster, so I was interested in giving it a test run.

Thanks for all your help. KH
I will be marking this thread as "Resolved". Thanks again. :)

---


---
title: "No Icons in OpenOffice"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by HornedBeast on 2007-05-09
Hello,

When I open OpenOffice (any of the programs) I dont see any icons. It simply says ¨Center¨ or ¨Align¨. I am Running X-Server because I wanted to Run Beryl with my ATI card (Aparently the only way at the moment). Is there a fix for this?

Thanks in advance.

---

### Post by HornedBeast on 2007-05-09
Ok.... I actually just found a fix myself.

To Fix I did the following:

Open Synaptic Package Manager and Installed the following packages:

OpenOffice.org-Style-Human
OpenOffice.org-Style-Crystal
OpenOffice.org-Style-Tango

This seems to have fixed the problem.

---

### Post by turezky on 2007-11-13
Got the same trouble... however when I try what was proposed it gives me the msg that the packages are already installed... :(

---

### Post by stchman on 2007-11-13
> **turezky said:**
> Got the same trouble... however when I try what was proposed it gives me the msg that the packages are already installed... :(

Install the other style packages.  You probably chose a different icon theme.  If you select a differnt icon theme OO needs to get the new icons from these packages.

openoffice.org-style-andromeda
openoffice.org-style-crystal
openoffice.org-style-default
openoffice.org-style-hicontrast
openoffice.org-style-human
openoffice.org-style-industrial
openoffice.org-style-tango

```

sudo apt-get -y install openoffice.org-style-andromeda openoffice.org-style-crystal openoffice.org-style-default openoffice.org-style-hicontrast openoffice.org-style-human openoffice.org-style-industrial openoffice.org-style-tango
```

These packages should probably be installed by default.

---

### Post by turezky on 2007-11-20
Thanks, **stchman**! :)
Worked like magic!

---

### Post by andrewski on 2008-03-25
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/153598/](https://bugs.launchpad.net/ubuntu/+source/openoffice.org/+bug/153598/) [br].[/br] ---------------------------- [br].[/br] [br].[/br] 				Yes, definitely. And because it probably won't get fixed unless we report it, see bug #153598.

---


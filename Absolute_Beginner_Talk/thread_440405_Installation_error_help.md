---
title: "Installation error help"
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by WElliott on 2007-05-11
I was installing Virtualbox when the power got yanked out of my machine. When I tried to reinstall I got error messages saying to run dpkg --configure ;a. Did that, ran fine. Now anything with the package installer is giving this error:

Could not initialize the package information

A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:The package virtualbox needs to be reinstalled, but I can't find an archive for it.'

I have the archive and tried to reinstall but it says it's corrupted. I downloaded a fresh copy... same error.

Thanks in advance.

---

### Post by WElliott on 2007-05-11
Stumbled across a fix myself..but seems to be a common issue!!

FIX:

sudo dpkg --remove --force-remove-reinstreq virtualbox

---


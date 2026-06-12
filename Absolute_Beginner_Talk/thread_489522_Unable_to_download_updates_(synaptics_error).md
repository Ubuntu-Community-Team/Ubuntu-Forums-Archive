---
title: "Unable to download updates (synaptics error)"
date: 2007-07-01
forum: Absolute Beginner Talk
---

### Post by Jilbert on 2007-07-01
hi. I tried installing the virtualbox but for some reason its like taking forever to install it so I attempted to cancel. I wasnt able to cancel so what I did was, i restarted my screen by pressing Alt + Ctrl then backspace, and now, am getting an error  ¨

A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:
'E:The package virtualbox needs to be reinstalled, but I can't find an archive for it.'

i  attempted to install the virtualbox using an offline installation but still its unable to solve it.



I tried this command

sudo apt-get install update -m

but still unable to update my packages.

is there a way for me to resolve this issue?

---

### Post by ambush_xx on 2007-07-01
sudo dpkg --force-remove-reinstreq --remove virtualbox

---

### Post by Jilbert on 2007-07-01
wow! thanks man! that worked.!

---


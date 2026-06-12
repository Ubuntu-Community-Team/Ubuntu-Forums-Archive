---
title: "Rpm exit code"
date: 2011-06-22
forum: Any Other OS
---

### Post by prinsh on 2011-06-22
Hi Friends,

I am trying to upgrade an installed rpm with force option and I am getting 0 as exit status of the rpm command for the first time when checked with echo $? but next time onwards it is always giving exit status 1.

any help with the rpm command or script to catch the exit code for any rpm installation command will be of great help.


Thanks

---

### Post by tommcd on 2011-06-22
Are you using Ubuntu??
If you are referring to a rpm package, then you will not be able to use this on Ubuntu. Ubuntu uses .deb packages.
What rpm package are you trying to upgrade? There is most likely a .deb in the Ubuntu repos.

And welcome to the Uubntu forums!

---

### Post by prinsh on 2011-06-22
I am not trying to install the rpm on Ubuntu instead its a different RFS developed by us for our use.

I am attaching the spec file for the rpm as we our self are creating the rpm. see if it can help.


thanks

---

### Post by Perfect Storm on 2011-06-24
Moved to Other OS/Distro Talk.

---


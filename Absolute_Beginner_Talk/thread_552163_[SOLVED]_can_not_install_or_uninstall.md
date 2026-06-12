---
title: "[SOLVED] can not install or uninstall"
date: 2007-09-16
forum: Absolute Beginner Talk
---

### Post by DLHmatt on 2007-09-16
while trying to install virtualbox something went a miss and now all i get are messages.

update manager says:
 Could not initialize the package information

A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:The package virtualbox needs to be reinstalled, but I can't find an archive for it.'

package manager says: 
an error occurred
The following details are provided:
E: The package virtualbox needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.

when i open the .deb file in package installer i get the message "could not open 'virtualbox_1.5.0-24069-1_Ubuntu_feisty_i386.deb' the package might be corrupted or you are not allowed to open the file. check the permission of the file"

i re-downloaded the program and nothing changed. and checked the permission and i have permission to read and write. 
:confused:

---

### Post by forestpixie on 2007-09-16
yea - I've been there, went round in circles for days 

open a terminal - accessories >terminal in case you don't know

```
sudo dpkg --remove --force-remove-reinstreq virtualbox
```

---

### Post by DLHmatt on 2007-09-16
> **forestpixie said:**
> yea - I've been there, went round in circles for days 

open a terminal - accessories >terminal in case you don't know

```
sudo dpkg --remove --force-remove-reinstreq virtualbox
```

AWESOME! thanks a million!

---

### Post by forestpixie on 2007-09-16
you're welcome it's no problem - be aware that you shouldn't use that command unless you really need to. I just remember how many commands I used that made no difference in that situation.

Can you mark thread solved - use thread tools at top.

---

### Post by forestpixie on 2007-09-16
sorry - double post

---


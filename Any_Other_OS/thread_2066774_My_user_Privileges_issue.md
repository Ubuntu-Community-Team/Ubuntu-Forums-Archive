---
title: "My user Privileges issue"
date: 2012-10-05
forum: Any Other OS
---

### Post by rmcellig on 2012-10-05
I just installed Madbox Linux which is a Ubuntu 12.04 distro running Openbox as the WM/DE.

For some reason when I install Synaptic using sudo apt-get install synaptic after installing and launching Synaptic presents a message "starting without administrative privileges. Also when I try to access any of the partitions on my HD I get this:

Authentication is required.

What should I do? When I do an ID from the terminal I get this:


uid=1000(randy) gid=1000(randy) groups=1000(randy),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),115(lpadmin),116(sambashare)

---

### Post by ajgreeny on 2012-10-05
Open synaptic with command ```
gksudo synaptic
```or make a launcher with that command (I don't know if that's possible in openbox) and you will get synaptic with admin permissions.  This is just the same as it is in ubuntu.

I don't know how you are trying to mount and access your other partitions but that will also need admin permissions.  Once again I don't know exactly how to do that in openbox other than with a terminal command, but I'm sure there must be a way.

---

### Post by oldos2er on 2012-10-05
Moved to Other OS/Distro Talk.

---


---
title: "samba"
date: 2008-01-31
forum: Absolute Beginner Talk
---

### Post by Matt26 on 2008-01-31
is samba included in the add/remove Applications section or Synaptics package manager on Ubuntu 7.10, or do you have to go to the website and download it?  i am assuming that it isn't installed on Ubuntu by default, correct? thanks.

---

### Post by oedha on 2008-01-31
smbclient is include.....
i installed from live cd.....and i took samba from synaptic to run samba server
if it's only to shared folder over network....take smbfs also from synaptic

regards;
~E~

---

### Post by Matt26 on 2008-01-31
so do i have to install it if i haven't done so already?  i am not sure what components or packages i would need if this is the case and where they would be located (add/remove Applications section or Synaptics package manager)... i want to be able to share files on an NTFS volume mounted within Ubuntu with a Windows XP Pro guest VM on VMware Workstation 6.0- would samba be necessary for this situation?  thanks.

---

### Post by jose158 on 2008-01-31
I'm pretty sure you could just do this: ```
sudo apt-get install samba
```

---

### Post by jaytek13 on 2008-01-31
> **Matt26 said:**
> so do i have to install it if i haven't done so already?  i am not sure what components or packages i would need if this is the case and where they would be located (add/remove Applications section or Synaptics package manager)... i want to be able to share files on an NTFS volume mounted within Ubuntu with a Windows XP Pro guest VM on VMware Workstation 6.0- would samba be necessary for this situation?  thanks.

There is a "shared folders" option system->administration. It will install the required software you need and then allow you to define share folders and permissions.

---

### Post by oedha on 2008-01-31
to read network folder ...smbclient is enough
you can see from places - connect to network
or type down the computer name like smb://computername
from nautilus
to map those drive you need smbfs :==> 
sudo apt-get install smbfs <-- run from terminal

~E~

---

### Post by Matt26 on 2008-02-01
i went into Shared Folders under Administration in Ubuntu and it prompted me to install smb and nfs, so i did and it allowed me to define my shares.  when i go into XP under Workgroups i can see the Ubuntu server now, but it prompts me to login when i try to access it- i'm guessing it is looking for credentials that belong to Ubuntu, so i tried using both my regular account and root, but neither would accept.  what am i doing wrong here?

---


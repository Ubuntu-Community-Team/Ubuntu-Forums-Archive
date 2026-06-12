---
title: "Debian not mounting external HDD"
date: 2012-06-13
forum: Any Other OS
---

### Post by Andrew Jeyaraj on 2012-06-13
Hi

I currently have Debian(squeeze) installed on a Dell Inspiron 9200 with a 1.6 GHz Pentium M and 512 Mb of RAM.I tried connecting my 320 Gb Samsung External harddrive and i get the following message.I checked the syslog file which stated that the system could not recognize CD format.

Im a bit confused now.Please Help

Regards
Andrew

---

### Post by Andrew Jeyaraj on 2012-06-13
error message dialouge

---

### Post by BBQdave on 2012-06-14
> **Andrew Jeyaraj said:**
> I currently have Debian(squeeze) installed on a Dell Inspiron 9200 with a 1.6 GHz Pentium M and 512 Mb of RAM.I tried connecting my 320 Gb Samsung External harddrive and i get the following message.I checked the syslog file which stated that the system could not recognize CD format.

Depends on the hard drive format. A general purpose format for external drives is fat32, you can access from Windows, Mac, and Linux machines.

If your hard drive is formatted as a back up drive (specific to the application that uses it), or an OS has formatted it specific to a user, then it can not be accessed in general.

---


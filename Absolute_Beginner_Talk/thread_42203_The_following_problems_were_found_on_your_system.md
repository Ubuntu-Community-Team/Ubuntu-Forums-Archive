---
title: "The following problems were found on your system:"
date: 2005-06-16
forum: Absolute Beginner Talk
---

### Post by Scheltes on 2005-06-16
When starting Synaptic packet manager I allways get the following Warning:

"The following problems were found on your system:

W: Kon de status van de bronpakketlijst [ftp://ftp.nerim.net](ftp://ftp.nerim.net) stable/main Packages (/var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_stable_main_binary-i386_Packages) niet opvragen - stat (2 Onbekend bestand of map)
W: Kon de status van de bronpakketlijst [ftp://ftp.nerim.net](ftp://ftp.nerim.net) testing/main Packages (/var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_testing_main_binary-i386_Packages) niet opvragen - stat (2 Onbekend bestand of map)"

What does it mean and how can I get rid of this warning?

Thanks in advance.

---

### Post by imightbegiant on 2005-06-16
This means that those 2 repositories are not working at the moment. You can disable them by commenting out those to 2 ftp sites in /etc/apt/sources.list or in synaptic>settings>repositories>remove.

---

### Post by Scheltes on 2005-06-16
I found out myself.
I created a new sources.list and that did the trick.

---


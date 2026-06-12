---
title: "hplip won't download dependencies."
date: 2008-02-03
forum: Absolute Beginner Talk
---

### Post by da Wookiee on 2008-02-03
I'm trying to install hplip 2.7.12 because my printer isn't supported with the default hplip that comes with 7.10.  Using the installer from the hplip site, it runs, but doesn't seem to be able to connect to the internet.  Firefox hits the internet just fine, so I'm unsure what's missing.


```
INSTALL MISSING OPTIONAL DEPENDENCIES
-------------------------------------
warning: There are 4 missing OPTIONAL dependencies.
note: Installation of dependencies requires an active internet connection.
warning: Missing REQUIRED dependency for option 'network': libcrypto (libcrypto - OpenSSL cryptographic library)
warning: Missing REQUIRED dependency for option 'network': libnetsnmp-devel (libnetsnmp-devel - SNMP networking library development files)
warning: Missing REQUIRED dependency for option 'scan': sane-devel (SANE - Scanning library development files)
warning: Missing OPTIONAL dependency for option 'scan': scanimage (scanimage - Shell scanning program)


CHECKING FOR NETWORK CONNECTION
-------------------------------
error: 
The network appears to be unreachable. Installation cannot complete without access to
error: distribution repositories. Please check the network and try again.

```

---

### Post by dcstar on 2008-02-04
> **da Wookiee said:**
> I'm trying to install hplip 2.7.12 because my printer isn't supported with the default hplip that comes with 7.10.  Using the installer from the hplip site, it runs, but doesn't seem to be able to connect to the internet.  Firefox hits the internet just fine, so I'm unsure what's missing.


```
INSTALL MISSING OPTIONAL DEPENDENCIES
-------------------------------------
warning: There are 4 missing OPTIONAL dependencies.
note: Installation of dependencies requires an active internet connection.
warning: Missing REQUIRED dependency for option 'network': libcrypto (libcrypto - OpenSSL cryptographic library)
warning: Missing REQUIRED dependency for option 'network': libnetsnmp-devel (libnetsnmp-devel - SNMP networking library development files)
warning: Missing REQUIRED dependency for option 'scan': sane-devel (SANE - Scanning library development files)
warning: Missing OPTIONAL dependency for option 'scan': scanimage (scanimage - Shell scanning program)


CHECKING FOR NETWORK CONNECTION
-------------------------------
error: 
The network appears to be unreachable. Installation cannot complete without access to
error: distribution repositories. Please check the network and try again.

```

You have the names of the missing packages, install them yourself using Synaptic.

---

### Post by da Wookiee on 2008-02-04
Tried that, libcrypto is the only one that synaptic has heard of.  the others all return no package selected.

---


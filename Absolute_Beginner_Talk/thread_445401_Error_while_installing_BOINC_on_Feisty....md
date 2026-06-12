---
title: "Error while installing BOINC on Feisty..."
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by txr13 on 2007-05-15
When trying to install boinc-client on Feisty, I receive the following message:
```
Setting up boinc-client (5.4.11-5) ...
chown: changing ownership of `/var/lib/boinc-client/global_prefs_override.xml': No such file or directory
dpkg: error processing boinc-client (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 boinc-client
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

I've looked at /var/lib/boinc-client, and there seems to be a global_prefs_override.xml in there. Can anybody give me an idea of what to try?

---

### Post by txr13 on 2007-05-15
Okay, looks like just creating a file with just a single space there overtop of the existing link fixed the issue...

---


---
title: "autopano-complete script fixes"
date: 2007-05-29
forum: Art &amp; Design
---

### Post by chrono325 on 2007-05-29
I realize that this should really be a bug report, but as far as I can tell, the launchpad.net page for Autopano-SIFT does not have an open bug report section.

Anyway, there are problems with the current 'autopano-complete' script as it is installed. It seems like Ubuntu installs autopano in a different way than it was designed. The upstream approach is to install the mono binaries directly in /usr/bin, whereas Ubuntu puts small scripts there which call those binaries. autopano-complete, however, expects the binaries to be there and tries to run `mono /usr/bin/generatekeys.exe` for example. What it should be doing is running `/usr/bin/generatekeys`. I can include a diff if need be.

---


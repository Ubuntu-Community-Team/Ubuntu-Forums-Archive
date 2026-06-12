---
title: "Can't Install PHP 5 package"
date: 2007-07-15
forum: Absolute Beginner Talk
---

### Post by JengaBlocks on 2007-07-15
I tried using Synaptic package Manager to mark the PHP 5 modules and I get back the following:

Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/p/php5/php5-common_5.1.6ubuntu2.3_i86.deb](http://security.ubuntu.com/ubuntu/pool/main/p/php5/php5-common_5.1.6ubuntu2.3_i86.deb)
404 Not Found (IP: 91.189.88.31 80]

among other 404's


Whats the prob? I can ping to the IP but something is hosed on Ubuntu's end. Anyone else?

---

### Post by agurk on 2007-07-15
According to [this page](http://packages.ubuntu.com/edgy/web/php5-common), your Synaptic is showing an old version, have you pressed 'Update'?

The correct (latest) file is [here](http://security.ubuntu.com/ubuntu/pool/main/p/php5/php5-common_5.1.6-1ubuntu2.5_i386.deb).

---

### Post by JengaBlocks on 2007-07-16
Agurk:

I assume you mean the "Reload" button to refresh the file list. If so, I tried that and it appears to have worked - I now have all the current PHP 5.x files on my system.

Thanks!

---

### Post by agurk on 2007-07-16
Ah yes, I meant 'Reload', glad it worked!

---


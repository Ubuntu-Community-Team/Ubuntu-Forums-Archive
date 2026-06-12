---
title: "Samba Install Issue: &quot;not fully installed&quot;"
date: 2006-09-02
forum: Absolute Beginner Talk
---

### Post by paulyphonic on 2006-09-02
whenever i start or stop Samba daemons, or update/upgrade i get the following error:

Setting up samba (3.0.22-1ubuntu3.1) ...
update-rc.d: warning: /etc/rc2.d/K09samba is not a link to ../init.d/samba or /etc/init.d/samba
update-rc.d: warning: /etc/rc3.d/K09samba is not a link to ../init.d/samba or /etc/init.d/samba
invoke-rc.d: dangling symlink: /etc/rc2.d/K09samba
dpkg: error processing samba (--configure):
 subprocess post-installation script returned error exit status 102
Errors were encountered while processing:
 samba
E: Sub-process /usr/bin/dpkg returned an error code (1)

is this an error that i should be concerned with, and if so, is there any advice that anyone has to offer and maybe help resolve this?

thanks in advance.

---

### Post by sitedesign on 2006-10-01
backup your samba config file first.

Try uninstalling all the samba packages and make sure you use the mark for complete removal option.

Then delete any file about samba. Then re-install the samba packages.

---


---
title: "Update Manager stuffed with &quot;Unauthenticated&quot; Updates"
date: 2009-05-29
forum: Apple Hardware Users
---

### Post by Enyalie on 2009-05-29
I've a Macbook Pro dual booting Intrepid and OS-X, and the update manager has come up with a huge list of updates which it warns are "unauthenticated" and could allow some malicious person or entity to damage or  take control of my computer. I've appended the list below. it looks like rather benign stuff. I haven't messed with the default repositories; any idea what's going on? Should I go ahead and install the updates anyway?

The updates listed as unauthenticated were:

acpid (version 1.0.6-9ubuntu4) will be upgraded to version 1.0.6-9ubuntu4.8.10.2
apparmor (version 2.3+1289-0ubuntu4.1) will be upgraded to version 2.3+1289-0ubuntu4.2
apparmor-utils (version 2.3+1289-0ubuntu4.1) will be upgraded to version 2.3+1289-0ubuntu4.2
apport (version 0.119) will be upgraded to version 0.119.2
apport-gtk (version 0.119) will be upgraded to version 0.119.2
apt (version 0.7.14ubuntu6) will be upgraded to version 0.7.14ubuntu6.1
apt-utils (version 0.7.14ubuntu6) will be upgraded to version 0.7.14ubuntu6.1
fakeroot (version 1.9.5ubuntu1) will be upgraded to version 1.9.5ubuntu1.1
firefox (version 3.0.8+nobinonly-0ubuntu0.8.10.2) will be upgraded to version 3.0.10+nobinonly-0ubuntu0.8.10.1
firefox-3.0 (version 3.0.8+nobinonly-0ubuntu0.8.10.2) will be upgraded to version 3.0.10+nobinonly-0ubuntu0.8.10.1
firefox-3.0-branding (version 3.0.8+nobinonly-0ubuntu0.8.10.2) will be upgraded to version 3.0.10+nobinonly-0ubuntu0.8.10.1
firefox-3.0-gnome-support (version 3.0.8+nobinonly-0ubuntu0.8.10.2) will be upgraded to version 3.0.10+nobinonly-0ubuntu0.8.10.1
firefox-gnome-support (version 3.0.8+nobinonly-0ubuntu0.8.10.2) will be upgraded to version 3.0.10+nobinonly-0ubuntu0.8.10.1
gnome-power-manager (version 2.24.0-0ubuntu8.2) will be upgraded to version 2.24.0-1mactel4
gnome-system-tools (version 2.22.1-0ubuntu1) will be upgraded to version 2.22.1-0ubuntu1.1
libapparmor-perl (version 2.3+1289-0ubuntu4.1) will be upgraded to version 2.3+1289-0ubuntu4.2
libapparmor1 (version 2.3+1289-0ubuntu4.1) will be upgraded to version 2.3+1289-0ubuntu4.2
libfreetype6 (version 2.3.7-2ubuntu1) will be upgraded to version 2.3.7-2ubuntu1.1
libpam-modules (version 1.0.1-4ubuntu5.3) will be upgraded to version 1.0.1-4ubuntu5.5
libpam-runtime (version 1.0.1-4ubuntu5.3) will be upgraded to version 1.0.1-4ubuntu5.5
libpam0g (version 1.0.1-4ubuntu5.3) will be upgraded to version 1.0.1-4ubuntu5.5
libpango1.0-0 (version 1.22.2-0ubuntu1) will be upgraded to version 1.22.2-0ubuntu1.1
libpango1.0-common (version 1.22.2-0ubuntu1) will be upgraded to version 1.22.2-0ubuntu1.1
libwmf0.2-7 (version 0.2.8.4-6) will be upgraded to version 0.2.8.4-6ubuntu0.8.10.1
linux-generic (version 2.6.27.11.14) will be upgraded to version 2.6.27.14.18
linux-headers-generic (version 2.6.27.11.14) will be upgraded to version 2.6.27.14.18
linux-image-generic (version 2.6.27.11.14) will be upgraded to version 2.6.27.14.18
linux-libc-dev (version 2.6.27-11.31) will be upgraded to version 2.6.27-14.33
linux-restricted-modules-common (version 2.6.27-11.16) will be upgraded to version 2.6.27-14.19
linux-restricted-modules-generic (version 2.6.27.11.14) will be upgraded to version 2.6.27.14.18
ntpdate (version 1:4.2.4p4+dfsg-6ubuntu2.2) will be upgraded to version 1:4.2.4p4+dfsg-6ubuntu2.3
python-apport (version 0.119) will be upgraded to version 0.119.2
python-problem-report (version 0.119) will be upgraded to version 0.119.2
xserver-xorg-input-synaptics (version 0.15.2-0ubuntu7) will be upgraded to version 0.15.2-0ubuntu7-mactel1
xulrunner-1.9 (version 1.9.0.8+nobinonly-0ubuntu0.8.10.1) will be upgraded to version 1.9.0.10+nobinonly-0ubuntu0.8.10.1
xulrunner-1.9-gnome-support (version 1.9.0.8+nobinonly-0ubuntu0.8.10.1) will be upgraded to version 1.9.0.10+nobinonly-0ubuntu0.8.10.1
linux-headers-2.6.27-14 (version 2.6.27-14.33) will be installed
linux-headers-2.6.27-14-generic (version 2.6.27-14.33) will be installed
linux-image-2.6.27-14-generic (version 2.6.27-14.33) will be installed
linux-restricted-modules-2.6.27-14-generic (version 2.6.27-14.19) will be installed

Thanks,
~Enyalie

---

### Post by cyberdork33 on 2009-05-30
only *some* on those packages are "unauthenticated". More specifically, the mactel packages that are from the mactel PPA. Since the PPA is not an official Ubuntu repo, it warns you that you are getting packages from there.

---

### Post by Enyalie on 2009-05-31
Got it, thanks!

---


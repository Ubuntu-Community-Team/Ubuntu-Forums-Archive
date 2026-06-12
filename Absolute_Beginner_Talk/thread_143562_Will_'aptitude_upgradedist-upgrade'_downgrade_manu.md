---
title: "Will 'aptitude upgrade/dist-upgrade' downgrade manually installed deb package?"
date: 2006-03-12
forum: Absolute Beginner Talk
---

### Post by Akhran on 2006-03-12
Let's say I download the latest source codes, create a deb package using checkinstall and install the package with 'dpkg -i', but the package version in the depositary is of a older version. Will doing a 'aptitude upgrade or dist-upgrade' actually downgrade the installed latest version to the older version found in the depositary?

Thanks.

---

### Post by Xian on 2006-03-12
No, when you install with dpkg it is recognized in APT and treated like any other versioned package, save that you do not have the reinstall option since it is only staged locally.

---


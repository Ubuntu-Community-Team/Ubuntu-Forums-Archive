---
title: "Uninstalling OpenOffice.org"
date: 2006-11-01
forum: Absolute Beginner Talk
---

### Post by zugu on 2006-11-01
Hello, fellow Ubuntu users!

When I try to remove openoffice.org packages, I am prompted that some other packages will be removed:

language-support-en
python-uno
thunderbird-locale-en-gb

Is it safe to remove these packages too?

---

### Post by chuckyp on 2006-11-01
Those packages should only be dependencies for openoffice.  It may also want to remove ubuntu-desktop which is a meta package for dist-upgrades.

---

### Post by zugu on 2006-11-01
Thank you.

---

### Post by jpeddicord on 2006-11-01
It should be safe to remove it, although you *may* not recieve language pack updates, as it appears to remove language-support-en. That is only speculation though, and it still may work fine.

---

### Post by carla on 2006-11-03
> **chuckyp said:**
> Those packages should only be dependencies for openoffice.  It may also want to remove ubuntu-desktop which is a meta package for dist-upgrades.

Thanks for this! I wanted to remove OpenOffice, and was unnerved by its apparent dependency on kubuntu-desktop. Forgot that was only a meta package. Whoops. Thanks for the reminder.

---


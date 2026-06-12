---
title: "Installing stuff"
date: 2005-07-12
forum: Absolute Beginner Talk
---

### Post by xbilly on 2005-07-12
I have been using linux for a while, but I still am clueless when it comes to installing anything not in SPM. Such as various games, programs, etc. Are their any online guides that could help me or assist me in installing certain file types and src codes?

---

### Post by musicman2059 on 2005-07-12
Well, first off, is usually isn't a good idea to install anything not in Ubuntu's repositories as it isn't designed for Ubuntu specifically.  (Most .debs out there are, obviously, mainly for Debian systems.  This doesn't neccesarily include Debian-based systems)

If you really feel the need to, try to stick with .deb files still, as compiling from .tar.gz can be tricky, and RPMs may mess things up.

Once you've downloaded it, use the following command in the terminal:

```
sudo dpkg -i /path/to/packagename.deb
```

---


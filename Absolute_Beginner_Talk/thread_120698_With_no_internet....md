---
title: "With no internet..."
date: 2006-01-23
forum: Absolute Beginner Talk
---

### Post by Thebrassmonkey on 2006-01-23
Wit no internet is it possible to download and install stuff on Ubuntu. I won't be able to connect my newly installed OS to the internet until March, at least. Being new to linux I have no idea if this is possible. Any options?

---

### Post by carlosqueso on 2006-01-23
Yes, it's possible, but not easy.  You can get packages that you want to try through packages.ubuntu.com transfer them over and install with ```
sudo dpkg -i <name of file>
```  However, I wouldn't recommend that method for packages with lots of dependencies.

---


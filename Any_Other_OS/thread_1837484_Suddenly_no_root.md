---
title: "Suddenly no root"
date: 2011-09-01
forum: Any Other OS
---

### Post by Zeta-K on 2011-09-01
I've been using Gentoo for a bit and everything's been working great until today.
Today I started my computer up and logged in as root to do some installation work only to find that root doesn't appear to have root access as far as permissions are concerned. I also can't sudo. I get a message: 
```
-bash: sudo: command not found
```If anyone could help me out, I'd **REALLY** appreciate it because I don't want to re-install.

Thanks.


_**EDIT:**_ Never mind! I feel like such an idiot! I've been trying to execute make.conf instead of reading it!

---

### Post by kyletstrand on 2011-09-01
It almost seems to me that you would have to reinstall sudo?

Maybe try just su and see if you can get root permissions that way.

---

### Post by kyletstrand on 2011-09-01
[http://www.gentoo.org/doc/en/sudo-guide.xml](http://www.gentoo.org/doc/en/sudo-guide.xml)

Maybe check out that limk to see if it offers any insight.

---

### Post by Zeta-K on 2011-09-01
> **kyletstrand said:**
> It almost seems to me that you would have to reinstall sudo?

Maybe try just su and see if you can get root permissions that way.

It changes me to root, but then I still can't access my make.conf file: Permission denied

_**EDIT: **_Never mind.

---

### Post by kyletstrand on 2011-09-01
Get it figured out??

---

### Post by Zeta-K on 2011-09-01
> **kyletstrand said:**
> Get it figured out??

Yeah, I was trying to execute a non-executable and thought I was sending the command to read it with nano. Root had permissions to read it all along; it only said permission denied because the file couldn't possibly be executed.

---


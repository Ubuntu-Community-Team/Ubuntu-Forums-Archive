---
title: "Completely re-installing a package"
date: 2006-10-08
forum: Absolute Beginner Talk
---

### Post by Orestes on 2006-10-08
When a package is installed and the removed, the configuration files are left  in /etc.

In a vain attempt to re-install a package with a virgin set of configuration files, I apt-get removed the package and the deleted the configuration files.

](*,) 

Yeah, I know it was stupid. Now.

Thing is, When I try and re-install the package, it complains about these missing files. How can I get it to reinstall the package as if it had never been installed in the first place?

Thanks!

---

### Post by Orestes on 2006-10-08
I found a way:

aptitude purge packagename

---


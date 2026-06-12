---
title: "Ubuntu packages in Mint"
date: 2008-04-15
forum: Absolute Beginner Talk
---

### Post by the beak on 2008-04-15
I have downloaded lib6c-dev from the Ubuntu repository to install in Mint.

However the package manager in mint doesn't unpack the file.

Does anyone know how to unpackage ubuntu files in mint please?

---

### Post by ibutho on 2008-04-15
Are you looking to install the package or just extract the deb file? If you are looking to install the deb file, then use "sudo dpkg -i somefile.deb" or install gdebi then click on the package. To extract the contents of the deb files, then use "ar x somefile.deb" and then "tar zxvf data.tar.gz".

---


---
title: "How do i install tar.gz packages onto my ubuntu linux?"
date: 2006-10-04
forum: Absolute Beginner Talk
---

### Post by frodegb on 2006-10-04
I am trying to install a application (madwifi), maybe i can install this with the synaptic package manager, but i want to learn how i install those .tar.gz packages myself using the terminal.

does it work like this?

$./configure "madwifi.tar"
$make install "madwifi.tar"
$install "madwifi.tar"

or something?

---

### Post by arochester on 2006-10-04
See [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by pay on 2006-10-04
The basic procedure is```
tar zxvf file.gz
cd file
./configure
make
sudo make install
```also you can make a basic .deb file by installing checkinstall and running sudo checkinstall -D make install instead of sudo make install.

---

### Post by frodegb on 2006-10-04
thanks!

---

### Post by jaboua on 2006-10-04
Also, if the file is a .tar.bz2 file instead of .tar.gz, run "tar -jxf file.tar.bz2" instead of the tar-command mentioned above

---


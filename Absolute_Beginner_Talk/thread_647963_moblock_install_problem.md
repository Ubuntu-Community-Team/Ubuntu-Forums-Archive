---
title: "moblock install problem"
date: 2007-12-22
forum: Absolute Beginner Talk
---

### Post by dfault312 on 2007-12-22
im trying to install moblock. i downloaded the tar, extracted it, but when i type "sudo make install" from the moblock directory, it says
> install -m 755 moblock /usr/bin
install: cannot stat `moblock': No such file or directory
make: *** [install] Error 1

what gives?

---

### Post by talsemgeest on 2008-01-19
Shouldnt you go 

sudo make
sudo make install

?

---


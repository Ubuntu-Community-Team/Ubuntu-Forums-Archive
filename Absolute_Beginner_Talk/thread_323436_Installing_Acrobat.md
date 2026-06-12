---
title: "Installing Acrobat"
date: 2006-12-22
forum: Absolute Beginner Talk
---

### Post by eng. on 2006-12-22
hi,
i want to install acrobat reader , its directory structure and files is as shown:

common
	acroread  -  acroread.tar   -    ar302lin.tar   -  LICREAD
i386-linux
	bin
	              acroread
	Browsers
	Fonts
	Reader

how could i install it without using Synaptic?

regards

---

### Post by Ferri on 2006-12-22
It should have a "readme" (or similar name) file inside.
Most programs can be installed, from command line by the following:
```
./configure
make
sudo make install
```
After configure you may need to install come dependencies it will list.
However, it's easier to install it with synaptic or "apt-get install".

---


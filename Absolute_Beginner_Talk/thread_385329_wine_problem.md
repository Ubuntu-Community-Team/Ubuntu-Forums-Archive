---
title: "wine problem"
date: 2007-03-15
forum: Absolute Beginner Talk
---

### Post by Franswa_CS on 2007-03-15
i have a problem in installing wine on my ubuntu linux. each time i try to install it, it gives my the following message:

WINE Installer v0.75


Running configure...


configure: creating cache config.cache
checking 
build system type... i686-pc-linux-gnulibc1

checking host system type... i686-pc-linux-gnulibc1

checking whether make sets $(MAKE)... yes

checking for gcc... gcc

checking for C compiler default output file name... 

configure: error: C compiler cannot create executables
See `config.log' for more details.

Configure failed, aborting install.

please reply quickly, thanks

---

### Post by jhenager on 2007-03-15
Wine can be installed through Add/Remove. I'd try that first.

---

### Post by dstew on 2007-03-15
Have you installed build-essentials?

---

### Post by Architeuthis on 2007-03-15
Hmm I don't know what method you are using there to install wine; but Installed wine by adding "deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main" to my /etc/apt/sources.list file. I got this information from the official wine page, but I just saw the page on wine HQ which told me to add that line has changed. So you should better check this page out: [http://www.winehq.com/site/download-deb](http://www.winehq.com/site/download-deb) ; there you can get some up to date information on how to add the official wine repository to your apt sources so you always have the latest version of wine.

---

### Post by Franswa_CS on 2007-03-16
i can't use add/remove program as i use a dial up modem to connect to the internet.
i have downloaded the package for my modem and installed it but i don't know how to run my modem.
i want to tell you that i have configured my modem.

---

### Post by Franswa_CS on 2007-03-18
thanks God i have installed wine on my ubuntu.
thanks for all of you

---


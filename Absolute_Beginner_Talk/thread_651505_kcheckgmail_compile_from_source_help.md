---
title: "kcheckgmail compile from source help"
date: 2007-12-27
forum: Absolute Beginner Talk
---

### Post by linuxnovice on 2007-12-27
Hi,

I want to install Kcheckgmail from on my system. The one in the Ubuntu repository is outdated. So I got the source from the developer's website. I started the configuration and it got stuck at finding headers and libs for qt4.

checking for Qt... configure: error: Qt (>= Qt 3.2 and < 4.0) (headers and libraries) not found. Please check your installation!
For more details about this problem, look at the end of config.log.

I installed libqt4-dev and qt4-dev-tools but they still gave the same error. Could someone please help me out on this?

Thanks.

Note: After libqt4-dev and qt4-dev-tools didnt help in the compilation I removed them from my system...so please let me know whether I need them in my installation.

---

### Post by SOULRiDER on 2007-12-27
Qt (>= Qt 3.2 and < 4.0)

That means 4 will NOT work, install the qt3 development libraries.

---

### Post by linuxnovice on 2007-12-27
> **SOULRiDER said:**
> Qt (>= Qt 3.2 and < 4.0)

That means 4 will NOT work, install the qt3 development libraries.

Thanks. So what files do I need to install here? There is no libqt3-dev but there is libqt3-mt-dev. It says this is qt3 threaded dev files. There is also qt3-dev-tools. So do I install these?

---


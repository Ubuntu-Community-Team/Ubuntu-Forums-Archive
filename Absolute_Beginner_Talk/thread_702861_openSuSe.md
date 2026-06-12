---
title: "openSuSe"
date: 2008-02-20
forum: Absolute Beginner Talk
---

### Post by supertails on 2008-02-20
How do you download openSuSe and is the openSuSe you download the same has the one you buy because I'm thinking for buying it but it has some extra feature but can it run and install all Windows products yet still keeping Linux safe?

---

### Post by jan quark on 2008-02-20
download here:
[http://www.opensuse.org/](http://www.opensuse.org/)

haven't used suse 
no idea

---

### Post by wolfen69 on 2008-02-20
the download version is the same as the one you buy. and no, you will not be able to run all windows programs. some programs might run with wine, but there are no guarantees.

---

### Post by supertails on 2008-02-20
Do you used openSuSe or Wine? What is the difference?

---

### Post by xyphur on 2008-02-20
No Windows program will run natively on Linux. It is not possible, just the same as it is impossible to run Mac OS X programs natively on Windows, or vice versa. They are completely different operating systems, each with their own executable binary formats, and thus are incompatible with one another.

That being said, there are programs available that will allow you to execute non-native binary formats under different operating systems than those which they were intended for. You can run some Windows programs under an application compatibility layer, such as that of Wine (WINdows Emulator), but not all programs play nicely in such an environment and many will refuse to run outright. It is therefore a better idea to find native Linux software that will provide the same functionality or purpose to that of the programs you use on Windows if at all possible, and rely on Wine as a last resort to software you absolutely cannot find alternatives for.

Failing that, another option is to run a virtual machine on Linux, with a complete installation of Windows and the essential programs you use installed inside it. This is different from Wine in that you are running a full and complete Windows environment, rather than a stripped down version consisting mainly of libraries and other dependancies that are required to run the program. Taking this route, you will likely have far less compatibility issues than you would with Wine, because as far as the program is concerned, it's running natively under Windows.

OpenSUSE is a distribution of Linux, just the same as Ubuntu, RedHat, or Debian is. It can't do any more than Ubuntu can do (run windows programs, et al), as it is built on essentially the same core technologies. A distribution is just another way of saying 'pre-packaged, slightly customized, differently configured version of' Linux. Under the hood, they're all roughly the same.

Hope that clarifies things a bit.

---

### Post by supertails on 2008-02-20
I get ya.

---


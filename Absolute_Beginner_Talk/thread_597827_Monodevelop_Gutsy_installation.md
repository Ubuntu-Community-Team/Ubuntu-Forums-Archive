---
title: "Monodevelop Gutsy installation"
date: 2007-10-30
forum: Absolute Beginner Talk
---

### Post by cwmoser on 2007-10-30
Looking for advice on how to install the latest version of MonoDevelop.

The  MonoDevelop website is [www.mondevelop.com](www.mondevelop.com) and they have only a Source Code tarball or an RPM  package.  

If I select the Source Code tarball, I'll have to deal with compiling the package - and all the problems of finding all the libraries and dependencies.  If I select the RPM package, will alien properly convert the package?

Ubuntu repositories will install v0.14 but the latest version is v0.16.

Anyone have any suggestions on the proper way to install MonoDevelop on Ubuntu Gutsy?

Thanks

Carl

---

### Post by rudeboyskunk on 2007-10-30
[http://www.howtogeek.com/howto/ubuntu/install-monodevelop-on-ubuntu-linux/](http://www.howtogeek.com/howto/ubuntu/install-monodevelop-on-ubuntu-linux/)

---

### Post by cwmoser on 2007-10-30
Regarding the website you referenced to install v0.16 MonoDevelop:

[http://www.howtogeek.com/howto/linux/installing-monodevelop-from-source-on-ubuntu/](http://www.howtogeek.com/howto/linux/installing-monodevelop-from-source-on-ubuntu/)



I got this error 127 when I did the "sudo make install" :

Making install in po
make[1]: Entering directory `/home/carl/Ubuntu Linux/Support/MonoDevelop/v0.16/monodevelop-0.16/po'
/home/carl/Ubuntu Linux/Support/MonoDevelop/v0.16/monodevelop-0.16/install-sh -d /usr/share/locale
make[1]: /home/carl/Ubuntu: Command not found
make[1]: *** [install-data-yes] Error 127
make[1]: Leaving directory `/home/carl/Ubuntu Linux/Support/MonoDevelop/v0.16/monodevelop-0.16/po'
make: *** [install-recursive] Error 1
carl@klaatu:~/Ubuntu Linux/Support/MonoDevelop/v0.16/monodevelop-0.16$ 

Using a previous project I have that worked under Feisty MonoDevelop v0.15, this version of MonoDevelop complains "Unknown language 'C#')"


Any help is appreciated.

Carl

---


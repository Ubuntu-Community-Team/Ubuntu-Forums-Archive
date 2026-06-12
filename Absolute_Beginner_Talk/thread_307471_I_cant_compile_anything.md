---
title: "I cant compile anything"
date: 2006-11-26
forum: Absolute Beginner Talk
---

### Post by thelocust on 2006-11-26
I cant install any tar files. I cd to the file I extracted the tar file and I ./configure in terminal and this is what I get...

```
bob@mybox:~/downloads/programs/kxdocker/kxdocker-configurator-1.0.2$ ./configure
checking build system type... Invalid configuration `i686-pc-linux-oldld': machi                                                                                                   ne `i686-pc-linux' not recognized
configure: error: /bin/sh admin/config.sub i686-pc-linux-oldld failed
bob@mybox:~/downloads/programs/kxdocker/kxdocker-configurator-1.0.2$ [3;2~

```

Thanks for any help you can give.](*,)

---

### Post by LLRNR on 2006-11-26
Do you have **build-essential** installed ?

---

### Post by lobstaman on 2006-11-27
Have you tried using the instructions from [http://www.supriyadisw.net/2006/03/kxdocker-on-dapper-drake](http://www.supriyadisw.net/2006/03/kxdocker-on-dapper-drake) ? They worked quite well for me.

BTW - you can install kxdocker directly without compiling it ... I believe its in the universe repository.

Good Luck!

---

### Post by duality on 2006-11-27
You need these packages:
sudo apt-get install build-essential linux-headers-$(uname -r)

Just type those commands to install the tools needded.

Then go to the source directory and type "./configure ; make ; make install"

You will probably need special libraries for the source code to compile, check the documentation for how to compile it, i just mention the tools.

---


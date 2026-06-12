---
title: "How to install Sun jdk?"
date: 2006-12-06
forum: Absolute Beginner Talk
---

### Post by matthewyoung on 2006-12-06
Here is what I did:

```
chmod u+x jdk-1_5_0_10-linux-i586-rpm.bin
sudo ./jdk-1_5_0_10-linux-i586-rpm.bin
...
error: Failed dependencies:
        glibc >= 2.1.2-11 is needed by jdk-1.5.0_10-fcs.i586
        sh-utils >= 2.0-1 is needed by jdk-1.5.0_10-fcs.i586
        fileutils >= 4.0-8 is needed by jdk-1.5.0_10-fcs.i586
        gawk >= 3.0.4-1 is needed by jdk-1.5.0_10-fcs.i586
        textutils >= 2.0-2 is needed by jdk-1.5.0_10-fcs.i586
        /bin/sh is needed by jdk-1.5.0_10-fcs.i586

```

I can apt-get fileutils and gawk. How can I install glibc, sh-utils and /bin/sh?

Is this the right way to install the JDK?  What about the existing /usr/bin/java

---

### Post by taurus on 2006-12-06
You can use automatix2 to install java on your system...

[http://getautomatix.com/wiki/index.php?title=Installation#Installing_on_.28K.2CX.29Ubuntu_6.10_i386.2Camd64_.28Edgy.29](http://getautomatix.com/wiki/index.php?title=Installation#Installing_on_.28K.2CX.29Ubuntu_6.10_i386.2Camd64_.28Edgy.29)

---

### Post by mscclr3 on 2006-12-06
sudo apt-get install sun-java5-jdk

If you care to use the command line instead

---


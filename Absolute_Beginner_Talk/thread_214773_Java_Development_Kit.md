---
title: "Java Development Kit"
date: 2006-07-13
forum: Absolute Beginner Talk
---

### Post by crystal on 2006-07-13
Is it okay to modify the instructions given in:
[ How to install J2SE Runtime Environment (JRE) with Plug-in for Mozilla Firefox](http://ubuntuguide.org/wiki/Dapper#How_to_install_J2SE_Runtime_Environment_.28JRE.29_with_Plug-in_for_Mozilla_Firefox)
by replacing with:
```
sudo aptitude install sun-java5-jdk sun-java5-plugin
```

In other words, does sun-java5-jdk include sun-java5-jre, or must I also install the jre?

---

### Post by gmatt on 2006-07-13
The SDK comes with the JRE. To install the firefox plugin you can usually just do it through firefox, unless you are running amd64.

I would think you have to install the JRE seperately of the SDK however, in the sense that you setup all the proper linkage (i.e. link the jre/bin/java to /usr/bin/java)

---

### Post by crystal on 2006-07-13
> The SDK comes with the JRE. To install the firefox plugin you can usually just do it through firefox, unless you are running amd64.
Thanks for the information :)

> I would think you have to install the JRE seperately of the SDK however, in the sense that you setup all the proper linkage (i.e. link the jre/bin/java to /usr/bin/java)
I see. Is that all the installation I need to do?

---

### Post by crystal on 2006-07-13
Oh, looks like that manual installation isnt required too.

All I needed to do was enter:
```
sudo update-alternatives --config java
```
then select Sun's Java package.

---

### Post by gmatt on 2006-07-13
Great stuff glad you got it working. I always just do it manually :mrgreen:

---


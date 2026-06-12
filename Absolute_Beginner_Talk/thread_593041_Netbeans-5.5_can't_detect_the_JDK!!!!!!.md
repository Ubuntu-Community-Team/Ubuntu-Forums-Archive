---
title: "Netbeans-5.5 can't detect the JDK!!!!!!"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by theoldnyx on 2007-10-26
I Downloaded the netbeans-5_5_1-linux.bin
and i have installed these sun-java packages :
java-common                                     install
libhsqldb-java                                     install
libjaxp1.2-java                                   install
libjline-java                                         install
libservlet2.3-java                               install
libxalan2-java                                      install
libxerces2-java                                   install
libxt-java                                              install
openoffice.org-java-common                      install
sun-java6-bin                                   install
sun-java6-fonts                                 install
sun-java6-jdk                                   install
sun-java6-jre                                   install
sun-java6-plugin                                install

and once i start installing netbeans

 Initializing InstallShield Wizard........
 Searching JVM........      
 No Java Development Kit(JDK) was found on this system.
does any one know why this is happening?

---

### Post by kast on 2007-10-26
I do have JDK installed correctly. How can I make the installer use it?

Run the installer with the-is:javahome <path-to-jdk>option.

If you believe you have the JDK installed properly, but the installer seems to fail to recognize it, you can try to run the installer with the-is:javahomeoption and specify the path to the JDK you want the installer to use. Example Linux:-is:javahome /usr/jdk/jdk1.5.0_06Windows: -is:javahome "C:\Program Files\Java\jdk1.5.0_06" Note surrounding double quotes if path contains space(s). 


Source
[http://wiki.netbeans.info/wiki/view/FaqInstallJavahome](http://wiki.netbeans.info/wiki/view/FaqInstallJavahome)

---


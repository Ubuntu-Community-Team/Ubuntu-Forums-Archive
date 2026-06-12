---
title: "Where to find java"
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by Drewat17 on 2007-06-14
Well i went to the java website and found the java i think i need but there are 4 to choose from can anyone help. [http://java.com/en/download/linux_manual.jsp?locale=en&host=java.com:80](http://java.com/en/download/linux_manual.jsp?locale=en&host=java.com:80)

that its where i went. and i run 6.06

---

### Post by overdrank on 2007-06-14
> **Drewat17 said:**
> Well i went to the java website and found the java i think i need but there are 4 to choose from can anyone help. [http://java.com/en/download/linux_manual.jsp?locale=en&host=java.com:80](http://java.com/en/download/linux_manual.jsp?locale=en&host=java.com:80)

that its where i went. and i run 6.06

Hi you can try automatix at getautomatix.com. :popcorn:

---

### Post by imspecial on 2007-06-14
automatix isn't supported by ubuntu in anyway so I would caution against using that....

you can get it by going into synaptic, search for sun-java and download sun-java-6. If you are not developing any java apps you will only need sun-java6-jre  sun-java6-plugin sun-java-bin

also after installing java, you will need to change your default java which can be done using 

```
sudo update-alternatives --config java
```

and then selecting sun-java-6 (or it may be written as 1.6.0)

---

### Post by Bablefish on 2007-06-14
Actually there is an easy way to find java just go to Add Remove and search for it.

---

### Post by zvacet on 2007-06-14
synaptic<search box>type **sun** and you will see all java versions available with synaptic.Select one you want to install and that is it.

---

### Post by Inxsible on 2007-06-14
you probably want the latest java. This will install the java jdk jre and the plugin

```
sudo aptitude install sun-java6-jdk sun-java6-jre sun-java6-plugin
```

---


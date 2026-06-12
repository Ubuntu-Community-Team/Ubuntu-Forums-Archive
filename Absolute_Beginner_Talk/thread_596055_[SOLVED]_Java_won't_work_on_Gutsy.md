---
title: "[SOLVED] Java won't work on Gutsy"
date: 2007-10-29
forum: Absolute Beginner Talk
---

### Post by BOZG on 2007-10-29
Having some problems setting up Java on Gutsy. I've checked through some of the other threads but I haven't found anything that works.

I installed Java with 
```
sudo apt-get install sun-java6-jre
```

which installed sun-java6-common and sun-java6-bin with it.  I then enabled the ubuntu-restricted extras package for the firefox plugin.  Everything worked ok but whenever I open a website with Java installed, firefox goes grey, freezes and takes about 30 seconds to recognise that Java is installed but even when it does, it stays grey.  Any suggestions?

---

### Post by Baby Boy on 2007-10-29
Are you using 64-bit Ubuntu?

---

### Post by Inxsible on 2007-10-29
you need to install the mozilla plugin for java.

---

### Post by taurus on 2007-10-29
Try installing the plugin package as well.

```
sudo apt-get install sun-java6-plugin
```
Then, restart firefox and in the address field, type

```
about:plugins
```
to check to make sure you have java plugin.

---

### Post by BOZG on 2007-10-29
Worked fine with the ```
sudo apt-get install sun-java6-plugin
```


Thanks.  I thought it should have worked fine if I just installed the restricted extras package but it's fine now. :)

---

### Post by mrmonkeyman on 2007-11-03
I have the same problem except that having installed the java plugin package did not fix it. I checked which version is running with the update-java-alternative command and it is 1.6 and checked about:plugins in firefox and it shows java 1.6. Java -version even shows 1.6 but I still get blank or gray pages and am using kubuntu 32 bit gutsy.

---


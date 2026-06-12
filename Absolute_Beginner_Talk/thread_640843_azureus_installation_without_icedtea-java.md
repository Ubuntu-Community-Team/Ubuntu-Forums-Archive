---
title: "azureus installation without icedtea-java"
date: 2007-12-14
forum: Absolute Beginner Talk
---

### Post by noorez on 2007-12-14
When I tried to install azureus with synaptic, it asked for the java package icedtea-java. I checked the dependencies and the first line looked like this:

icedtea-java7-jre | sun-java6-jre | sun-java5-jre

I already have downloaded Java 6 myself using the .bin download from Sun's website. I created a package called 'Java6u3.deb' and installed it. I also put in the provides section
java-compiler, java-runtime, java6-runtime so that the system knows that Java is installed.

How can I install azureus then without having to install either icedtea-java or sun-java6-jre ?

---

### Post by Pumalite on 2007-12-14
Better try Deluge.

---

### Post by Jet8225 on 2007-12-14
You could download azureus form a package at packages.ubuntu.com. Seach for it using the search function and if it says it has a problem with dependencies then download that dependency separate and try to download azureus again.

---

### Post by Pumalite on 2007-12-14
If you are not a purist, you can also try ktorrent. It's great.

---

### Post by taurus on 2007-12-14
Transmission.

---


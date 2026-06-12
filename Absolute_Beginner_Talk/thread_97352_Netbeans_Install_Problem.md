---
title: "Netbeans Install Problem"
date: 2005-11-30
forum: Absolute Beginner Talk
---

### Post by mitchy_g on 2005-11-30
Hi,

Im trying to install netbeans from the Linux Binary file I got from the website.

I ran the .bin file by using the folloing command : sudo ./netbeans-4_1-linux.bin

All is well when the installation start, however a few seconds later i get this:

"The wizard cannot continue because of the following error: could not load wizard specified in /wizard.inf (104)"

The netbeans website says if this problem occurs to: "Temporarily remove jre/lib/endorsed/sax.jar from the JDK directory during IDE installation."

However I cannot find the sax.jar file. Any ideas?

(i installed jdk via synaptic)

Thanks for your help
Mitch

---

### Post by amohanty on 2005-12-01
sudo updatedb
locate -e sax.jar

HTH
AM

---


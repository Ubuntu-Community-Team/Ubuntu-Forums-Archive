---
title: "Installing java repo way vs non-repo way"
date: 2007-11-12
forum: Absolute Beginner Talk
---

### Post by noorez on 2007-11-12
I would like to update my java installation.  I looked in the repo's and found sun-java6, however, when I checked the dependencies there was quite a lot of them! However, If I go to Sun's website to download the .bin file for java, I can install it quite easily. I would only have to extract it and then set up a few symbolic links to the executables. So why does the repo way need all the dependencies ?

And a sort of relate question: can make-jpkg work on sun java 6? it says that it was made for sun java 5...

---

### Post by jfinkels on 2007-11-12
Installing java using ```
sudo aptitude install sun-java6-jre
``` will install the runtime environment and will automatically install the java6 architecture-dependent binaries. What other dependencies do you want to know about? Most are required libraries and Debian package management utilities and such. You can read about any package by doing ```
apt-cache show sun-java6-jre
``` 

The Sun .bin installer probably just installs both the runtime environment and the binaries.

---

### Post by noorez on 2007-11-20
So then for the repo installation, why would everything have been split up like it has been? Why not just have a package that represents exactly what Sun distributes? What is the reasoning behind dividing up the package into multiple ones?

---


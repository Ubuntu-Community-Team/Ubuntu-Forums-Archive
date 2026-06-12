---
title: "Java Installation Problem"
date: 2007-08-16
forum: Absolute Beginner Talk
---

### Post by esthrim on 2007-08-16
Hi, i need help with my java installation which is not working.
(i'm newbie in ubuntu and java) 

here is my steps :

1.i download RPM package j2sdk & j2re update 2 from sun java download.
2. i convert RPM Package to DEB with alien.
3. i install the DEB file which is success.

but when i  run : java -version
the version is 1.4.2 ....gjc...

and when i run : sudo update-alternatives --config java
it says that only 1 java installed, and nothing to configure.

in synaptic, the j2sdk which i installed has "jdk" name not j2sdk.... and "jre" not j2re....

how is to fix this problem?

thanks.

---

### Post by Elegorod on 2007-08-16
I also can't install Java in this way.
Now you can install sun-java6-jdk from Synaptic (it's old version, which was released a half of year ago), then unpack RPM contents to the installation folder (shown in Synaptic after installation in package properties).
This works for me.

---

### Post by HereInOz on 2007-08-16
Just install the J2re1.4 version using synaptic and when it is installed, you create a symbolic link from the firefox plugin directory - in feisty this is /usr/lib/firefox/plugins - that links to the libjava_oji.so file which is installed by the J2re1.4 installation.

Again, the location of this file may change with various versions, but check out this site:

[http://plugindoc.mozdev.org/faqs/firefox-linux.html#install-java](http://plugindoc.mozdev.org/faqs/firefox-linux.html#install-java)

for some clues as what to do.

---

### Post by Elegorod on 2007-08-16
J2re1.4 ?
In this thread we install JavaSE 1.6 update 2. Java 1.4 is very old version. But thanks for Firefox issue.
For Opera, enter URL opera:config, select Java, enter JVM Home Directory, and press Save button.

---


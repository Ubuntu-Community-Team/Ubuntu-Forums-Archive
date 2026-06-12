---
title: "java install"
date: 2009-04-17
forum: Alabama Team - US
---

### Post by staylor29a11 on 2009-04-17
i have javas rpm.bin dowloaded ( i am new to ubuntu) I need to find out how to install this java package to my pc so i can view it in mozilla. Can anyone help me? :)  Any help will be greatly appreciated. 

samantha
[email]samafayla33@aim.com[/email]

---

### Post by Tim Sharitt on 2009-04-17
The easiest way to install Java on Ubuntu is to install it from the repositories.

You can install sun-java6-jre and sun-java6-plugin with Add/Remove in the Applications menu or Synaptic. 

Alternately, You can install via the command line with

```
sudo apt-get install sun-java6-jre sun-java6-plugin
```

---

### Post by jcorriher on 2010-04-08
I have tried over and over to install java.  Running the above commands do not work for me.  I receive this error:

Package sun-java6-jdk is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-jdk has no installation candidate

Any ideas?

---

### Post by 23dornot23d on 2010-04-08
Its in Synaptic ..... and loads from there .... no problems .... you should be able to select it and apply it

Administration - Synaptic Package Manager .....

[IMG]http://i39.tinypic.com/dr61t.jpg[/IMG]

---

### Post by garvinrick4 on 2010-04-09
> **jcorriher said:**
> I have tried over and over to install java.  Running the above commands do not work for me.  I receive this error:

Package sun-java6-jdk is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-jdk has no installation candidate

Any ideas? Install your partners repository that is where java resides.

---


---
title: "Where is Java?!"
date: 2007-06-17
forum: Absolute Beginner Talk
---

### Post by datavirtue on 2007-06-17
I could have sworn I read that Java came with Ubuntu.

Also I cannot change properties on a file?  Tried to make the JRE install executable but could not.

I can figure this stuff out myself but I was evaluating Ubuntu for the computer illiterate.

As a system with no Java (doesn't run JAR files) it is of little use to me.

Sean

---

### Post by meborc on 2007-06-17
short answer here - [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_J2SE_Runtime_Environment_.28JRE.29_v6.0_with_Plug-in_for_Mozilla_Firefox](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_J2SE_Runtime_Environment_.28JRE.29_v6.0_with_Plug-in_for_Mozilla_Firefox)

---

### Post by datavirtue on 2007-06-17
Now why can't I change file properties?  I saw nothing about root on installation.

Sean

---

### Post by weel on 2007-06-17
> **datavirtue said:**
> Now why can't I change file properties?  I saw nothing about root on installation.

Would you care to explain exactly what you did, what you expected to happen, and what did happen? I'm not saying this to be nasty, but simply because I'm having a hard time guessing.

---

### Post by meborc on 2007-06-17
java is in the repos... you just need to enable the extra repositories... like in the link i posted... it is quite easy ;)

---

### Post by daxumaming on 2007-06-17
Sorry you're experiencing this problem, but it can easily be resolved by issuing the command to download Java, it'll only take a few minutes anyway.
```

sudo aptitude install sun-java6-jre

```

---

### Post by datavirtue on 2007-06-17
I tried to run the Java install (.bin) from a Windows Share over Samba.  Not cool.

I copied it to my Ubuntu machine and it works fine.

Sean

---


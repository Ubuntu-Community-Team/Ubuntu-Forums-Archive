---
title: "Firefox crashes after installing java"
date: 2006-07-03
forum: Absolute Beginner Talk
---

### Post by james016 on 2006-07-03
Hi there

I have the issue as in the thread title. I have downloaded and unpacked the latest Java installation from the Sun website (1.5.0_07). I have followed their instructions on how to create a symbolic link which works. But when I go to verify the installation Firefox crashes. Even crashed trying to access this forum. Everything is fine when I remove the link from Firefox's plugin folder.

I have also installed the java package from the Add/remove thing in the Applications menu but I'm not sure where it installed to or what to do next with it.

Am I doing something wrong when trying to make the symbolic link or am I missing something?

I am very new to this, only installed Ubuntu today.

Thanks :)

---

### Post by Jagot on 2006-07-03
Try:

```
sudo update-alternatives --config java
```

---

### Post by james016 on 2006-07-03
I get this and I chose 3, default was 2
  Selection    Alternative
-----------------------------------------------
      1        /usr/bin/gij-wrapper-4.1
 +    2        /usr/lib/jvm/java-gcj/jre/bin/java
*     3        /usr/lib/jvm/java-1.5.0-sun/jre/bin/java

Sites that need java still come up with needing the missing plugin

---

### Post by Jagot on 2006-07-03
Ok, some linkage is required then.  For me, this works:

```
mkdir -p /home/jagot/.mozilla/plugins

cd ~/.mozilla/plugins

ln -s /usr/lib/jvm/java-1.5.0-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so libjavaplugin_oji.so

sudo ln -s /usr/lib/jvm/java-1.5.0-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib/firefox/plugins/
```

---

### Post by james016 on 2006-07-03
I actually got it working on my own. I was using the ns7gcc29 folder rather than the ns7 folder as you have in your linkage.

Thank you very much for your replies. :)

---

### Post by Jagot on 2006-07-03
That's fine - glad you got it working!

---


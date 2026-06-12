---
title: "Getting rid of stuck install packages."
date: 2010-12-02
forum: Apple Hardware Users
---

### Post by Symbolix on 2010-12-02
I tried to install sun Java 6.0. And it kind of worked. But I think one or two packages failed to install and they are stuck somehow somewhere in a package queue. Any time I try to install something, I get:
```
 Setting up sun-java6-doc (6-14-0ubuntu1.8.04) ...
This package is an installer package, it does not actually contain the
JDK documentation.  You will need to go download one of the
archives:

    jdk-6u10-docs.zip jdk-6u10-docs-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    http://java.sun.com/javase/downloads/

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort]
```

How can I get rid of this?

---

### Post by krishnandu.sarkar on 2010-12-02
Enable partner repository. (As you didn't stated what version of Ubuntu are you using I can't tell you the exact menu location)

Lucid : System > Administration > Software Sources

Maverick : Application > Software Center. Edit > Software Sources.

Now on terminal run sudo apt-get install sun-java6-jre sun-java6-jdk sun-java6-plugin

---

### Post by Symbolix on 2010-12-02
Ah sorry :)
It is Ubuntu 8.04.4.

I think Java 6.0 installed properly. It was only that doc that failed. I think it reported that it failed in the taskbar... it should be ok now.

I can only see the error when installing a new package.

Thanks.

---

### Post by krishnandu.sarkar on 2010-12-02
Why don't you consider installing it using apt-get from repository??

BTW consider upgrading your version :P

---

### Post by Symbolix on 2010-12-04
Ah! I wish upgrading was an option, but no. I am stuck with this kernel. I can get full OpenGL for my AT X1600 only with this version of Ubuntu. And everything is rock-solid stable only with this kernel and driver combination. This is an old mac A1151.

---


---
title: "do i have a rootkit?"
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by mills on 2007-04-25
i think i found a rootkit

messin with chkrootkit after i just downloaded it and found something

Searching for OBSD rk v1... /usr/lib/security
/usr/lib/security/classpath.security

so i opened the file and found these five lines at the bottom

```
security.provider.1=gnu.java.security.provider.Gnu
security.provider.2=gnu.javax.crypto.jce.GnuCrypto
security.provider.3=gnu.javax.crypto.jce.GnuSasl
security.provider.4=gnu.javax.net.ssl.provider.Jessie
security.provider.5=gnu.javax.security.auth.callback.GnuCallbacks
```

so googled the lot of em and found this one ominous site

[http://metastatic.org](http://metastatic.org)

can someone allay my fears and tell me that everyone has a
usr/lib/security/classpath.security

---

### Post by kerry_s on 2007-04-25
I would love to tell you, but i don't have a usr/lib/security/classpath.security
But that doesn't mean it's a root kit.
What version of java do you have installed?

---

### Post by mills on 2007-04-25
java-6-sun-1.6.0.00

this seems to be the source code if any  programmers are interested

[http://metastatic.org/source/gnu-crypto-jessie-2.patch.txt](http://metastatic.org/source/gnu-crypto-jessie-2.patch.txt)

does chkrootkit often throw out wrong information?

---

### Post by mills on 2007-04-25
also chkrootkit found these files

Searching for suspicious files and dirs, it may take a while... 
/usr/lib/jvm/.java-6-sun.jinfo
/usr/lib/jvm/java-6-sun-1.6.0.00/.systemPrefs
/usr/lib/firefox/.autoreg
/lib/modules/2.6.20-15-generic/volatile/.mounted

i cant reply for an hour or so, i gotta pop out

thanks in advance for any help on this for any help on this

---

### Post by hyperair on 2007-04-25
I also have that classpath.security file. I doubt it's a rootkit though. ^^ It looks like an innoucous java package file.

---

### Post by mills on 2007-04-25
yeah looks like it is, i just found this and it says its a false positive

[http://www.safranek.hu/docs/local/chkrootkit/README.FALSE-POSITIVES](http://www.safranek.hu/docs/local/chkrootkit/README.FALSE-POSITIVES)

false alarm everyone
(phew)

---

### Post by klytu on 2007-04-25
> **mills said:**
> i think i found a rootkit

messin with chkrootkit after i just downloaded it and found something

Searching for OBSD rk v1... /usr/lib/security
/usr/lib/security/classpath.security

so i opened the file and found these five lines at the bottom

```
security.provider.1=gnu.java.security.provider.Gnu
security.provider.2=gnu.javax.crypto.jce.GnuCrypto
security.provider.3=gnu.javax.crypto.jce.GnuSasl
security.provider.4=gnu.javax.net.ssl.provider.Jessie
security.provider.5=gnu.javax.security.auth.callback.GnuCallbacks
```

so googled the lot of em and found this one ominous site

[http://metastatic.org](http://metastatic.org)

can someone allay my fears and tell me that everyone has a
usr/lib/security/classpath.security

I have that file, but it only contains the line: > security.provider.1=gnu.java.security.provider.Gnu which is the same as the first line of your file. I am using J2RE Standard Edition build 1.5.0_06-b05.

---

### Post by mills on 2007-04-25
iam pretty sure its not a rootkit

just me jumping the gun a bit thats all

---

### Post by casey.marshall on 2007-05-02
My website is ominous? I had no idea...

That's not a rootkit, it's a configuration file for GNU Classpath, which is a free reimplementation of the Java class libraries, and it is a part of the GNU project.

Ubuntu gives you a few choices on the Java runtime you can install; you can install the (still) non-free one from Sun, or you can install the GNU GCJ runtime. You can also select which one to use through the alternatives system. GNU GCJ compiles Java programs directly to native code, and there are some programs (for example, the Java compiler from Eclipse) that can be installed as native binaries, instead of as class files that are launched with a JIT.

[http://www.gnu.org/software/classpath/](http://www.gnu.org/software/classpath/)
[http://gcc.gnu.org/java/](http://gcc.gnu.org/java/)

Cheers.

-- Casey "ominous classpath hacker" Marshall

---


---
title: "Need help clearing out an old apt install"
date: 2008-02-13
forum: Absolute Beginner Talk
---

### Post by dhtseany on 2008-02-13
Hi all,

I hadn't realized that I already installed Java 6 when I was trying to install Java5 from apt. I exited terminal thinking that it had only downloaded the need files but not yet began the install. Wrong. Check out the following:
```

root@lcsws001:/home/sean# apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  sun-java5-bin sun-java5-jre
Suggested packages:
  sun-java5-plugin ia32-sun-java5-plugin sun-java5-fonts
The following NEW packages will be installed:
  sun-java5-bin
The following packages will be upgraded:
  sun-java5-jre
1 upgraded, 1 newly installedl, 0 to remove and 5 not upgraded.
1 not fully installed or removed.
Need to get 0B/29.9MB of archives.
After unpacking 83.5MB of additional disk space will be used.
Do you want to continue [Y/n]? n
Abort.

```

How do I get rid of that Java installation (sun-java5-bin)?

Thanks for any help I can get :)

Peace
Sean

---

### Post by dhtseany on 2008-02-13
*Bump

I'm sure this isn't hard ya'll :)

---

### Post by kellemes on 2008-02-13
Well, you need to find out what packages are depending on sun-java5-bin and sun-java5-jre.. and remove those packages if you really want to get rid of java 5.
You can use "aptitude" for this.

---

### Post by dhtseany on 2008-02-14
Thanks for the reply! 

How would I use apt to figure that out?

Thanks,

Sean

---

### Post by kaiju on 2008-02-14
with apt, you can do an
```
apt-cache show sun-java5-bin
```
or whatever package you want to look up. in the output, there is an entry for dependencies.

---

### Post by dhtseany on 2008-02-15
Thanks for the responses, but here is what I did to fix the issue:

First, since I had Java6 already installed, I canceled the Java5 install. This made the Java5 install hang in limbo. So I did the following:

```

$ sudo apt-get remove sun-java5-bin

```

Then after I removed that I decided it was probably best to remove Java6 and reinstall it too:
```

$ sudo apt-get remove sun-java6-bin
---Removed it... ----

$sudo apt-get install sun-java6-bin

```

Everything now seems to be back to normal!

Thanks for all the help!

Peace

Sean

---


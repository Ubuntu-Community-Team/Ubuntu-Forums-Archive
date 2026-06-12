---
title: "G3 Pismo java 1.5 install help"
date: 2007-08-03
forum: Apple PPC Users
---

### Post by vector on 2007-08-03
hi all
I need some help installing a latter Java on my G3. Im running ubuntu dapper 6 and the laptop was given to me with the OS already installed and working. So far its been great.
powerbook G3 Pismo.

I went to install PCgen yesterday and it crashed (see error below) the pcgen install instructions say to check the java version, saying it needed Java 1.5 or higher. I have not contacted PCGen yet as I dont have 1.5 installed.

java -version gives me 
```
 java -version
java version "1.4.2"
gij (GNU libgcj) version 4.1.0 (Ubuntu 4.1.0-1ubuntu8)
```


apt-get gij tells me its the latest 

When I was given the laptop the owner mentioned that later versions of ubuntu may not support this older laptop. Does this mean that I am stuck with java 1.4? Is there no way of upgrading it? I am not sure if things on the laptop had to be fiddled above and beyond the standard dapper ppc install in order to get them to work so im a little apprenhisve of digging too deep.

```
uname -a
Linux nudibranch 2.6.15-23-powerpc #1 Tue May 23 13:46:54 UTC 2006 ppc GNU/Linux
```



```
~~~~~~~~error given by pcgen
 ./pcgen.sh
Exception in thread "main" java.awt.AWTError: Cannot load AWT toolkit: gnu.java.awt.peer.gtk.GtkToolkit
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.7)
   at pcgen.util.Logging.<clinit>(Unknown Source)
   at java.lang.Class.initializeClass(libgcj.so.7)
   at pcgen.core.Main.dieWithBadEntryPoint(Unknown Source)
   at pcgen.core.Main.main(Unknown Source)
Caused by: java.lang.ClassNotFoundException: gnu.java.awt.peer.gtk.GtkToolkit
   at java.lang.Class.forName(libgcj.so.7)
   at java.lang.Class.forName(libgcj.so.7)
   at java.awt.Toolkit.getDefaultToolkit(libgcj.so.7)
   ...4 more
```

---

### Post by Auria on 2007-08-03
See PowerPC FAQ

[https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ)

you currently have GCJ - it's the open-source java implementation, but not the best. Sun does not release a PPC version of Java for linux, so you cannot install it. But you can install IBM's VM, which is better than GCJ i believe (never tried myself)  see section "Java, video codecs, and DVD playback" - package seems to be called "ibm-j2re1.5"

might not work in version 6 though (and... what version 6? there are 2: 6.06 and 6.10)

---

### Post by vector on 2007-08-03
Ok
follwoing the instructions at [https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ)  --Java, video codecs, and DVD playback
I added medibuntu to the sources .list.

/etc/apt/sources.list
```
deb-src http://au.archive.ubuntu.com/ubuntu dapper main restricted

deb http://au.archive.ubuntu.com/ubuntu dapper-updates main restricted
deb-src http://au.archive.ubuntu.com/ubuntu dapper-updates main restricted


deb-src http://au.archive.ubuntu.com/ubuntu dapper universe

deb http://archive.ubuntu.com/ubuntu/ dapper multiverse universe main restricted
deb-src http://au.archive.ubuntu.com/ubuntu dapper multiverse


deb http://medibuntu.org
```


then i did the 
```
  wget - q -http://packages.medibuntu.org/medibuntu-key.gpg -0- |sudo apt-key add -
gpg: no valid OpenPGP data found.
```

any thoughts?

---

### Post by vector on 2007-08-03
hang on i didnt get the rpo addition right

---

### Post by vector on 2007-08-03
ok instead i went to the medibuntu site and did this


```
echo "deb http://packages.medibuntu.org/ dapper free non-free" | sudo tee -a /etc/apt/sources.list
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

which seemed to work as expected.

the next step would be
```
sudo apt-get install ibm-j2re1.5 ppc-codecs libdvdcss2
```

however i get 
```
sudo apt-get install ibm-j2re1.5 ppc-codecs libdvdcss2
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package ppc-codecs
```

and yes to a previous question its dapper drake 6.06 LTS

---

### Post by vector on 2007-08-03
ok i 

sudo apt-get install ibm-j2re1.5

only thinking that was the one i needed in this case

which tooka while but it installed ok.

however pcgen did no better same as original error

---

### Post by vector on 2007-08-04
I take it following this wont help cause mines a powerpc??

[http://ubuntuguide.org/wiki/Dapper#How_to_install_J2SE_Runtime_Environment_.28JRE.29_with_Plug-in_for_Mozilla_Firefox](http://ubuntuguide.org/wiki/Dapper#How_to_install_J2SE_Runtime_Environment_.28JRE.29_with_Plug-in_for_Mozilla_Firefox)

---

### Post by Auria on 2007-08-04
> **vector said:**
> ok i 

sudo apt-get install ibm-j2re1.5

only thinking that was the one i needed in this case

which tooka while but it installed ok.

however pcgen did no better same as original error

okay you installed the IBM VM, but you still have GCJ installed too, so probably GCJ still takes over IBM's VM - i'm not sure how to tell which one to use as i don't have Java insatlled at all on my linux computer, but someone else should be able to tell (or just uninstall GCJ if you don't need it)

the link you pointed is a firefox plugin for sun's java, so no it won't work. to get IBM's Java working in the browser, there are steps described at [http://blog.effraie.org/post/2006/10/29/PPC-Java-Plugin-dans-Firefox](http://blog.effraie.org/post/2006/10/29/PPC-Java-Plugin-dans-Firefox)

it's in french though, but appropriate terminal commands are there and can just be executed

(also it is to be noted that IBM's Java is still not as good as Sun's so don't expect miracles - once  again i'm not speaking for myself but quoting what i read elsewhere)

---

### Post by vector on 2007-08-04
managed to break it good n poper now :)

i uninstalled java
```
sudo apt-get remove java-gcj-compat
```

```
sudo apt-get install ibm-j2re1.5 --reinstall
```

in the vain attempt it would re configure or redirect it to this one.
but now i get this.

```

 java -version
JVM not found: libjvm.so  - libjvm.so
```

same result after trying pcgen

searching the cache for jvm turned up a number of hits and Im not sure which one it would be if any

sudo update-alternatives --config java

```

There are 3 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
      1        /usr/bin/gij-wrapper-4.0
      2        /usr/bin/gij-wrapper-4.1
*+    3        /usr/lib/j2re1.5-ibm/jre/bin/java


```
so its using the right one

---

### Post by stmiller on 2007-08-04
Seems like you are all set. But if there are still problems, you can download the PowerPC Linux java directly from ibm.com. Might have to use bugmenot.com to get a login for ibm downloads to avoid spam.

---

### Post by vector on 2007-08-05
but now i get this!!!!!

Code:

 java -version
JVM not found: libjvm.so  - libjvm.so

same result after trying pcgen

searching the cache for jvm turned up a number of hits and Im not sure which one it would be if any

So im not out of the woods yet

do i need to load a jvm? and if so which one?

---


---
title: "Total newb- attempted to install JDK but broke it? help.."
date: 2007-11-07
forum: Absolute Beginner Talk
---

### Post by fredix on 2007-11-07
hello,

well this is my first post here.. and i am in need of a bit of general newbie linux help..


I would like to install the jdk 1.5 however i seem to have wrecked it, quite badly.

I have recently installed gutsy on my ppc and all working smoothly. I downloaded the jdk.bin file from sun, left it on my desktop and executed it. it was running but not showing me any progress or anything. after about 10minutes i thought it was not doing anything maybe stuck or something so i ended the thread! (bad idea i am now guessing)

so i searched a bit and found that you should install this kind of thing in /usr/local/lib/ so mv it there then, when i try to execute it it says

```

.
.
Do you agree to the above license terms? [yes or no] 
        YES
Unpacking...
Checksumming...
0
0
Extracting...
./install.sfx.6462: 1: Syntax error: "(" unexpected
cd: 718: can't cd to jdk1.5.0_13
 
Done.
xxxx@ubuntu:/usr/local/lib$ 


```

I have even tried redownloading the file but no luck, as i thought maybe the file was changed a bit in the half install? any ideas would be great. thanks ......./f

---

### Post by Hospadar on 2007-11-08
you should not use the bin from sun's website.  You should install it from the repositories either use synaptic or install it from the command line ```
sudo apt-get install sun-java5-jdk
```You might want to go into synaptic, search by name for "sun-java5" and look for any java packages you might want to install from there.

Also, I think it's possible that some of the packages conflict with sun-java6 so you might need to uninstall that stuff if you have it installed.

---

### Post by fredix on 2007-11-08
thanks Hospadar,


i have tried to use the synaptic package manager but it does not seem to find the jdk? i have enable all of the options in the software sources.. and when i search for ´sun-java5´ it only gives me a list of 

doc
fonts
jre
source

but no jdk?

also i have just tried ```

x@ubuntu:/usr/local/lib$ sudo apt-get install sun-java5-jdk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sun-java5-jdk is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java5-jdk has no installation candidate
x@ubuntu:/usr/local/lib$ 


```


is there something that i am missing. thanks.../f

---

### Post by MrFSL on 2007-11-08
> fsl@Laptop:~$ apt-cache search java | grep -i jdk
sun-java5-demo - Sun Java(TM) Development Kit (JDK) 5.0 demos and examples
sun-java5-doc - Sun JDK(TM) Documention -- integration installer
sun-java5-jdk - Sun Java(TM) Development Kit (JDK) 5.0
sun-java5-source - Sun Java(TM) Development Kit (JDK) 5.0 source files
sun-java6-demo - Sun Java(TM) Development Kit (JDK) 6 demos and examples
sun-java6-doc - Sun JDK(TM) Documention -- integration installer
sun-java6-jdk - Sun Java(TM) Development Kit (JDK) 6
sun-java6-source - Sun Java(TM) Development Kit (JDK) 6 source files
fsl@Laptop:~$ 


Looks like an apt-get install sun-java5-jdk should do the trick!

I noticed the following:
> fsl@Laptop:~$ clear; apt-cache show sun-java5-jdk 
Package: sun-java5-jdk
Priority: optional
***_Section: multiverse/devel_***
Installed-Size: 11448
Maintainer: Matthias Klose <doko@ubuntu.com>
Architecture: i386
Source: sun-java5
Version: 1.5.0-11-1ubuntu2
Provides: java-compiler, java2-compiler
Depends: sun-java5-jre (= 1.5.0-11-1ubuntu2), sun-java5-demo (= 1.5.0-11-1ubuntu2), libc6, libx11-6
Pre-Depends: debconf (>= 0.5) | debconf-2.0
Suggests: sun-java5-doc, sun-java5-source
Filename: pool/multiverse/s/sun-java5/sun-java5-jdk_1.5.0-11-1ubuntu2_i386.deb
Size: 5046212
MD5sum: 7c88ec36fa6f897cc2f1080d8b68b09f
SHA1: e22dc3559eefe9548d6c5e2d22de58afc7d59acb
SHA256: b84a96071112e28c8bbf259dca370ace2b2f12c276f7e2fc5af34e91c42fde4b
Description: Sun Java(TM) Development Kit (JDK) 5.0
 The JDK(TM) is a development environment for building applications,
 applets, and components using the Java programming language.
 .
 The JDK includes tools useful for developing and testing programs
 written in the Java programming language and running on the Java
 Platform.
 .
 NOTE: You must accept Sun's EULA prior to successfully installing
 this package
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu

fsl@Laptop:~$ 
So I would make sure Multiverse is enabled.

---

### Post by fredix on 2007-11-08
hi thanks for that just tried what you said but still the jdk is not showing up 

```

x@ubuntu:/usr/local/lib$ apt-cache search java|grep -i jdk
icedtea-java7-doc - Icedtea Development Kit (JDK) documentation
icedtea-java7-jre - Java runtime based on OpenJDK
icedtea-java7-source - Icedtea Development Kit (JDK) source files
sun-java5-doc - Sun JDK(TM) Documention -- integration installer
sun-java5-source - Sun Java(TM) Development Kit (JDK) 5.0 source files
sun-java6-doc - Sun JDK(TM) Documention -- integration installer
sun-java6-source - Sun Java(TM) Development Kit (JDK) 6 source files
x@ubuntu:/usr/local/lib$ 

```

as you can see no jdk? also i double checked and i have enabled multiverse, but when it reloaded to check for updates it gets a few errors saying:


[http://ports.ubuntu.com/ubuntu-ports/dists/gutsy/main/source/Sources.gz:](http://ports.ubuntu.com/ubuntu-ports/dists/gutsy/main/source/Sources.gz:) 404 Not Found
[http://ports.ubuntu.com/ubuntu-ports/dists/gutsy/restricted/source/Sources.gz:](http://ports.ubuntu.com/ubuntu-ports/dists/gutsy/restricted/source/Sources.gz:) 404 Not Found
[http://ports.ubuntu.com/ubuntu-ports/dists/gutsy/universe/source/Sources.gz:](http://ports.ubuntu.com/ubuntu-ports/dists/gutsy/universe/source/Sources.gz:) 404 Not Found
[http://ports.ubuntu.com/ubuntu-ports/dists/gutsy/multiverse/source/Sources.gz:](http://ports.ubuntu.com/ubuntu-ports/dists/gutsy/multiverse/source/Sources.gz:) 404 Not Found
[http://ports.ubuntu.com/ubuntu-ports/dists/gutsy-updates/main/source/Sources.gz:](http://ports.ubuntu.com/ubuntu-ports/dists/gutsy-updates/main/source/Sources.gz:) 404 Not Found
[http://ports.ubuntu.com/ubuntu-ports/dists/gutsy-updates/restricted/source/Sources.gz:](http://ports.ubuntu.com/ubuntu-ports/dists/gutsy-updates/restricted/source/Sources.gz:) 404 Not Found
[http://ports.ubuntu.com/ubuntu-ports/dists/gutsy-updates/universe/source/Sources.gz:](http://ports.ubuntu.com/ubuntu-ports/dists/gutsy-updates/universe/source/Sources.gz:) 404 Not Found
[http://ports.ubuntu.com/ubuntu-ports/dists/gutsy-updates/multiverse/source/Sources.gz:](http://ports.ubuntu.com/ubuntu-ports/dists/gutsy-updates/multiverse/source/Sources.gz:) 404 Not Found
[http://ports.ubuntu.com/ubuntu-ports/dists/gutsy-backports/main/source/Sources.gz:](http://ports.ubuntu.com/ubuntu-ports/dists/gutsy-backports/main/source/Sources.gz:) 404 Not Found
[http://ports.ubuntu.com/ubuntu-ports/dists/gutsy-backports/restricted/source/Sources.gz:](http://ports.ubuntu.com/ubuntu-ports/dists/gutsy-backports/restricted/source/Sources.gz:) 404 Not Found
[http://ports.ubuntu.com/ubuntu-ports/dists/gutsy-backports/universe/source/Sources.gz:](http://ports.ubuntu.com/ubuntu-ports/dists/gutsy-backports/universe/source/Sources.gz:) 404 Not Found
[http://ports.ubuntu.com/ubuntu-ports/dists/gutsy-backports/multiverse/source/Sources.gz:](http://ports.ubuntu.com/ubuntu-ports/dists/gutsy-backports/multiverse/source/Sources.gz:) 404 Not Found
[http://ports.ubuntu.com/ubuntu-ports/dists/gutsy-security/main/source/Sources.gz:](http://ports.ubuntu.com/ubuntu-ports/dists/gutsy-security/main/source/Sources.gz:) 404 Not Found
[http://ports.ubuntu.com/ubuntu-ports/dists/gutsy-security/restricted/source/Sources.gz:](http://ports.ubuntu.com/ubuntu-ports/dists/gutsy-security/restricted/source/Sources.gz:) 404 Not Found
[http://ports.ubuntu.com/ubuntu-ports/dists/gutsy-security/universe/source/Sources.gz:](http://ports.ubuntu.com/ubuntu-ports/dists/gutsy-security/universe/source/Sources.gz:) 404 Not Found
[http://ports.ubuntu.com/ubuntu-ports/dists/gutsy-security/multiverse/source/Sources.gz:](http://ports.ubuntu.com/ubuntu-ports/dists/gutsy-security/multiverse/source/Sources.gz:) 404 Not Found

is this the problem? if so any ideas?

what i also would really like to know is why the downloaded jdk.bin from sun does not work anymore? in my first post after i terminated the thread it must have left some files somewhere? is there anyway to clean that up? or is there somehting else i am missing to enable to see the jdk in the synaptic? thanks....../f

---


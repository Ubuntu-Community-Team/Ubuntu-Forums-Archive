---
title: "Install Java On Ubuntu"
date: 2007-02-27
forum: Absolute Beginner Talk
---

### Post by dulbelajardul on 2007-02-27
How to Install Java on Ubuntu but my PC is an offline PC

---

### Post by taurus on 2007-02-27
You need to download it from another PC that is connected to the net from Sun's site.  Then, transfer it to your machine with a USB thumbdrive or a CD.  Install it by hand after that.

---

### Post by Gregory_NZL on 2007-10-20
I tried installing the Java JDK on Ubuntu 7.10 with apt-get unfortunately it failed for me. 

I did some more searching around and found these manual instructions which are valid for both Ubuntu and Debian. 
[http://wiki.serios.net/wiki/Debian_Java_JRE/JDK_installation_manually](http://wiki.serios.net/wiki/Debian_Java_JRE/JDK_installation_manually)


**These are the commands I used to install the Java JDK binary**

You have to dowload the latest Java JDK (in this case, jdk-6u3-linux-i586.bin) from the Sun Java site.

Change directory to /usr/local/lib

```
cd /usr/local/lib
```

From there extract the JRE or JDK archive file you downloaded:

```
sudo sh /some/path/jdk-6u3-linux-i586.bin
```

In the above commands, replace /some/path with where the JRE/JDK .bin/.tgz resides and of course replace the filename with what it actually is in your case.

Now create some symlinks so that the executables can be run easily. Change directory to /usr/local/bin

```
cd /usr/local/bin
```

From there execute the following set of commands:

```
sudo ln -sf ../lib/jdk1.6.0_03/bin/* .
```
        
Pay attention to the period at the end of the command, it is required. And adjust the directory as well to what you have (e.g. jdk1.6.0_03 for the Sun Java 1.6.0_03 JDK).

3 Verify installation

To verify that the installation was successful, execute

```
java -version
```

The output should look something like this if everything is well

```
java version "1.6.0_03"
Java(TM) SE Runtime Environment (build 1.6.0_03-b05)
Java HotSpot(TM) Client VM (build 1.6.0_03-b05, mixed mode, sharing)
```

---


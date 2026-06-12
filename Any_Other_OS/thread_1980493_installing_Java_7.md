---
title: "installing Java 7"
date: 2012-05-15
forum: Any Other OS
---

### Post by HappyLinux on 2012-05-15
I've been searching the internet trying to find out how to solve this, but to no avail. So I'm hoping someone in here can point me in the right direction.

I'm currently on Mint 12, but will be moving up to Mint 13 in due time. However, I'm posting in this section because it might be relevant to whomever has this sort of problem with Ubuntu 12.04.

I currently have install sun-java6-plugin and sun-java6-re (installed by default upon installing Mint, instead of OpenJDK6).

The thing is, I would like to update to Oracle Java 7, not OpenJDK7.

The thing is, I've previously found that the OpenJDK just doesn't cut it with some of my needs. Some of the websites that I go to check to see what version of Java I'm running, and they don't recognise OpenJDK, and thus don't work, but they do with Sun/Oracle.

So until I update to Mint 13, how do I update to Oracle Java 7? I don't want the development part, just the runtime part.

Searching the web keeps yielding results for Java6 and OpenJDK, and even articles that are several years old.

I've downloading the Java7 package from [www.java.com](www.java.com) for my 64bit OS just in case.

Oh yes, I also found an article that Ubuntu 12.04 comes default with OpenJDK, and that if you want Java7 instead, you have to manually deactivate OpenJDK, then uninstall it, then remove excess files, then download the files from the Java website, install, and then activate it.

That seemed somewhat confusing as I thought it was a matter of just going to the software manager and uninstall OpenJDK. No faffing about with deactivation etc.

Well, can anyone help??

---

### Post by TBABill on 2012-05-15
[http://www.ubuntugeek.com/how-to-install-oracle-java-7-in-ubuntu-12-04.html](http://www.ubuntugeek.com/how-to-install-oracle-java-7-in-ubuntu-12-04.html)

---

### Post by QIII on 2012-05-15
You don't need to purge OpenJDK if you already have it.  In fact, I would keep it because it is open source.  You might want to remove the IcedTea plug in if you wish.

You can have as many JRE/JDKs as you want and switch between them.

See my post here

[http://ubuntuforums.org/showthread.php?t=1977358](http://ubuntuforums.org/showthread.php?t=1977358)

If you only want the JRE, you should install that from the Oracle website.  However, unlike the this suggestion and the one above, you will have to manually install updates as Oracle makes them available.

---

### Post by Perfect Storm on 2012-05-15
Moved to Other OS/Distro Talk.

---

### Post by Haghiri75 on 2012-05-15
use free java runtime environment:

```

$sudo apt-get install openjdk-7-jre 

```and for browser plugin:
```

$sudo apt-get install icedtea6-plugin

```and SDK:
```

$sudo apt-get install openjdk-7-jdk

```

---

### Post by QIII on 2012-05-15
The OP said he did not want OpenJDK, but Oracle Java.

---

### Post by HappyLinux on 2012-05-15
> **TBABill said:**
> [http://www.ubuntugeek.com/how-to-install-oracle-java-7-in-ubuntu-12-04.html](http://www.ubuntugeek.com/how-to-install-oracle-java-7-in-ubuntu-12-04.html)

I read through the comments and noticed that people have been having trouble after following the instructions given on the page. I don't want that hassle.

---

### Post by HappyLinux on 2012-05-15
> **QIII said:**
> You don't need to purge OpenJDK if you already have it.  In fact, I would keep it because it is open source.  You might want to remove the IcedTea plug in if you wish.

You can have as many JRE/JDKs as you want and switch between them.

See my post here

[http://ubuntuforums.org/showthread.php?t=1977358](http://ubuntuforums.org/showthread.php?t=1977358)

If you only want the JRE, you should install that from the Oracle website.  However, unlike the this suggestion and the one above, you will have to manually install updates as Oracle makes them available.

I don't have OpenJDK and IcedTea installed anyway, so switching between them isn't important. I'll manually install/update if I have to, I just don't know how when it comes to Java. I downloaded what Oracle provides, but it's in many files, across several folders/directories.

---

### Post by HappyLinux on 2012-05-15
> **Haghiri75 said:**
> use free java runtime environment:

```

$sudo apt-get install openjdk-7-jre 

```and for browser plugin:
```

$sudo apt-get install icedtea6-plugin

```and SDK:
```

$sudo apt-get install openjdk-7-jdk

```

I'm not interested in OpenJDK because it doesn't work with what I do.

---

### Post by HappyLinux on 2012-05-15
> **QIII said:**
> The OP said he did not want OpenJDK, but Oracle Java.

Ah, you beat me to the punch. Oops.

---

### Post by craig10x on 2012-05-15
I have a very easy solution for you (i use it myself and it is terrific!) by the way, mint 13 does not have the Oracle Java....they are only providing the open source version from now on)...

I have a program that needs the oracle version myself and was delighted to find this mint post:
[http://forums.linuxmint.com/viewtopic.php?f=42&t=93052](http://forums.linuxmint.com/viewtopic.php?f=42&t=93052)

It is a pre-packaged deb file that not only INSTALLS the latest version of Oracle Java for you (which is now version 7 by the way) but adds a ppa to your software sources...that means that when there is new version available, it will pop into your updater!....

Just copy and paste the 4 lines shown in this link, one at a time of course (let the terminal do it's thing for each one) and you will be all set...:)

This works in all deb based distros by the way...it is not mint specific...i use it on ubuntu 12.04...

---

### Post by QIII on 2012-05-15
> **HappyLinux said:**
> I don't have OpenJDK and IcedTea installed anyway, so switching between them isn't important. I'll manually install/update if I have to, I just don't know how when it comes to Java. I downloaded what Oracle provides, but it's in many files, across several folders/directories.

As I said in the post cited, the process is done for you in three easy commands in the terminal.  The creators of the two available PPAs have scripted the whole process.  I know for certain the webupd8 PPA works fine, as I use it exclusively.

There is no need for you to figure out what to do with a bunch of files.

Just execute the three commands and you are done.

You will get Oracle Java, not OpenJDK.

---

### Post by HappyLinux on 2012-05-17
> **craig10x said:**
> I have a very easy solution for you (i use it myself and it is terrific!) by the way, mint 13 does not have the Oracle Java....they are only providing the open source version from now on)...

I have a program that needs the oracle version myself and was delighted to find this mint post:
[http://forums.linuxmint.com/viewtopic.php?f=42&t=93052](http://forums.linuxmint.com/viewtopic.php?f=42&t=93052)

It is a pre-packaged deb file that not only INSTALLS the latest version of Oracle Java for you (which is now version 7 by the way) but adds a ppa to your software sources...that means that when there is new version available, it will pop into your updater!....

Just copy and paste the 4 lines shown in this link, one at a time of course (let the terminal do it's thing for each one) and you will be all set...:)

This works in all deb based distros by the way...it is not mint specific...i use it on ubuntu 12.04...

Ack, it's a shame Mint is switching to OpenJDK instead of sticking with Oracle.

As for the rest, cheers. It would be most helpful.

---

### Post by HappyLinux on 2012-05-18
Oops, I forgot to mark this thread as closed.

---


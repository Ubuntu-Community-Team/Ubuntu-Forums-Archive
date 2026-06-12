---
title: "Limewire + !(JRE) = fail;"
date: 2005-10-09
forum: Absolute Beginner Talk
---

### Post by nerdman on 2005-10-09
```

Starting LimeWire...
Java exec not found in PATH, starting auto-search...
ls: /usr/lib/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.4.x or newer from http://www.java.com
ls: /usr/java/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.4.x or newer from http://www.java.com
ls: /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.4.x or newer from http://www.java.com

```

...I figured it needed java, LW for windows updates your JRE on install.
I can apt-get new software.
I can even try and wget and unzip it.

but how do I download a .bin file and install it?

---

### Post by karuptdata on 2005-10-09
Download the .bin file from sun's website. Open terminal and type in chmod a+x j2refilename, then in terminal as well type ./j2refilename and it will launce the file in terminal for you to agree on terms and things like that..say yes of course.After that finishes extracting in terminal type cd / then type mkdir /usr/java now all you have to do is move the extracted contents from .bin so move the entire directory to usr/java..So the final directory for your java should go /usr/java/jre1.5.0_04 for example the relaunch lime wire aND YOU SHOULD BE FINE..

---

### Post by nerdman on 2005-10-09
bingo. Many thanks. Now for some gnutella fun...

---

### Post by rxmoi on 2005-10-18
Hi,

Don't you also to add the /etc/java/bin to the PATH in some (like UNIX login) file? I have made the JRE installation but fail to find the java command. I have updated the PATH in /etc/profile, but it does not "bite". Apparently this is not the correct place. Tips are welcome!

/Mike

---

### Post by patrick295767 on 2005-10-18
[QUOTE=nerdman]```

Starting LimeWire...
Java exec not found in PATH, starting auto-search...
ls: /usr/lib/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.4.x or newer from http://www.java.com
ls: /usr/java/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.4.x or newer from http://www.java.com
ls: /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.4.x or newer from http://www.java.com

```

...I figured it needed java, LW for windows updates your JRE on install.
I can apt-get new software.
I can even try and wget and unzip it.

but how do I download a .bin file and install it?[/QUOTE]



You can try that :
[http://www.ubuntuforums.org/showthread.php?p=424626#post424626](http://www.ubuntuforums.org/showthread.php?p=424626#post424626)

---


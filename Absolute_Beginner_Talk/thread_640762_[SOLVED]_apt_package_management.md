---
title: "[SOLVED] apt package management"
date: 2007-12-14
forum: Absolute Beginner Talk
---

### Post by quandary on 2007-12-14
Hi!

Question: I've installed java jdk + plugin etc.  including  sun-java6-doc with apt-get

when installing sun-java6-doc, apt throws this output
```
Setting up sun-java6-doc (6-03-0ubuntu2) ...
This package is an installer package, it does not actually contain the
JDK documentation.  You will need to go download one of the
archives:

    jdk-6-doc.zip jdk-6-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    http://java.sun.com/javase/downloads/

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort] 

```

Now I don't really need all the java docs, so i just don't install it at all.
But now, every time i want to install something (e.g. samba), i get the message above.

```

root@googlebot:~# apt-get install samba
Reading package lists... Done
Building dependency tree       
Reading state information... Done
samba is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up sun-java6-doc (6-03-0ubuntu2) ...
This package is an installer package, it does not actually contain the
JDK documentation.  You will need to go download one of the
archives:

    jdk-6-doc.zip jdk-6-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    http://java.sun.com/javase/downloads/

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort] dpkg: error processing sun-java6-doc (--configure):

```


It's really very annoying. 

So, how can I clean apt, so I don't get the above message anymore?
I know there is some general command, because i used it once when i did install something with libXY-* and it screwed up - unfortunately i forgot the command and can't find it anymore on google...;-)

---

### Post by quandary on 2007-12-14
anybody?

---

### Post by Rocket2DMn on 2007-12-14
If you run 
```
sudo apt-get clean
```
it will clear all downloaded installer files.  Hopefully that should do the trick.

---

### Post by quandary on 2007-12-14
yea, that's what i thought, too. But it doesn't work...

see:

```

root@googlebot:~# apt-get clean
root@googlebot:~# apt-get install samba
Reading package lists... Done
Building dependency tree       
Reading state information... Done
samba is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up sun-java6-doc (6-03-0ubuntu2) ...
This package is an installer package, it does not actually contain the
JDK documentation.  You will need to go download one of the
archives:

    jdk-6-doc.zip jdk-6-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    http://java.sun.com/javase/downloads/

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort] dpkg: error processing sun-java6-doc (--configure):
 subprocess post-installation script killed by signal (Interrupt)
Errors were encountered while processing:
 sun-java6-doc
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@googlebot:~# 


```

---

### Post by llamakc on 2007-12-14
You need to remove that -doc package, and then it will stop prompting you.

apt-get clean 'cleans' out the package cache of downloaded debs and won't fix this issue for you.

---

### Post by Rocket2DMn on 2007-12-14
> **llamakc said:**
> You need to remove that -doc package, and then it will stop prompting you.

apt-get clean 'cleans' out the package cache of downloaded debs and won't fix this issue for you.

I would have thought that clean would remove the sun-java6-doc installer (I didn't think it actually installed).  I agree you should try removing the package.

---

### Post by online_lie on 2007-12-14
Try the snippet below to clean up your repositories. ```
sudo apt-get autoremove
```

---

### Post by llamakc on 2007-12-14
> **Rocket2DMn said:**
> I would have thought that clean would remove the sun-java6-doc installer (I didn't think it actually installed).  I agree you should try removing the package.

Yes, but with the way that dpkg/apt is handled once the package is partially installed (which is what the current situation is) one needs to remove the package.

Also apt-get autoremove is for packages that are no longer depended upon by previously removed packages, or changes in a packages 'depends'.

If 'apt-get remove package' doesn't work, then the OP will have to grab the docs from Sun, put it in /tmp like the instructions say so, and finish installing with `apt-get -f install`

---

### Post by quandary on 2007-12-14
no, autoremove doesn't work either, i already tried that.

but i did that:
apt-get remove sun-java6-doc
and this does the trick... strange.

Anyway, problem solved ;-)

Edit:
Ah, partially removed means autoremove and clean don't work... aha... aaaaaaaaaaaaaaaaaaaaaargh ;-)
What if you're stuck with some hundred of partially installed packages? Just remove them manually ? *lol*

---

### Post by Rocket2DMn on 2007-12-14
> **llamakc said:**
> Yes, but with the way that dpkg/apt is handled once the package is partially installed (which is what the current situation is) one needs to remove the package.

Learn something new every day.

---


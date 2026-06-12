---
title: "Synaptic Problems..."
date: 2008-03-02
forum: Absolute Beginner Talk
---

### Post by BossGreen on 2008-03-02
When I try to open up Synaptic Package manager from the applications tab, i get this message

```
An error occured

The following details are provided:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

```


When i open it from a shortcut i made from the desktop, it lets me open it, but I'm not able to change anything since it says im not the super user.  It normally would ask for the password as soon as i open it and everything would be fine.

---

### Post by BossGreen on 2008-03-02
also...
when i try to run 

```
dpkg --configure -a
```

i get this message

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

---

### Post by kellemes on 2008-03-02
Please try..
```
sudo dpkg --configure -a
```

---

### Post by BossGreen on 2008-03-02
still get the same message

```
nicholas@Nicholas:~$ sudo dpkg --configure -a
[sudo] password for nicholas:
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

(yes my name is nicholas :tongue:

---

### Post by BossGreen on 2008-03-02
Ive tried to get the files it says, but the instructions dont work for me, i think it may be because im on xubuntu rather than something more common?
idk.
Thank you in advance for your help

---

### Post by BossGreen on 2008-03-02
any advice?

---


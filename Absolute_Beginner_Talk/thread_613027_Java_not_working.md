---
title: "Java not working"
date: 2007-11-14
forum: Absolute Beginner Talk
---

### Post by Ub1476 on 2007-11-14
I just noticed now (after using Gutsy since release) that Java doesn't work:(

I've installed the package "ubuntu-restricted-extras".

When I try to enter page with java on it, I get this "install missing plugins". Now, it fails to install automatic, so I did the manual install which didn't work either. 

I'm using Swiftfox and java (and java scripts) is allowed.

Please help:/

---

### Post by taurus on 2007-11-14
Try to install it by hand from a terminal.

```
sudo apt-get update
sudo apt-get install sun-java6-plugin
```

---

### Post by TidusBlade on 2007-11-14
Not sure if it could be this, but I think theres a window that pops up when installing Java, which you gotta scroll down to the end to check the box then it will work, I made that mistake by closing the window immediently. Im using Kubuntu but it shouldnt be any different.

---

### Post by Ub1476 on 2007-11-14
> **taurus said:**
> Try to install it by hand from a terminal.

```
sudo apt-get update
sudo apt-get install sun-java6-plugin
```

Terminal output says that the latest version of sun-java6-plugin is already installed.

> Not sure if it could be this, but I think theres a window that pops up when installing Java, which you gotta scroll down to the end to check the box then it will work, I made that mistake by closing the window immediently. Im using Kubuntu but it shouldnt be any different.

Yes, I think I got that in Fiesty, but there were no license agreement in Gutsy (I'm 100% sure I didn't ignore it). 

_Java still not working.._

---

### Post by taurus on 2007-11-14
What's the output of this command from a terminal?

```
java -version
```
And you did restart firefox after you installed java, right?  Do you see java plugin when you run this in the address field?

```
about:plugins
```

---

### Post by Ub1476 on 2007-11-14
```
java version "1.4.2-02"
Java(TM) 2 Runtime Environment, Standard Edition (build Blackdown-1.4.2-02)
Java HotSpot(TM) Client VM (build Blackdown-1.4.2-02, mixed mode)

```

About: plugins consists of: 

[LIST]
[*]Shockwave Flash
[*]Totem Web Browser Plugin 2.20.0
[*]Windows Media Player Plug-in 10 (compatible; Totem)
[*]DivX® Web Player
[*]QuickTime Plug-in 7.2.0
[/LIST]
There's no sign of Java there.

---

### Post by taurus on 2007-11-14
Why don't you go into synaptic (System -> Administration) and Search for java.  Then, remove the 1.4 version and install sun-java6-bin, sun-java6-jre, and sun-java6-plugin.

---

### Post by Ub1476 on 2007-11-14
They are installed, but I removed 1.4

Still not working though..

java version "1.6.0_03"
Java(TM) SE Runtime Environment (build 1.6.0_03-b05)
Java HotSpot(TM) Client VM (build 1.6.0_03-b05, mixed mode, sharing)

---

### Post by taurus on 2007-11-14
And you do see java plugin in the plugin screen.  What website are you looking at?

---

### Post by Ub1476 on 2007-11-14
"Enable Java" and "Enable JavaScript" is in the plugin tab and checked. I'm testing on the java web check on Java.com now: [http://www.java.com/en/download/installed.jsp?detect=jre&try=2](http://www.java.com/en/download/installed.jsp?detect=jre&try=2)

---

### Post by taurus on 2007-11-14
```
about:plugins
```

---

### Post by Ub1476 on 2007-11-14
Nope, it's not there. Even used Swiftfox search function to double-check.

---

### Post by powder on 2007-11-14
Open terminal and type:
```
ls /usr/lib/firefox/plugins
```

You should see **libjavaplugin.so** in there.  If not...

```
sudo ln -s /usr/lib/jvm/java-6-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib/firefox/plugins/libjavaplugin.so
```

---

### Post by Ub1476 on 2007-11-14
It's there.

```
flashplugin-alternative.so  libtotem-mully-plugin.so
libjavaplugin.so            libtotem-mully-plugin.xpt
libtotem-basic-plugin.so    libtotem-narrowspace-plugin.so
libtotem-basic-plugin.xpt   libtotem-narrowspace-plugin.xpt
libtotem-gmp-plugin.so      libunixprintplugin.so
libtotem-gmp-plugin.xpt

```

---

### Post by powder on 2007-11-14
If you browse to /usr/lib/firefox/plugins and look at the file properties of **libjavaplugin.so**, make sure it is linked to "/usr/lib/jvm/java-6-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so".  Also make sure **libjavaplugin_oji.so** exists.

---

### Post by Ub1476 on 2007-11-14
Everything is there, and it's linked. But I'm using Swiftfox, does it matter?

---

### Post by taurus on 2007-11-14
Are you running Gutsy x86 or x86_64?

---

### Post by Ub1476 on 2007-11-14
I got it to work! Had to change the link (the .so files) to the Swiftfox directory (opt/swiftfox/plugins).

Thanks for your help!:)

---


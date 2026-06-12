---
title: "Manage Apple Airport Wireless Router"
date: 2009-04-29
forum: Apple Hardware Users
---

### Post by spikoley on 2009-04-29
Is there any way in Ubuntu to manage an Apple Airport wireless router?  I believe it has custom software to manage it.  When I try to access it I am able to download the .bin file but cannot run it.  Is there some open source software or a way to run the .bin file?

Thanks.

---

### Post by spikoley on 2009-05-01
I found the solution in this [post]("http://ubuntuforums.org/showpost.php?p=3878625&postcount=4").

**Overview** 

You need to download airport-config and sun-java5-jdk.  The airport-utils program only works with the older version of Java.  If you run airport-config with the new Java it will do nothing and return you to a command prompt.

**Install airport-utils**

```
sudo apt-get install airport-utils
```

**Install Sun Java 5 JDK**

```
sudo apt-get install sun-java5-jdk
```

**Switch to Sun Java 5 JDK**

```
sudo update-alternatives --config java
```

**Select Sun Java 5 JDK**

```

There are 2 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
*+        1    /usr/lib/jvm/java-6-sun/jre/bin/java
          2    /usr/lib/jvm/java-1.5.0-sun/jre/bin/java

```

In this case it is option 2.

**Run airport-config**

```
airport-config
```

The AirPort Base Station Configurator GUI will open and you can control your AirPort.

**Notes**

When you are finished configuring your AirPort you may need to switch your Java version back for other programs to function properly.

---


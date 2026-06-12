---
title: "install Java??"
date: 2007-05-12
forum: Absolute Beginner Talk
---

### Post by ianb72 on 2007-05-12
How do I install the Java plugin??

Ian

---

### Post by kjaggu on 2007-05-12
Please check out [www.ubuntuguide.org](www.ubuntuguide.org)

The best place to find answers for such queries. If u want any further help please post. 

Best of luck!!!

---

### Post by cmost on 2007-05-12
If you want a really painless way, the easiest method I know of is to use Automatix2 to install Swiftfox and it's plugins.  It completely automates the process.

---

### Post by kjaggu on 2007-05-12
> **cmost said:**
> If you want a really painless way, the easiest method I know of is to use Automatix2 to install Swiftfox and it's plugins.  It completely automates the process.

That's right. I forgot. You may even use the Add/Remove application in Ubuntu where your search for Java will turn up some results of which you can select the latest one. I believe its Sun Java 6 or something. 

Install it from there. Its very easy. :)

---

### Post by zvacet on 2007-05-12
> Click Applications &#8594; Add/Remove. In the top right, change the setting to All available applications. Then select Other in the left panel and then select the Ubuntu restricted extras package. Click OK.

Another way is to go to the synaptic and in search box type** sun**.Of course in both cases you need all repositories to be open.
**system>administration>software properties>chek all boxes>reload**

---

### Post by crimesaucer on 2007-05-12
After you have a chosen a way to install Java, I think this wiki page way is the easiest way,

-add extra repositories then in terminal do this:

```
sudo aptitude install sun-java6-jre sun-java6-plugin sun-java6-fonts

```

...then check to make sure you are using it:

```
sudo update-alternatives --config java
```

Just follow the simple directions and choose the latest version that you want to use, enter the number, and press enter. If it's already chosen, then just press enter. Now you know you have it configured and installed.

This is what mine looks like:

```
blah@blah-blah:~$ sudo update-alternatives --config java
Password:

There are 4 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/gij-wrapper-4.0
*         2    /usr/lib/jvm/java-6-sun/jre/bin/java
          3    /usr/bin/gij-wrapper-4.1
 +        4    /usr/lib/jvm/java-gcj/jre/bin/java

Press enter to keep the default[*], or type selection number: 2
Using `/usr/lib/jvm/java-6-sun/jre/bin/java' to provide `java'.
blah@blah-blah:~$ 

```

---


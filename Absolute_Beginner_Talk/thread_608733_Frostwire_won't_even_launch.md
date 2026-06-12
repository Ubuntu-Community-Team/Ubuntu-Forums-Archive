---
title: "Frostwire won't even launch"
date: 2007-11-10
forum: Absolute Beginner Talk
---

### Post by sc2 on 2007-11-10
I either couldn't follow or things didn't work in other threads I've viewed, so I figured I'd make yet another frostwire thread. Sorry guys. :lolflag:

Here is what I get when I type "Frostwire" in the terminal:

```
 will@will-desktop:~$ frostwire
Starting FrostWire...
Java exec found in PATH. Verifying...
OOPS, you don't seem to have a valid JRE. FrostWire works best with Sun JRE available at http://www.java.com
ls: /usr/lib/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.5.x or newer from http://www.java.com
ls: /usr/java/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.5.x or newer from http://www.java.com
ls: /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.5.x or newer from http://www.java.com 
```


I'm using Ubuntu Gutsy, and I installed Frostwire from their site. Suggestions? :/

---

### Post by linuxlizard on 2007-11-10
it's complaining you don't have java. Make sure you have sun-java (search for it in synaptic) installed. I use frostwire and on my system I have:

sun-java6-bin
sun-java6-jre
sun-java6-plugin

all installed. You can search for these in synaptic. Probably you just need to search for sun-java6-jre but if you don't have the other two, they are useful. bin is probably a dependency of jre anyway, but plugin is nice to have if you don't have it.

---

### Post by por100pre1 on 2007-11-10
Have you installed Java:

```
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
```

If that's not enough, try using the installer from the java website.

EDIT: This answer came kind of late.

---

### Post by PmDematagoda on 2007-11-10
If you have installed Java, you may simply be using he wrong JRE, use:-
```

sudo update-alternatives --config java
```

in a terminal to see if you have different JRE's and if so to switch to the latest JRE.

---

### Post by rsambuca on 2007-11-10
Are you using 64bit Ubuntu?  If so, you need a different java to get frostwire to work.

---

### Post by sc2 on 2007-11-10
> **linuxlizard said:**
> it's complaining you don't have java. Make sure you have sun-java (search for it in synaptic) installed. I use frostwire and on my system I have:

sun-java6-bin
sun-java6-jre
sun-java6-plugin

all installed. You can search for these in synaptic. Probably you just need to search for sun-java6-jre but if you don't have the other two, they are useful. bin is probably a dependency of jre anyway, but plugin is nice to have if you don't have it.

That worked! Thanks!

---

### Post by kidguayas on 2007-11-10
I have a similar problem I have a 64-bit machine what Java do I need?
Thanks

---

### Post by rsambuca on 2007-11-10
> **kidguayas said:**
> I have a similar problem I have a 64-bit machine what Java do I need?
Thanks

I gave you the answer in your [other thread]("http://ubuntuforums.org/showpost.php?p=3743649&postcount=7").

---


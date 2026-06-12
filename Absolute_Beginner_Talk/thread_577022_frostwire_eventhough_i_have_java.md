---
title: "frostwire eventhough i have java"
date: 2007-10-15
forum: Absolute Beginner Talk
---

### Post by 001100 on 2007-10-15
helllo I just installed frostwire with java. I installed java from there website and download frostwire for ubuntu from frostwires webste and when I try to launch frost wire it doesn't lauch. and when I try to launch limewire it comes up but it has no interface it has window boarders but no interface. I have java enabled and i tryed turning off desktop effects and then trying to launching them but no luck. can anybody help me??

---

### Post by JustinAllen on 2007-10-15
This is my first time trying to help so here it goes..lol....

If you've installed java run the following command and select the correct version of java jre..

sudo update-alternatives --config java

---

### Post by DoorGunner on 2007-10-15
type frostwire into your terminal and report back with errors if any ;)

and what JustinAllen Said

---

### Post by mndzmyst on 2007-10-21
I also have the same problem. I typed sudo update-alternatives --config java and got this

          1    /usr/bin/gij-4.2
          2    /usr/bin/gij-4.1
*+        3    /usr/lib/jvm/java-6-sun/jre/bin/java

so I'm guessing it should be configured correctly, yet it's not. Look what I get when I run frostwire from the terminal

Starting FrostWire...
Java exec not found in PATH, starting auto-search...[COLOR="Red"]
**OOPS, unable to locate java exec in  /usr/lib/  hierarchy**[/COLOR]
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
ls: /usr/java/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
ls: /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)

See what is highlighted? How come it can't find java in /usr/lib?:confused:

---

### Post by DoorGunner on 2007-10-22
I think I ended up going to the frostwire site and downloading that version to fix the problem.

---


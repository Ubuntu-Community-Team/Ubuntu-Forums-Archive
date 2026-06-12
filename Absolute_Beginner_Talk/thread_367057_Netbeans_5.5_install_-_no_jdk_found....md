---
title: "Netbeans 5.5 install - no jdk found..."
date: 2007-02-21
forum: Absolute Beginner Talk
---

### Post by kane77 on 2007-02-21
I installed the sun-java6-jdk package and wanted to install netbeans...
downloaded the .bin file chmoded +x and ran it

it searches for java virtual machine but fails and outputs this "No Java Development Kit(JDK) was found on this system"

what can I do?? I realy need netbeans...

---

### Post by mahy on 2007-02-21
If everything else fails, you can opt for the NetBeans+JDK bundle installation. :)

EDIT: What does "java -version" say?

btw, kone&#269;ne vidím niekoho zo Slovenska!

---

### Post by kane77 on 2007-02-21
java version "1.4.2-02"
Java(TM) 2 Runtime Environment, Standard Edition (build Blackdown-1.4.2-02)
Java HotSpot(TM) 64-Bit Server VM (build Blackdown-1.4.2-02, mixed mode)

hmm... but why now I installed both the sun -java5 and 6 -JDK!?

does the bundle install on x64??

(aj ja som rad.. :) )

---

### Post by mahy on 2007-02-21
then open the terminal and run

sudo update-alternatives --config java

and select an appropriate option.

---

### Post by kane77 on 2007-02-21
(hejj funguje :D ) dikes
 <translation>
hey thanx it works now!!
</translation> :D
should I remove the other versions? (are they in any way useful/neccessary?)

---

### Post by mahy on 2007-02-21
You can safely remove them :) they're not being used now anyway...

---

### Post by ceelow on 2007-03-06
I'm having the same problem...

Blank screen when netbeans runs, nothing in the screen...
Now I'm new to ubuntu (linux in general), but not to java and I'm sure its java :)  
And ran -> sudo update-alternatives --config java, and choose option three and nothing...

Plus, this version of netbeans came with 1.6.0, which for some reson tells me that the older version I pointed to (/usr/lib/jvm/java-1.5.0-sun/jre/bin/java by the command's story) might not work... 

I installed netbeans by flipping the exec switch in its properties, and then it installed itself in my home dir, ../netbeans and ../jdk1.6.0

So I'm at a loss...  I'm glad I got vmware to work though!

Anyone out there with a solution to this?  PLUS - why doesn't the Add/Remove app or Synaptic have the newer version of java...  Its been out a while...

- c

---


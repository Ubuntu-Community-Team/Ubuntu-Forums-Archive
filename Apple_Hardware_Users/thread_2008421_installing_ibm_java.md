---
title: "installing ibm java"
date: 2012-06-22
forum: Apple Hardware Users
---

### Post by digs on 2012-06-22
anyone manage to install ibm's java sdk/jre at [http://www.ibm.com/developerworks/java/jdk/linux/download.html]("http://www.ibm.com/developerworks/java/jdk/linux/download.html")? it's suppose to be faster than openjdk but all i get is a coredump on execution of the anywhereinstall bin file.

---

### Post by gordintoronto on 2012-06-22
What kind of Apple are you running? And what version of Linux?

---

### Post by QIII on 2012-06-23
Take a look at the link at the left of my signature.  Scroll down past the Oracle Java part.

---

### Post by digs on 2012-06-23
ibm java, not oracle java. ibm has x86 & ppc builds while oracle only has x86. ibm lists 8.04 as supported but 12.04 just coredumps.

---

### Post by QIII on 2012-06-23
I understand that you were not asking about Oracle Java, which is why I said to follow the link at the left of my signature and scroll past the Oracle Java section.  There is an IBM Java section there.

---

### Post by digs on 2012-06-24
if you're talking about medibuntu, then the wiki must be outdated becuz there is no ibm java on medibuntu. the websphere route is also dead.

---

### Post by rsavage on 2012-06-24
There are old packages still in medibuntu [http://packages.medibuntu.org/pool/non-free/i/](http://packages.medibuntu.org/pool/non-free/i/) (click clicking refresh if you get 403 forbidden).

---

### Post by rsavage on 2012-06-24
Can't get the version 7 install anywhere working (it does indeed seem to core dump), but I installed ibm java 6 jre ("install anywhere") okay.  I even got the firefox plugin working:

```

sudo update-alternatives --install /usr/lib/mozilla/plugins/mozilla-javaplugin.so mozilla-javaplugin.so /opt/ibm/java/ibm-java-ppc-60/jre/lib/ppc/libnpjp2.so 1
sudo update-alternatives  --config mozilla-javaplugin.so 

```

I also noticed jamvm is now in precise.

---

### Post by rsavage on 2012-06-24
This [http://www.wikihow.com/Install-IBM-Java-on-Ubuntu-Linux](http://www.wikihow.com/Install-IBM-Java-on-Ubuntu-Linux) is the guide I used to install IBM Java.  I think it could do with some work/updating and integrating into the community wikis by somebody who knows about Java stuff.
 
IBM have a lot of documentation [http://publib.boulder.ibm.com/infocenter/java7sdk/v7r0/index.jsp?topic=%2Fcom.ibm.java.lnx.70.doc%2Fhomepage%2Fplugin-homepage-java.html](http://publib.boulder.ibm.com/infocenter/java7sdk/v7r0/index.jsp?topic=%2Fcom.ibm.java.lnx.70.doc%2Fhomepage%2Fplugin-homepage-java.html)
 
@ QIII
Btw, IBM Java is available for a lot of architectures not just PowerPC [http://www.ibm.com/developerworks/java/jdk/linux/download.html](http://www.ibm.com/developerworks/java/jdk/linux/download.html)

---

### Post by QIII on 2012-06-24
@rsavage:  yes, I am aware if that.  

Anyone can help maintain the wikis.  I do for several wikis, including the Oracle Java section of the Java wiki, which is why I knew there is an IBM Java section there.

You can help keep the IBM section updated with your recent experience to help the community.

---

### Post by rsavage on 2012-06-24
I have no interest in Java. I was just killing time before the football. Sigh.
 
I may migrate the stuff in the PowerPC FAQ over to your wiki though.

---

### Post by rsavage on 2012-06-25
Can anybody point me in the direction of a real-life Java application they use?  I'd like to compare the speed of Zero, Zero/Shark, JamVM, Cacao, IBM before I write anything up in wikis.  Ta.

---

### Post by gordintoronto on 2012-06-25
[http://www.google.ca/url?sa=t&rct=j&q=&esrc=s&source=web&cd=1&ved=0CFgQFjAA&url=http%3A%2F%2Fwww.shiffman.net%2Fitp%2Fclasses%2Fa2z%2Fweek01%2FFleschIndex.java&ei=DAbpT4eHHuXA0AHWxO35DA&usg=AFQjCNE-fG0HtX9oV4Mg1FeoDsfPqoQcjA&sig2=ttAbS6PwG-M25BndVEzfpg](http://www.google.ca/url?sa=t&rct=j&q=&esrc=s&source=web&cd=1&ved=0CFgQFjAA&url=http%3A%2F%2Fwww.shiffman.net%2Fitp%2Fclasses%2Fa2z%2Fweek01%2FFleschIndex.java&ei=DAbpT4eHHuXA0AHWxO35DA&usg=AFQjCNE-fG0HtX9oV4Mg1FeoDsfPqoQcjA&sig2=ttAbS6PwG-M25BndVEzfpg)

It's the first result in Googling: flesch reading index java

---

### Post by rsavage on 2012-06-26
Thanks for the link although I didn't use it in the end.  I had to look up what a flesch reading index was.

I had already found the jmol chemistry program in the repositories.  A quick summary of the VMs with it:

zero sluggish as expected
zero/shark crashed
jamvm very fast
cacao crashed on exit but fast
ibm fast

So I moved on to something bigger and started trying to get runescape working.  jamvm and ibm both worked (they're the only ones I tested) although I can't really say they are acceptably fast.  This is probably because my processor is on the borderline of the requirements and I couldn't get opengl working with the game, but that might be my graphcis card (it doesn't meet the listed specs).  

The ibm plugin seems to work better than the icedtea plugin.

It would be interesting to hear from anybody who uses games on PowerPC as it is something I have never explored before.

The fantastic thing which I discovered trying to get OpenGL to work is that kwin has stopped crashing.  If only I could figure out what i did......

---

### Post by gordintoronto on 2012-06-26
You might also look at Cool Math Games for Kids, Shisen. However, I don't think it will help you judge performance, other than "it works/it doesn't work."

---

### Post by rsavage on 2012-07-08
IBM Java and Openjdk sections have been updated for PowerPC.
 
[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---


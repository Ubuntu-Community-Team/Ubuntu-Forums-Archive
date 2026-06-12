---
title: "Updated to JRE 6.0 question."
date: 2007-02-26
forum: Absolute Beginner Talk
---

### Post by crimesaucer on 2007-02-26
Hello, I just updated to sun-java6-jre from what I had before which was sun-java5-jre with the jre-1_5_0_10-linux-i586.bin update using the java-package and fake root. 

So my question is at the bottom of this short description of what I have done:

I followed the wiki with this:
```
sudo apt-get install sun-java6-jre sun-java6-plugin
```

...then I basically removed my sun-java5-jre and the mozilla plugin in Synaptic, then I removed the jre-1_5_0_10 update in Synaptic, and then used the code:

```
 sudo update-alternatives --config java

```

to change to my java-6-sun like below:

There are 4 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/gij-wrapper-4.0
          2    /usr/bin/gij-wrapper-4.1
 +        3    /usr/lib/jvm/java-gcj/jre/bin/java
*         4    /usr/lib/jvm/java-6-sun/jre/bin/java

Press enter to keep the default[*], or type selection number: 4
Using `/usr/lib/jvm/java-6-sun/jre/bin/java' to provide `java'.


MY QUESTION IS THIS: What is the + sign next option #3 mean? Should I Delete /java-gcj from /usr/lib/jvm or do I need it in there for a reason?

Was /java-gcj part of the java-package I had installed for update _8, _9, and _10? 

Thanks, I'm just trying to make sure that I know what I'm doing instead of just following the wiki and not knowing what certain things are.

---

### Post by sv452 on 2007-03-07
bump

i would like to know the same thing - i have installed java 6 and i did the same except that java1.4 still starts

There are 6 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
      1        /usr/bin/gij-wrapper-4.1
      2        /usr/lib/jvm/java-gcj/jre/bin/java
      3        /usr/lib/jvm/java-1.5.0-sun/jre/bin/java
*+    4        /usr/lib/j2se/1.4/bin/java
      5        /usr/bin/jamvm
      6        /usr/lib/jvm/java-6-sun/jre/bin/java

---

### Post by crimesaucer on 2007-03-07
Did you press selection 6 and enter?

That should enable your java-6-sun which is the new one.  Then there should be a star next to that selection, and when you do this code agian:

```
sudo update-alternatives --config java
```

it should already have the star on your selected #6 java-6-sun from the last time you entered that code and pressed 6 and enter. 

so just press enter to keep it the same (on #6).

If you do what I said, and still have a selection #4 marked with the star, then you should ask an expert about that, cause I wouldn't know what to say.

---


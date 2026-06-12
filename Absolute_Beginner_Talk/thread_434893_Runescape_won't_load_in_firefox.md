---
title: "Runescape won't load in firefox"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by geezerone on 2007-05-06
Hi

Just having problem with runescape getting to the 'starting engine' bit and the bar is about 25% across scren but then nothing happens? I see that CPU is at 100% at this time. Any ideas?

---

### Post by tophatandy on 2007-05-06
in any operating system you will prabably hit 100% cpu usage when running java as it is a processor intensive platform. try selecting a different java (on the detail selection page if they still have that.. idk havent played in a LONG time)

---

### Post by aidanr on 2007-05-06
it's working for me with sun-java6
```
sudo aptitude install sun-java6-plugin
sudo update-alternatives --config java
```

---

### Post by geezerone on 2007-05-06
Thanks for the replies

Strangely, this used to work with Java 1.5 but as I was trying to get Frostwire to work I had Java 6 installed in packages so switched the default  to it to see if this cured the Frostwire problem of crashing when starting up / asking for Chat name. I tried Runescape but now get the loading game engine message :confused: . Must try the Java 6 SE plugin though thanks for the tip - on Windows at present.

BTW, Java seems to cause a fair share of problems with Linux, is there an idiots guide anywhere on this site at all?

Thanks

---

### Post by geezerone on 2007-05-06
Tried java plugin but just stuck at Connecting to update server message. FYI if I start Frostwire with Java 6 I can't see any characters in the search boxes but with 1.5 is ok - wierd!

Any idea how to clear temp files with java control panel also as runescape asks which java u use?

Here is my current java setup:

```
 Selection    Alternative
-----------------------------------------------
      1        /usr/bin/gij-wrapper-4.1
 +    2        /usr/lib/jvm/java-gcj/jre/bin/java
      3        /usr/lib/jvm/java-1.5.0-sun/jre/bin/java
*     4        /usr/lib/jvm/java-6-sun/jre/bin/java

```

**EDIT:  The game does eventually load but takes about 2 minutes!**

---

### Post by tophatandy on 2007-05-08
odd.. well I did make a post a long time ago.. you can look at that if you wish.

that was for java 5,
which I have installed.. not sure about downgrading (as I have never done it before)
sounds like you might have downloaded a bad package..

---

### Post by tophatandy on 2007-05-08
here is my thread..
[http://ubuntuforums.org/showthread.php?t=314535](http://ubuntuforums.org/showthread.php?t=314535)

and it should work.. being that it is just the plugin for firefox, not the runtime enviorment.. I think that JREs are backwards compatible..

---


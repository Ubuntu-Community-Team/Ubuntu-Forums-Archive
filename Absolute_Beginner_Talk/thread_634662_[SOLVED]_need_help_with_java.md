---
title: "[SOLVED] need help with java"
date: 2007-12-07
forum: Absolute Beginner Talk
---

### Post by antisocialist on 2007-12-07
i want to use frostwire which is written in java, based on the limewire core, and i have java but when i ran it in terminal (icon never works idk why) it said that i didnt have java or something, so i installed all the java packages in add/remove and it still doesnt work, can someone please tell me how to get it to work?

thanks in advance,
antisocialist

---

### Post by PmDematagoda on 2007-12-07
What version of Ubuntu do you have? Is it 32 bit or 64 bit?

---

### Post by antisocialist on 2007-12-08
intel, i believe that makes it 32bit right?

---

### Post by PmDematagoda on 2007-12-08
Post the result of:-

```
uname -a
```

---

### Post by antisocialist on 2007-12-08
Linux allan-laptop 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux


thats what i got

---

### Post by PmDematagoda on 2007-12-08
Do:-
```

sudo update-alternatives --config java
```

And post the results as they are.

---

### Post by antisocialist on 2007-12-09
There are 6 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/lib/jvm/java-6-sun/jre/bin/java
          2    /usr/bin/gij-4.2
          3    /usr/bin/gij-4.1
          4    /usr/lib/jvm/java-gcj/jre/bin/java
          5    /usr/lib/jvm/java-1.5.0-sun/jre/bin/java
*+        6    /usr/lib/j2se/1.4/bin/java

Press enter to keep the default[*], or type selection number: 1


i pressed 1

---

### Post by antisocialist on 2007-12-09
and it worked, thanks

---

### Post by PmDematagoda on 2007-12-09
Why were you using J2SE(Blackdown)? It is unsafer than normal Java since it does not have a monitor which means that if a specific web site has a code that would erase the contents of your entire PC your JRE would execute it and cause a lot of damage.

---

### Post by antisocialist on 2007-12-09
because im a newb, i didnt know. also, it would have caused no damage, other then maybe a half hour of my time, my entire computer is backed up, all id have to do is reinstall and restore everything, and im using 6 now

---


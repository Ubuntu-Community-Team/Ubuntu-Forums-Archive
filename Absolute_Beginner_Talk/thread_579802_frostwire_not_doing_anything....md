---
title: "frostwire not doing anything..."
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by kamitsukai on 2007-10-18
i recentley installed frostwire and it ran well for maybe a couple of days but just now it started to not let me type in the search box or anything so i closed it and now im trying to start it again but now when i click on the icon nothing happens...no error nothing i have the latest java and everything installed so i just dont know whats going on!

---

### Post by Hobo Joe on 2007-10-18
Type 'frostwire' in the console, and see if it gives any errors. If it does, post them here.

---

### Post by kamitsukai on 2007-10-18
```
carl@carl-laptop:~$ frostwire
Starting FrostWire...
Java exec found in PATH. Verifying...
OOPS, you don't seem to have a valid JRE. FrostWire works best with Sun JRE available at http://www.java.com
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.5.x or newer from http://www.java.com
ls: /usr/java/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.5.x or newer from http://www.java.com
ls: /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.5.x or newer from http://www.java.com
carl@carl-laptop:~$ 
carl@carl-laptop:~$ 


```

hmmm does this mean i dont have java? so why did it work for a couple of days?:confused:

---

### Post by nickpaton on 2007-10-18
It appears to be a common problem (use search) - have a look at this [typical post]("http://ubuntuforums.org/showthread.php?t=259627")

---

### Post by kamitsukai on 2007-10-18
thnx ill try one of those

[Edit]
worked great i used this command recomended by "ST.x"

```
sudo update-alternatives --config java
```

which then came up with this

```
There are 4 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/gij-4.2
          2    /usr/bin/cacao
          3    /usr/lib/jvm/java-1.5.0-sun/jre/bin/java
*+        4    /usr/lib/jvm/java-gcj/jre/bin/java

Press enter to keep the default[*], or type selection number: 
```

which came up with this

```
Using `/usr/lib/jvm/java-1.5.0-sun/jre/bin/java' to provide `java'.

```

And now everything works great although i still have no idea why it didnt work:confused::lolflag:

---

### Post by nickpaton on 2007-10-18
Great - glad to hear it.

---

### Post by kamitsukai on 2007-10-18
no damn! i havent now all the other applications that use java arent working!!!!
god this is annoying *take's deep breath..... and puts laptop back on desk and away from window*:mad:

---

### Post by nickpaton on 2007-10-18
My smypathies - reading the rest of that link I gave you, most people solved the problem by a Gutsy reinstall due to issues with it.

Sounds a bit drastic to get a couple of programs to work but hey.... us Ubu users have nought better to do somethimes ](*,)

---

### Post by kamitsukai on 2007-10-18
nah ill get the nice I.T guy at college to create me a script so when i click on an application it will auto change the thing that aint workin back or sumin im sure he will think of somthing (he likes my mums cream cakes :P.....incentives help)

---

### Post by nickpaton on 2007-10-18
Any chance of sending a cream cake up to Geordie land by any chance :lolflag:

---

### Post by kamitsukai on 2007-10-18
well with postal strikes an all i can garantee it will get there by about sametime next year? lol, thnx for your help by the way :P

---


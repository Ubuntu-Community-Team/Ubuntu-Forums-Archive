---
title: "Java problem: Could not find libjava.so"
date: 2006-06-18
forum: Absolute Beginner Talk
---

### Post by ulgor on 2006-06-18
I had problems with my SUN Java install, so I decided to completely reinstall it. This time I tried it with Synaptics, installed sun-jre-bin and plugins. 

The installation quit with the message: Could not find Java 2 Runtime Environment, leaving unconfigured.

Then I tried it manually, downloaded the .bin and followed the instructions. The Terminal says "Done." but if I do java -version I get this:
```

ubuntu@ubuntu:/usr/local/jre1.5.0_07$ java -version
Error: could not find libjava.so
Error: could not find Java 2 Runtime Environment.

```

I also configured the Java alternatives using 
```

ubuntu@ubuntu:/usr/local/jre1.5.0_07$ sudo update-alternatives --config java

There are 3 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
      1        /usr/bin/gij-wrapper-4.1
 +    2        /usr/lib/jvm/java-gcj/jre/bin/java
*     3        /usr/local/jre1.5.0_07/bin/java

Press enter to keep the default[*], or type selection number: 3
Using `/usr/local/jre1.5.0_07/bin/java' to provide `java'.

```
That seems to work...

But still:
```

ubuntu@ubuntu:/usr/local/jre1.5.0_07$ java -version
Error: could not find libjava.so
Error: could not find Java 2 Runtime Environment.

```

How can I get my Java install working?!
How can I tell ubuntu that libjava.so ALREADY EXISTS, and where to find it?!
Thanks in advance...

---

### Post by Drakkor on 2006-06-18
I'm pretty new at linux, but got Java from Automatix,it works great ! :p

---

### Post by divague on 2006-06-18
I had the same problem and i did this:
installed sun-java5-plugin with synaptic and in a terminal i put:

sudo update-alternatives --config java

and selected

/usr/lib/jvm/java-1.5.0-sun/jre/bin/java

to find libjava.so:

sudo find / -name libjava.so

---

### Post by ulgor on 2006-06-20
@divag: Thanks, I followed the same steps as you did, including the update-alternatives.

BUT...

I KNOW where my libjava.so is, but my system does not find any Java, even if it was installed correctly with Synaptics... does anyone know how to modify the alternatives and make the system find libjava.so etc.?

---

### Post by pataphysician on 2006-06-20
where is your libjava.so located? mine's in /usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/i386/

---

### Post by ulgor on 2006-06-20
OK, mine is (the current installation) in:
/usr/lib/jvm/jre1.5.0_7/lib/i386

So? :(

---

### Post by ulgor on 2006-06-20
I found a link in: "/etc/alternatives/java_vm" pointing to: 

"/usr/lib/jvm/java-1.5.0-sun/jre/bin/java_vm"

But the target does not exist anymore, propably because I deinstalled an earlier version? Should I create a link to my current installation in: 

"/usr/lib/jvm/jre1.5.0_7/bin/java_vm" 

???
Just guessing, I have no clue how to create or even repair links like that one... any help appreciated...

---

### Post by aragorn2909 on 2006-06-20
ulgor, check your private messages

---

### Post by ulgor on 2006-06-24
OK, once again...

The manual installation and installation with Automatix both worked. The alternatives both show up, like this:
```
There are 2 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
      1        /usr/local/jre1.5.0_07/bin/java
*+    2        /usr/lib/jvm/java-1.5.0-sun/jre/bin/java

Press enter to keep the default[*], or type selection number: 2
Using `/usr/lib/jvm/java-1.5.0-sun/jre/bin/java' to provide `java'.

```

BUT if I try "java -version", it does not work, take a look at this:
```
ubuntu@ubuntu:/usr/local/jre1.5.0_07$ java -version
Error: could not find libjava.so
Error: could not find Java 2 Runtime Environment.

```

I DO have a libjava.so, look...
```
ubuntu@ubuntu:/usr/local/jre1.5.0_07$ find -name libjava.so
./lib/i386/libjava.so

```

But where should I link/copy it? How can I fix that? 
divague says he had the same problem, but hey, what did you do once you found the libjava.so??

I do not need help with installing packages, I need to set them up properly! I need JAVA asap to work on my project, please help me!

---

### Post by raptros-v76 on 2006-06-24
you need the sun-j2re package.

---

### Post by ulgor on 2006-06-24
Thanks for the answers guys, but could you be a little bit more precise? What can I do?

btw: I know that I need the package, but I installed it via Synaptics before, and Automatix is supposed to install it too, right?? Well, Synaptics actually started to say "could not find libjava.so" every time I try to install the sun-jre package... uhm, but how am I supposed to have the libjava.so before installing the package, wuahh! [-(

---

### Post by lu.victor2008 on 2008-06-02
I know this is an old post... but i'm having the exact same problems with java version 6.
Please help

---


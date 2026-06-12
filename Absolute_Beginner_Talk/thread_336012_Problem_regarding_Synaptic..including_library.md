---
title: "Problem regarding Synaptic..including library"
date: 2007-01-11
forum: Absolute Beginner Talk
---

### Post by KsR on 2007-01-11
Hi all,
    I installed a library pacakage for java...libbuoy(libraries for Buoy) using the Synaptic Manger.  The package installed correctly, but when i tried to compile a java program which uses the Buoy libraries, the following error was shown
```
Exception in thread "main" java.lang.NoClassDefFoundError: BWalkthrough/java
```

I understand the the compiler is not able to import the given libraries...but I have no idea on how to do that..:confused: 
java -version command gives
```
java version "1.5.0_08"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_08-b03)
Java HotSpot(TM) Client VM (build 1.5.0_08-b03, mixed mode, sharing)
```

thanks..

---

### Post by usien on 2007-01-11
firstly this is more of a java related question than ubuntu/linux.u need to add appropriate import statements at the beggining of ur code nd specify the appropriate library path at compile time(to the compiler).if u need further details let me know.

---

### Post by KsR on 2007-01-11
yeah.. I understand that this is a java related question..
The code itself is perfect, it has all the import statements, infact the code is of an example from the Buoy website.  
  Actually, the reason why i posted this thread here was that I thought that when I use synaptic to install libraries, they should automatically set/update the CLASSPATH for the libraries...please correct me if I'm wrong..:)

---

### Post by usien on 2007-01-11
by the looks of it, it doesnt :-D

---


---
title: "Java half-working"
date: 2006-07-28
forum: Apple PPC Users
---

### Post by lo_mein_dreams on 2006-07-28
This is a really dumb question, but I haven't slept in too many hours and I don't feel like failing at thinking anymore, so asking here will get me to sleep.

I have just installed ibm's java 1.5.0, and everything works fine (involving it running in opera and the like) but I just can't get the java command to work. My machine says no command exists.


I am running a 900 mhz iBook G3 with xubuntu 6.06.

I know it is something simple, but if anyone knows the answer I will be so happy. I need to get working on learning java for school next year.

---

### Post by T700 on 2006-07-28
How did you install Java and what exactly is the command you're trying?

Paul

---

### Post by lo_mein_dreams on 2006-07-28
I installed java by looking at. [https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java). The exact command I am trying to do is "java /home/matt/Desktop/bluej-213.jar"

---

### Post by georger on 2006-08-04
You probably have to provide the full path to where you/the java installer dumped the java binary. You can use the search for files entry in the places menu to search for javac or java, and then drag the icon to the terminal (it will fill in the path) then put in -jar and your file. If that doesn't work, the java command is probably somewhere like this (if you ran the installer w/ sudo) /opt/JDK1.5/bin/java -jar /home/matt/Desktop/bluej-213.jar. The JDK1.5 part probably isn't correct, but it should be something like that.

---

### Post by APU on 2006-08-04
I also followed the Howto from [https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java) (step by step exactly like it is written there) and now everything works as expected. There seems nothing to be wrong with this tutorial then.

Probably you have forgotten the step where you configure which Java Runtime to use (call "sudo update-alternatives --config java") ?

APU

---

### Post by Jukums on 2007-10-18
make sure you have sun-java5-jdk installed

```
sudo apt-get install sun-java5-jdk
```

tell ubuntu to use sun java 1.5
```
sudo update-java-alternatives -s java-1.5.0-sun
```

cd to the current directory and
```
java -jar bluej.jar
```

or right click bluej file and "open with sun 5.0 runtime"

that should do the trick 
(did for me)

---

### Post by mbechdel on 2007-10-19
> **Jukums said:**
> make sure you have sun-java5-jdk installed

```
sudo apt-get install sun-java5-jdk
```

tell ubuntu to use sun java 1.5
```
sudo update-java-alternatives -s java-1.5.0-sun
```

cd to the current directory and
```
java -jar bluej.jar
```

or right click bluej file and "open with sun 5.0 runtime"

that should do the trick 
(did for me)

Hey, did you do this on powerpc? I only ask because I installed IBM Java fine; however, BlueJ is having problems with it and this would be great if it was your solution.

Thanks,
Max

---

### Post by mbechdel on 2007-10-19
> **lo_mein_dreams said:**
> I installed java by looking at. [https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java). The exact command I am trying to do is "java /home/matt/Desktop/bluej-213.jar"

By the way, to install BlueJ you need to type:

java -jar /home/matt/Desktop/bluej-213.jar

not java /home/matt/Desktop/bluej-213.jar

---

### Post by Jukums on 2007-10-20
mbechdel

I've a Acer Aspire 5051AWXMi with 64 AMD Turon

---


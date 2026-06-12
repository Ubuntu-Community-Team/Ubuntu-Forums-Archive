---
title: "Very very slow?????????"
date: 2007-01-21
forum: Absolute Beginner Talk
---

### Post by Mba7eth on 2007-01-21
Hi all, I used to use windows for my whole life but i thought it is a good idea to try linux. I installed ubuntu and i really like it Except things about java. it is very slow ???? 
Can some one help us here and tell if we can increase its speed in a way or another. 
(I thought using xubuntu when increase the speed but unfortunatly same results :( ) 


Cheers, 
      Fawaz

---

### Post by taurus on 2007-01-21
When you say slow, what exactly is slow?  And if you don't mind, can you post the spec of your machine as well?

---

### Post by Mba7eth on 2007-01-21
I use IBM thinkpad R40 with 1.4 cent CPU, 512 ram. I develop some applet but they are very slow when running. As it take time when i click on a menu, add an icon (this is in the running time). 
So please give me a hand an help :). But the case was not that when using windows in the old days on the same box.

Cheers, 
      Fawaz

---

### Post by maxamillion on 2007-01-21
are you sure you are running Sun-Java5 or are you using gcj/gij? ... I noticed a decent amount of performance gain when running java on linux over windows when using the Sun-Java5, but gij is a little on the slow side.

---

### Post by Zaffe on 2007-01-21
Try This:
List of the alternatives:
```
update-java-alternatives -l
```
Select the last version of java ( if u have it installed)
```
sudo update-java-alternatives -s java-1.5.0-sun
```

More info here: [https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

### Post by Mba7eth on 2007-01-21
```
java version "1.4.2"
gij (GNU libgcj) version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-14ubuntu7)

Copyright (C) 2006 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

```
this is the result of java -version

---

### Post by maxamillion on 2007-01-21
then yes, you have gij and that is why things are slow.... you need to install the Sun Microsystems Java ... [http://ubuntuguide.org/wiki/Ubuntu_Edgy#Java_.26_Non-Media_Browser_Plug-ins](http://ubuntuguide.org/wiki/Ubuntu_Edgy#Java_.26_Non-Media_Browser_Plug-ins)

---

### Post by Mba7eth on 2007-01-21
Thanks alll problem solved
the solution was what zaffe propose :) 

I don't know which is faster now :) hopefully linux :guitar: :guitar: 


Cheers,
     Mba7eth

---


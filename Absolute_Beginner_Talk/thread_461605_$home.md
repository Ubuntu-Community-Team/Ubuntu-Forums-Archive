---
title: "$home"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by cytutchi on 2007-06-01
hi people

i define a home variable at a konsole e.g. export JAVA_HOME=/usr/java/jdk1.5.0_02
then i type:
$JAVA_HOME
and it shows that bash:its a directory and shows the one i set so all good so far
but
if i close the konsole and re-open it and do it again nothing happens,like it forgot the HOME thing!!
well did it???
can i see if it is still set somehow or every time i open it n i will want to set it i'll have to retype it everytime????

Thenx in AdVaNcE!!!

---

### Post by taurus on 2007-06-01
Edit ~/.bashrc

```
kate ~/.bashrc
```
and add this line to the end of it.

```
export JAVA_HOME=/usr/java/jdk1.5.0_02
```
Then, either log out and back in or rehash it.

```
source ~/.bashrc
```

---

### Post by cytutchi on 2007-06-01
Ok then, i suppose that what you said keeps it and makes permanent right?

So what i was doing was just something temporary until the sell closes?

---

### Post by taurus on 2007-06-01
When you add it to a terminal, it's valid on that terminal only until you close it.  So when you close that terminal and open another one, you have to enter that line again.  And if you want to make it so that each time you open a terminal, you don't have to enter that line to set your java, then you want to add that into your ~/.bashrc since each terminal will read ~/.bashrc when it opens.

---

### Post by cytutchi on 2007-06-01
Thenx a lot!!!! :)
working smoothly now!!! :)
though one final question...that file is read only when i open a konsole or every time i start kubuntu??

P.S. on the installation instructions of software they don't mention that clearly but they just say to type the command on the konsole(not the permanently way) i think they should say this stuff cause who wouldnt like to have this permanently????

Anyway problem solved so...Thenx again

---

### Post by taurus on 2007-06-01
Do you have a link to that installation instructions?  Or you can contact the author(s) and request a modification.

---

### Post by cytutchi on 2007-06-01
yes i have some links
i used the instruction you gave me for: MAVEN, APACHE ANT and JAVA_EE_SDK-5_01
they were all saying the temporary way or just to define the $HOME so i suppose also most of the potential users would know what to do...but if u want to have a look for example here it is
the links are:

[http://ant.apache.org/manual/index.html](http://ant.apache.org/manual/index.html)

[http://java.sun.com/javase/6/webnotes/install/jdk/install-linux.html](http://java.sun.com/javase/6/webnotes/install/jdk/install-linux.html)

[http://maven.apache.org/maven-1.x/start/install.html](http://maven.apache.org/maven-1.x/start/install.html)

but i will also ned to use Jetspeed-2 so at least i m learning a lot on the way before i go into deep water :P

---

### Post by cytutchi on 2007-06-06
Although the JAVA_HOME now is correct though

why if i type:

java -version

shows the 1.4.2 instead of the one i just instaled wich is sdk 5.01 ?????

---

### Post by taurus on 2007-06-06
Perhaps you need to configure it first.

```
sudo update-alternatives --config java
```

---

### Post by cytutchi on 2007-06-07
i did that but it produced three results which none is the folder where i installed the java!

How could i delete the one i installed and use sudo apt-get to get it like that and install it by over-riding the default??
or maybe one of them is the one i installed (which i doubt it) cause it should take out the folder under which it is installed right??

---

### Post by taurus on 2007-06-07
I assume you want to remove /usr/java/jdk1.5.0_02.

```
cd /usr
sudo rm -rf java
```

---

### Post by cytutchi on 2007-06-07
Great!!!! :)

first i did this: sudo apt-get install sun-java5-jdk

and then what you said to select which one i wanted n all is coll n on now!!! 

Thanx a lot for your help!!!!!

---

### Post by taurus on 2007-06-07
See which version is your default now.

```
java -version
```

---

### Post by cytutchi on 2007-06-07
N also forgot to say that i had installed it under: /usr/local/java

so just used sudo rm -r <dir>

n then all the above!

Coolio!

---

### Post by cytutchi on 2007-06-07
java -version

java version "1.5.0_06"

but had to select that...cause the default was beeing used again so after the selction i asked for this n now since java -version replies that then i think all is good!!!

P.S. all this to try to install the software called kepler kepler cause i was facing a prob. that prob gone that i had but still another appears n cant use the software :/

---


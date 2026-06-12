---
title: "Help with making java work in my browser"
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by ace-n-wifey on 2007-06-18
I'm sorry if I'm repetative, I've searched the forum and not found a direct answer I can understand to make my java plug in work.  I came across this post to help and tried it:

 HowTo:How to Install Java in Ubuntu/Kubuntu
This tut will allow you to install a java environment that will allow you to run apps on your firefox/konqueror.

We will now install the following Java packages
sun-java6-bin - Contains the binaries
sun-java6-demo - Contains demos and examples
sun-java6-doc - Contains the documentation
sun-java6-fonts - Contains the Lucida TrueType fonts from the JRE
sun-java6-jdk - Contains the metapackage for the JDK
sun-java6-jre - Contains the metapackage for the JRE
sun-java6-plugin - Contains the plug-in for Mozilla-based browsers
sun-java6-source - Contains source files for the JDK

Installing the Java Runtime Environment

1) In terminal, enter the following command:
Code:

sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts

2) Once it downloads the packages and begins the installation, you’ll get a screen that contains the Sun Operating System Distributor License for Java and hit Enter to continue. You’ll see a dialog that asks you if you agree with the DLJ license terms. Select Yes, and hit Enter; the JRE will finish installing.


Aftermath:

First, check that the JRE is properly installed by running the following command from a terminal.
java -version
You should get similar output
java version “1.6.0&#8243;
Java(TM) SE Runtime Environment (build 1.6.0-b105)
Java HotSpot(TM) Client VM (build 1.6.0-b105, mixed mode, sharing)

Making sure java works on Firefox:

Open Firefox and type
Code:

about:plugins

in the address bar and check for java plugin.

~~~~~ I got everything until I check it in Firefox by typing about:plugins, java isn't there and it still won't work for the chat and games I'm trying to use it for.  Can anybody tell me what command to use to make it work right and show up in firefox??? Thank you sooo much in advance!

---

### Post by reset3x on 2007-06-18
I used this guide to get it installed and working... [http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)

Good Luck!!

---

### Post by guardsman85 on 2007-06-18
[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

> 
If you want to use Sun's Java instead of the open source GIJ (GNU Java bytecode interpreter) you need to set it as default. To list installed JVMs: 
 update-java-alternatives -l 
 To select, for example, Sun's JVM as provided in Ubuntu 6.06, run: 
 sudo update-java-alternatives -s java-1.5.0-sun 
 You should also edit **/etc/jvm** and move **/usr/lib/jvm/java-1.5.0-sun** to the top of JVMs offered. 

 
You may need to modify your version number accordingly.

---

### Post by ace-n-wifey on 2007-06-18
I tried to enter those codes in the terminal and it tells me:
update-java-alternatives: directory does not exist: /usr/lib/jvm/java-1.5.0-sun

any suggestions??

---

### Post by Pconfig on 2007-06-18
I just installed it with typing the same commands as you did. Worked fine here. Hm

You might want to try

```
sudo apt-get install j2re1.4-mozilla-plugin 
```

---

### Post by jonward0690 on 2007-06-18
I had to use automatix to install java.

---

### Post by ace-n-wifey on 2007-06-18
what is automatix???

---

### Post by arnieboy on 2007-06-18
> **ace-n-wifey said:**
> what is automatix???
[http://www.getautomatix.com](http://www.getautomatix.com)

---

### Post by guardsman85 on 2007-06-19
> **ace-n-wifey said:**
> I tried to enter those codes in the terminal and it tells me:
update-java-alternatives: directory does not exist: /usr/lib/jvm/java-1.5.0-sun



What's the output when you try the following? (note that $ represents the prompt, not something you need to type)
```
$ cd /usr/lib/jvm
$ ls  
```

---


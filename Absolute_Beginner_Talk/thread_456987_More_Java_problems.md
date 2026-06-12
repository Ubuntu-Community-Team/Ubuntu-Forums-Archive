---
title: "More Java problems"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by Tyke91 on 2007-05-28
meh... i think java just hates my computer


ok. 

when i type in 

```
sudo aptitude update
```

everything seems to work fine

then when i type in

```
sudo aptitude install sun-java6-bin sun-java6-plugin sun-java6-font

```

i get a nasty message that this is only an installer package and that i need to go to sun.java.com to get the files... i went there but i can't find the files it's asking for.



now the strange bit is, i've gone to the add remove programs list thing and both the java 6 web environment and java 6 console are installed on my computer

but when i put 

```
 java -version 
``` 

into the console, it tells me I'm still in java 1.4


what's going on?!






--------------------------
system specs. 
I'm running feisty
processor is intel core duo 2.13 ghz on each cpu
32 bit

---

### Post by justifier on 2007-05-28
is your machine up to date? with all updates?

try instaling by doing 

sudo apt-get install <packages>

to find the packages, and there names, and check they are availble to you do

apt-cache serarch java6

you should get a list, if the above install command doesnt work, use those package names

---

### Post by Tyke91 on 2007-05-28
i just tried that... something still isn't working

```
mykola@TheWinLixBeast-Mykolas:~$ apt-cache search java6
sun-java6-bin - Sun Java(TM) Runtime Environment (JRE) 6 (architecture dependent files)
sun-java6-demo - Sun Java(TM) Development Kit (JDK) 6 demos and examples
sun-java6-doc - Sun JDK(TM) Documention -- integration installer
sun-java6-fonts - Lucida TrueType fonts (from the Sun JRE)
sun-java6-javadb - Java(TM) DB, Sun Microsystems' distribution of Apache Derby
sun-java6-jdk - Sun Java(TM) Development Kit (JDK) 6
sun-java6-jre - Sun Java(TM) Runtime Environment (JRE) 6 (architecture independent files)
sun-java6-plugin - The Java(TM) Plug-in, Java SE 6
sun-java6-source - Sun Java(TM) Development Kit (JDK) 6 source files
mykola@TheWinLixBeast-Mykolas:~$ sudo apt-get install sun-java6-bin
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
sun-java6-bin is already the newest version.
The following packages were automatically installed and are no longer required:
  libcommons-collections3-java libcommons-pool-java liblucene-java eclipse-rcp
  libcommons-el-java junit libregexp-java libcommons-modeler-java
  liblog4j1.2-java libswt3.2-gtk-java libservlet2.4-java libtomcat5.5-java
  libbcel-java ant libcommons-launcher-java libcommons-logging-java
  libcommons-dbcp-java libcommons-collections-java libcommons-beanutils-java
  libgtk1.2-common imlib-base libcommons-digester-java eclipse-platform
  liblucene-java-doc libjsch-java libswt3.2-gtk-jni ant-optional libmx4j-java
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up sun-java6-doc (6-00-2ubuntu2) ...
This package is an installer package, it does not actually contain the
JDK documentation.  You will need to go download one of the
archives:

    jdk-6-doc.zip jdk-6-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    http://java.sun.com/javase/downloads/

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort] no
Abort installation of JDK documentation
dpkg: error processing sun-java6-doc (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 sun-java6-doc
E: Sub-process /usr/bin/dpkg returned an error code (1)
mykola@TheWinLixBeast-Mykolas:~$ 

```

---

### Post by Tyke91 on 2007-05-28
meh... so is there nothing i can do?

---

### Post by justifier on 2007-05-28
anything on that website?

---

### Post by Tyke91 on 2007-05-28
here's the website it wants me to dl from

[http://java.sun.com/javase/downloads/index.jsp](http://java.sun.com/javase/downloads/index.jsp)

i've gotten the file and put it in temp, but it says it must be owned by root.root

---

### Post by odiseo77 on 2007-05-28
> **Tyke91 said:**
> ```
 java -version 
``` 

into the console, it tells me I'm still in java 1.4


what's going on?!

Try the following:

```
sudo update-alternatives --config java
```

And select the number for java5 or java6 (the one you wish) at the prompt.

---

### Post by Tyke91 on 2007-05-28
thanks m8! that did it for me

---

### Post by Tyke91 on 2007-05-28
alright... my java is fully upgraded and ready to go


but


every time i try to install ANYthing i get that wierd

```
his package is an installer package, it does not actually contain the
JDK documentation.  You will need to go download one of the
archives:

    jdk-6-doc.zip jdk-6-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    http://java.sun.com/javase/downloads/

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort] no
Abort installation of JDK documentation
dpkg: error processing sun-java6-doc (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 sun-java6-doc
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

bug.


is there any way to just go to that website, download the files, switch the owner to root, and put them into the /tmp file?

---

### Post by odiseo77 on 2007-05-28
I had a similar problem with the java doc package and what I did was to uninstall it, seems nothing seemed to solve it. Just out of curiosity, what do you need the java-6-doc package for?? (I mean, I think it has some documentation about java and stuff, but it's not necessary to run java).

---

### Post by Tyke91 on 2007-05-28
dunno what i actually need it for... it seems to have icons and such in it...

alright- this is what i've done


I've downloaded the correct docs (found them)

I extracted it to /tmp

i ran 
```
sudo chown root.root /tmp/docs
```

ctrl+alt+backspace 


so now i have that file, owned by root, in my /tmp folder




AND IT'S STILL COMPLAINING THAT I DONT!

---

### Post by Tyke91 on 2007-05-28
so... i've followed all of it's commands to no avail...

is there some sort of fixinstall i need to run?

---

### Post by Tyke91 on 2007-05-28
I've checked online and there doesn't seem to be anyone who knows how to fix this problem...

is there a way to revert back to what i had and try again?

---

### Post by Tyke91 on 2007-05-28
lol... so am i just screwed?

---


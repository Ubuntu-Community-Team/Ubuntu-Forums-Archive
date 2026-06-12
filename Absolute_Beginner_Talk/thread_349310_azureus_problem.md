---
title: "azureus problem"
date: 2007-01-30
forum: Absolute Beginner Talk
---

### Post by syalam on 2007-01-30
Whenever I load up Azureus it automatically closes. Is it just me? If so, is there another good BT client for Linux?

---

### Post by muguwmp67 on 2007-01-30
Nope, not just you.

first time you run it, run it through the terminal:

sudo opt/azureus/azureus

It needs to do this in order to create the configuration files.  After that has been done, you can use the menu to start it.

If you download an azureus update (or plug-in update) you will need to run it as sudo again to install the update.

---

### Post by syalam on 2007-01-30
sudo: opt/azureus/azureus: command not found

---

### Post by muguwmp67 on 2007-01-30
my bad

sudo /opt/azureus/azureus

---

### Post by syalam on 2007-01-30
still no good =(

---

### Post by muguwmp67 on 2007-01-30
Use the file manager to search the filesystem for azureus.  It will appear as a shell script.  Note which directory it is found in (in my case it was /opt/azureus).

then 

sudo (insert your path here)/azureus

---

### Post by morfeibg on 2007-01-30
I had the same problem. I didn't figure out what was causing it, but to recover from it I installed the Azureus from the official web site:

[http://azureus.sourceforge.net/](http://azureus.sourceforge.net/)

It is really easy. You have to download the archive and extract it to the directory where you want. Use the azureus script to start it. You need JVM installed and JAVA_HOME set in order to run it.

---

### Post by anaconda on 2007-01-30
I am quitting azureus and moving to ktorrent. It is about as good, and written in C++, so you dont need java.

In my previous ubuntu-installation azureus worked very well.. but I didn't install it from the repositories... Ktorrent is easier, because it just works. The only thing I haven't found from it is a firewall test. So dont know if my firewall is blocking part of the traffic..

---

### Post by ultima on 2007-01-30
My guess is something to do with Java.

Find and open the program called terminal from your start menu

If Sun Java is not installed enter in the following
```
sudo apt-get install sun-java5-jre
```
press enter
enter your password

Once Java is installed do
```
sudo update-alternatives --config java
```

press enter
enter your password

Then you should see something like
```

There are 2 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/gij-wrapper-4.1
*+        2    /usr/lib/jvm/java-1.5.0-sun/jre/bin/java
```

You will need to choose the number for sun Java in this case number 2

enter the number and hit enter

Now try and run azureus again

---

### Post by mahiyar on 2007-01-30
I had the same problem. I solved it by using this how-to. [http://www.ubuntuforums.org/showthread.php?t=144546&highlight=azureus](http://www.ubuntuforums.org/showthread.php?t=144546&highlight=azureus)

---


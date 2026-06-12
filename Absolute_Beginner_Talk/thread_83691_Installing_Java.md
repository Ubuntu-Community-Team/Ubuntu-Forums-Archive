---
title: "Installing Java"
date: 2005-10-29
forum: Absolute Beginner Talk
---

### Post by jqp on 2005-10-29
I downloaded an RPM of limewire and used alien to install it. After it installed, I'm having trouble running it.  The errors it gives me are related to Java.  I have installed a JRE 1.5.x from java.com.  Here's what Limewire tells me in the terminal.
```
Starting LimeWire...
Java exec found in PATH. Verifying...
OOPS, you don't seem to have a valid JRE. LimeWire works best with Sun JRE avail able at http://www.java.com
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.4.x or newer from http://www.java.com
ls: /usr/java/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.4.x or newer from http://www.java.com
ls: /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.4.x or newer from http://www.java.com

```

If I didn't install Java correctly, what can I do to correct this?

---

### Post by homeboy on 2005-10-29
searchfor automix in wiki. It will install "java" as well as numerous other apps with no problems.

  homeboy

---

### Post by jqp on 2005-10-29
A search for [automix](https://wiki.ubuntu.com//FrontPage?action=fullsearch&context=180&value=automix&fullsearch=Text) in the wiki didn't turn up anything.

---

### Post by jqp on 2005-10-29
Well, I ran the installer again from here:
[http://java.com/en/download/manual.jsp](http://java.com/en/download/manual.jsp)
and I it still doesn't work.  

I installed Azureus, which uses Java, and that works, but limewire doesn't work and the Java plugin for Firefox does not work.  I don't know what to do to get Java installed properly.

---

### Post by jeremy on 2005-10-29
try
sudo update-alternatives --config java
and select sun java

---

### Post by Donnut on 2005-10-29
Java 1.4 is included in breezy, it's in add applications, internet, more programs.

Hope this helps.  It worked for me.

---

### Post by nitricacid on 2005-10-29
1.Download and and save (non-RPM file) file into like '/home/(usrname)/java'
2.Open a terminal window and type 'sudo apt-get install fake root java-package'
3.Then type: 'sudo apt-get fake root make-jpkg (name of java file)'
4.Then Type: 'sudo dpkg -i *.deb

You can also install 'blackdown' from synaptic package manager and then skip step 1.

---

### Post by jqp on 2005-10-29
installing the package from Add Applications > Internet > Java ... , and then the "update-alternatives" command did it.  Thanks a lot!

---


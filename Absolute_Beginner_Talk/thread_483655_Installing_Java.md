---
title: "Installing Java?"
date: 2007-06-25
forum: Absolute Beginner Talk
---

### Post by Tombo5150 on 2007-06-25
I am trying to install java. I need it currently for Frostwire to run, but i know I will need it more in the future. I downloaded, installed, and agreed to terms> sudo apt-get install sun-java5-jre sun-java5-plugin sun-java5-fonts

and when I try and run frostwire [through terminal] I get: Starting FrostWire...
Java exec found in PATH. Verifying...
OOPS, you don't seem to have a valid JRE. FrostWire works best with Sun JRE available at [http://www.java.com](http://www.java.com)
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
ls: /usr/java/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
ls: /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)


Help?

---

### Post by wormser on 2007-06-25
I am not sure this is the issue but there is Java 6 package.  

> sun-java6-jre 

---

### Post by atria on 2007-06-25
```
sudo aptitude install sun-java6-jre
```

if you need firefox java plugin support,
```
sudo aptitude install sun-java6-plugin
```

---

### Post by alecwh on 2007-06-25
I"m having the same problem. I did the things above, but it didn't work. I get:

> Java exec not found in PATH, starting auto-search...
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
ls: /usr/java/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
ls: /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)


---

### Post by Tombo5150 on 2007-06-25
Yes. I enteredthose codes. However, it stills says I need the latest java. Its JDE 1.5.x or something. Can I get this off java's website? If so, how do i install the download file after I download it?

---

### Post by Tombo5150 on 2007-06-25
Ok, a friend found me this link which worked for me! [https://help.ubuntu.com/community/FrostWire]("https://help.ubuntu.com/community/FrostWire")
In there it had instructions on how to get the latest java. It was very simple.

> sudo update-alternatives --config java


Then after that, you selected from the list of which to install and it said to do the one with 'sun' in it. I installed the one that was version 1.5.0 or soemthinglike that. Works fine now, thanks for all the help!:popcorn:

---

### Post by alecwh on 2007-06-25
Thanks Tombo!

---

### Post by SLiguykyle on 2007-06-28
i've tried all this, and this is what i get :(

op:~$ sudo update-alternatives --config java

There is only 1 program which provides java
(/usr/bin/gij-wrapper-4.1). Nothing to configure.

what am i diong wrong? how can i fix it?

---


---
title: "Frostwire wont work"
date: 2008-03-21
forum: Absolute Beginner Talk
---

### Post by jordank on 2008-03-21
No matter what I do, I can't get frostwire to work.

Any suggestions please?

I keep reinstalling the package, but when I try to run it, nothing.

---

### Post by Bachstelze on 2008-03-21
Please, please, *please* be more specific!

What does it do instead of working?

---

### Post by Hospadar on 2008-03-21
You must use the bittorrent!  The power of Sweden can be yours!

Um, I don't really know about your frostwire, I would try running it in a terminal and see if it barfs up some error messages.  Applications->Accessories->Terminal, then type "frostwire"

See if you get some error messages and post em up here


Seriously though, you really should look into bittorrent, my favorite client for linux is "deluge", and azureus is a great solution too, and runs better on windows. (although I prefer utorrent on windows)

[this]("http://thepiratebay.org/") should get you started.

Also bittorent is a lot safer (for you) it's harder to detect and is much nicer on bandwidth for both you and your ISP.

---

### Post by jordank on 2008-03-21
Java exec found in PATH. Verifying...
1.4.2-02
OOPS, your java version is too old [java = 1.4.2-02]
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
ls: /usr/java/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
ls: /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)

---

### Post by jordank on 2008-03-21
When i search JRE on synaptics, it tells me that i have jre5 though, which i thought would be an appropriate java.  What should I do to get java working, how do i update it?

Snakes.

---

### Post by brimondyl on 2008-03-21
Theres been a lot of problems with Java. I installed Iced Tea Java and now Frostwire works great..its in the repositories:)

---

### Post by rocketangel on 2008-03-21
I downloaded frostwire-4.13.5.i586.deb from [http://www.frostwire.com](http://www.frostwire.com) .

I installed the package with the package installer. I opened Terminal and typed frostwire. The error message was the same as yours. 

I went to System > Administration > Synaptic Package Manager. Searching for JRE, I found sun-java5-jre. I right-clicked on sun-java5-jre and clicked Mark for Installation. At least one additional package was highlighted. I clicked Apply. 

After JRE installation, I typed frostwire into the terminal and the installation dialog appeared.

---

### Post by jordank on 2008-03-22
java5 appears to already be installed.  i don't know why it claims to not have the right version of java...

---

### Post by jordank on 2008-03-22
Okay.  Played around in terminal a bit,  What's the problem here?


kristie@kristie-laptop:~$ sudo apt-get install sun-java6-bin sun-java6-jre
Reading package lists... Done
Building dependency tree       
Reading state information... Done
sun-java6-bin is already the newest version.
sun-java6-jre is already the newest version.
The following packages were automatically installed and are no longer required:
  libopenexr2c2a kdelibs-data liblualib50 liblua50
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
kristie@kristie-laptop:~$ sudo apt-get install sun-java6-plugin
Reading package lists... Done
Building dependency tree       
Reading state information... Done
sun-java6-plugin is already the newest version.
The following packages were automatically installed and are no longer required:
  libopenexr2c2a kdelibs-data liblualib50 liblua50
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
kristie@kristie-laptop:~$ frostwire
Starting FrostWire...
Java exec found in PATH. Verifying...
1.4.2-02
OOPS, your java version is too old [java = 1.4.2-02]
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
ls: /usr/java/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
ls: /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
kristie@kristie-laptop:~$ java -version
java version "1.4.2-02"
Java(TM) 2 Runtime Environment, Standard Edition (build Blackdown-1.4.2-02)
Java HotSpot(TM) Client VM (build Blackdown-1.4.2-02, mixed mode)
kristie@kristie-laptop:~$

---

### Post by snkiz on 2008-03-22
uninstall the old version of java don't know why it doesn't do this for you but it doesn't. also I think getdeb has a package try that

---


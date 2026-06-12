---
title: "PPC Java"
date: 2009-05-18
forum: Apple Hardware Users
---

### Post by balt11t on 2009-05-18
This may seem like a stupid question, but I can't get Java installed! I've looked through all the tutorials and guides, but I can't figure any of it out. In the terminal, when I type in java -version, I get this: 
java version "1 .5.0"
gij (GNU libgcj) version 4.2.4 (Ubuntu 4.2.4-1ubuntu3)

This means I have it installed, I just can't do anything with it, like Youtube. Should I uninstall then re-install or what? Thanks!

---

### Post by balt11t on 2009-05-18
Also, when I try what it says here: [https://help.ubuntu.com/community/Java#head-81c3789bc76872336f69a7af90d1759ef38eeb64](https://help.ubuntu.com/community/Java#head-81c3789bc76872336f69a7af90d1759ef38eeb64) it says the openjdk-6-jre can not be installed on my computer type, but it also says it can't download all repository indexes. It can't even find a sun-java6-bin package

---

### Post by mkvnmtr on 2009-05-18
Up until 8.10 there was some IBM java packages that I used. I think they were in the medibuntu repository. I can't find them in 9.04.

---

### Post by balt11t on 2009-05-19
Where can I get Medibuntu at? At the website, there is a PPC download, but when I try to open it I get libstdc++5 error. When I look through my repository there is only a libstdc++6 file for 64 bit computers

---

### Post by jamesstansell on 2009-05-22
Take a look at openjdk-6, which has a ppc version.  It's in the ubuntu repositories, beginning with 8.10.  I like to track the [https://launchpad.net/ubuntu/+source/openjdk-6](https://launchpad.net/ubuntu/+source/openjdk-6) page.

---

### Post by tiresia on 2009-05-22
This could be a way
[http://ubuntuforums.org/showthread.php?t=1116368](http://ubuntuforums.org/showthread.php?t=1116368)

---

### Post by 10011010 on 2009-05-23
Here is the repository HOWTO, it is platform independent, so PPC doesn't matter.


```

Ubuntu 9.04 "Jaunty Jackalope":

sudo wget [http://www.medibuntu.org/sources.list.d/jaunty.list](http://www.medibuntu.org/sources.list.d/jaunty.list) --output-document=/etc/apt/sources.list.d/medibuntu.list



```

```

sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

```


If you run a terminal and execute that, you can use it in aptitude or synaptic/adept, etc...

As far as Java, you may need to enable universe and multiverse in the synaptic repositories to get the sun libs.

---


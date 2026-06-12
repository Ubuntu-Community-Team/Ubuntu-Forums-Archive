---
title: "Java Problems."
date: 2008-05-27
forum: Apple Hardware Users
---

### Post by Scientia on 2008-05-27
Hi. A short while ago i was referred to install the IBM version of Java [http://ubuntuforums.org/showthread.php?t=806987](http://ubuntuforums.org/showthread.php?t=806987) because the conventional version cannot run on my pc's architecture(iBook PowerPC). It installed without a hitch but Java programs still cannot run.

Example: I tried running frostwire.

johanan@johanan-laptop:~$ frostwire
Starting FrostWire...
Java exec found in PATH. Verifying...
OOPS, you don't seem to have a valid JRE. FrostWire works best with Sun JRE available at [http://www.java.com](http://www.java.com) [java = dl]
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
ls: /usr/java/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
ls: /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.5.x or newer from [http://www.java.com](http://www.java.com)
johanan@johanan-laptop:~$ 


Any help?
Thanks, I'm still floundering in the new environment.

---

### Post by TCE on 2008-05-27
I think your problem is you may have another version of java installed on your system.  To use ibm java as your default java just 'sudo update-alternatives --config java.  It should work after that.

---

### Post by jamesstansell on 2008-05-28
I don't use frostwire myself, but I've heard that it is very picky about its JRE.  Other Java applications are likely to work fine with the openjdk-6-jre package.

As for java applets and webstart, there are known deficiencies in the icedtea-gcjwebplugin package,  Are you trying to run any java code other than frostwire?

---

### Post by Scientia on 2008-05-29
I already tried sudo update-alternatives --config java. It still doesn't work, apparently system doesnt register the change or something. I havn't tried anything but frostwire, but i think other java apps don't work either. I'm not using iced tea as it doesnt work either. If you could help me with a flash player too, i'd be very thankful.

---

### Post by TCE on 2008-05-29
I wonder whats wrong with java?  Maybe try installing it again.  I installed ibm java and it works with frostwire.  As for flash the only flash that is possible to install on ppc is gnash.  The newest update i heard works on sites on youtube. Just sudo apt-get install gnash-mozilla-plugin. Also which ibm java are you trying to use jre1.5 or jre1.6.  jre1.6 may not work.

---

### Post by TCE on 2008-05-29
Also one more thing did you type 'java -version' in terminal to make sure everything is properly installed.  If not try 'sudo apt-get install libstdc++5.

---


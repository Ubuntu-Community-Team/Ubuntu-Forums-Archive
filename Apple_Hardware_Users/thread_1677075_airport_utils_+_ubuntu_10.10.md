---
title: "airport utils + ubuntu 10.10"
date: 2011-01-28
forum: Apple Hardware Users
---

### Post by dumble on 2011-01-28
So I installed airport utils

sudo apt-get install airport-utils


I typ in this command to open the utility
airport2-config

because I have the extreme base station.

And guess what, nothing happens..

So what do I do wrong?

---

### Post by linuxopjemac on 2011-01-28
I think you need Java5:
[http://ubuntuforums.org/showthread.php?t=569692](http://ubuntuforums.org/showthread.php?t=569692)

---

### Post by dumble on 2011-01-28
so how do I get java 5? the commands in the other topic you gave me do not work.
$ sudo apt-get install sun-java5-jdk
$ sudo update-alternatives --config java

Do I need other commands?

---

### Post by linuxopjemac on 2011-01-28
there is indeed no java5 for Maverick, maybe this works:
[http://steve-on-sakai.blogspot.com/2010/05/how-to-install-sun-java-15-on-ubuntu.html](http://steve-on-sakai.blogspot.com/2010/05/how-to-install-sun-java-15-on-ubuntu.html)

---

### Post by dumble on 2011-01-29
naah, doesnt seem to work mate

---

### Post by ivanzakharyaschev on 2012-08-05
Or gcj-4.4. gcj-4.4 is said to make airport-utils working.

Unfortunately, in the recent distributions (Ubuntu 12.04), with the newer Java, airport-utils doesn't work -- [https://bugs.launchpad.net/ubuntu/+source/airport-utils/+bug/706623](https://bugs.launchpad.net/ubuntu/+source/airport-utils/+bug/706623) . Even with gcj (4.6).

The code needs to be adapted for new Java.

And there are situations when there is no workaround: say, if you use an ARM computer, you can't run the Windows binary under wine....

---


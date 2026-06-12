---
title: "su password"
date: 2007-09-24
forum: Absolute Beginner Talk
---

### Post by jlyn on 2007-09-24
To install JAVA I need a  password for  su
entering nothing doesn't do the job
nor does the password I use to log on with (I am the only user).
So, what is the su password?
Thanks,

---

### Post by -SpaZ on 2007-09-24
Almost any command with su in it can be replaced by sudo.

---

### Post by original_jamingrit on 2007-09-24
Actually, you can use a
```
sudo su
```
but for any commands you need to enter after that can also be preceeded with a
```
sudo *commandname*
```
It will ask you your superuser password, which should be the same as the password of your first account.

---

### Post by jlyn on 2007-09-24
thanks.  I have to put in a qualifier for sudo - which one do I choose?

---

### Post by kerry_s on 2007-09-24
ubuntu does not use su, there is no root password.
use sudo or sudo su and your password.

java is in the repos.
make sure all your repos are on.

**sudo apt-get install sun-java6-plugin**

it will pull in all the stuff you need

---

### Post by jlyn on 2007-09-24
what is a  repos  and how do I change it's state?

---

### Post by jlyn on 2007-09-24
One last question:  is this  linux   or  linux RPM?
What is the difference?

---

### Post by jlyn on 2007-09-24
One last question:  is Ubuntu composed on  linux   or  linux RPM?
What is the difference?

---

### Post by st33med on 2007-09-24
Do the command:
```
sudo apt-get install sun-java6-plugin
```
As the guy said above in the terminal. It is better than installing from a package.

---

### Post by kerry_s on 2007-09-24
ubuntu is debian based, no rpm, it uses deb's.

you have a package manager to install or remove applications.

administration> synaptic
the command line is> apt-get

read here-> [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by jlyn on 2007-09-24
I did that and it said it couldn't find package sun-java ...
So I checked what came in on the desktop and found it was a 
jre-6u2-linux-i586.bin  
Now what do I do with it?

---

### Post by fedira on 2007-09-24
You can also just try going to Applications > Add/Remove, then at the top, do Show: All available applications, and then type "Java" in the search box. Check off what you were trying to install, then click Apply.

---

### Post by kerry_s on 2007-09-24
open synaptic and turn on all your repos. then click reload, then search java

---

### Post by 3rdalbum on 2007-09-24
If you don't have more than 3 gigabytes of RAM and are running the 64-bit edition of Ubuntu, then you shouldn't be. :-)  Java is proprietary software that Sun has not built for 64-bit operating systems, so that may explain why you can't find it in the repositories.

---


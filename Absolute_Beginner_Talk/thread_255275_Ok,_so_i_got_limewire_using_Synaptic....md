---
title: "Ok, so i got limewire using Synaptic..."
date: 2006-09-11
forum: Absolute Beginner Talk
---

### Post by Sp00ne on 2006-09-11
...and whenever i type ```
limewire
``` into the konsole, i get this: ```
Starting LimeWire...
Java exec found in PATH. Verifying...
OOPS, you don't seem to have a valid JRE. LimeWire works best with Sun JRE available at http://www.java.com
OOPS, unable to locate java exec in  /usr/lib/  hierarchy
You need to upgrade to JRE 1.4.x or newer from http://www.java.com
ls: /usr/java/j*: No such file or directory
OOPS, unable to locate java exec in  /usr/java/  hierarchy
You need to upgrade to JRE 1.4.x or newer from http://www.java.com
ls: /opt/j*: No such file or directory
OOPS, unable to locate java exec in  /opt/  hierarchy
You need to upgrade to JRE 1.4.x or newer from http://www.java.com

```

So i go into Synaptic and search "java". I literally have no idea what i'm meant to be getting to make it work, and going on the Java wesbsite doesn't help either.

---

### Post by xyz on 2006-09-11
Hi there,
Do you have Automatix installed?
It may be the easiest way for you to install Java. Let us know...

---

### Post by ron999 on 2006-09-11
Hi Spoone
I also used automatix to install java.
I think that the only two items you need to install by synaptic though are
java-common
java-gcj-compat
These are the only two java components that are installed on my machine and Limewire works fine for me.

---

### Post by smelly_sox on 2006-09-11
Hi SpOOne,
Error messages R telling U that Limewire wants JRE - a specific type of java. Instructions:
Go to [SUN]("http://www.java.com/en/download/manual.jsp") & download "Linux RPM (self-extracting file)"
Open synaptic, search for & install "alien"
In terminal *cd* to directory where you saved jre-XXX.rpm.bin
*chmod +x jre-XXX.rpm.bin*
*./jre-XXX.rpm.bin*
will exit with errors, that's O.K.
*alien -d --scripts jre-XXX.rpm*
you'll then have a file called "jre-XXX.deb"
*dpkg -i jre-XXX.deb*
*Ctrl + Alt + Backspace*
Log back in & your away

Regards

---

### Post by skymt on 2006-09-11
No. Do not download the RPM, and do not use alien. That's a kludge. There's a much easier way, [here](https://help.ubuntu.com/community/Java). Follow the directions for installing Sun Java, and make sure to select it as the default (directions farther down the page).

---

### Post by ron999 on 2006-09-11
Yes skymt
I too had loads of aggro trying to get java through their website, that's why I ended up using automatix.

---

### Post by Sp00ne on 2006-09-11
@ xyz:

No, i do not have automatix, where can i get it?

@ ron999:

I have those 2, but it doesnt work.

@ smelly_sox:

It doesnt work at "alien -d jre-XXX.rpm" part of what you said to do.

@ skymt:

That does not work at all. It literally does not work.

---

### Post by xyz on 2006-09-11
> @ xyz:

No, i do not have automatix, where can i get it?

Go here:
[www.getautomatix.com](www.getautomatix.com)
and check your private message.

Feel free to ask in case of problem/understanding.
You'll get there!

---

### Post by smelly_sox on 2006-09-11
Sorry SpOOne,
My bad ..
*alien -d --scripts jre-XXX.rpm*

---

### Post by Stone123 on 2006-09-11
Just listen to skymt , don't use automatix and dont use alien.

I bet you missed this part on wiki :
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by RobsterUK on 2006-09-11
I had exactly the same problem with frostwire (based on limewire)

The problem was not that I didn't have java installed, it was that the startup script was looking for it in the wrong place.

If you are sure you have java installed (I did it via Ubuntu Add/Remove programs) try this:

Use the Ubuntu text editor to edit the script runLime.sh
Look for this line:
```
JAVADIR=/usr/lib
```
and change it to
```
JAVADIR=/usr/lib/jvm
```

---

### Post by smelly_sox on 2006-09-11
I'd be interested to know why NOT to use alien to convert SUN's reference java package?

---

### Post by Sp00ne on 2006-09-11
Thanks for all your replies, Smelly_sox: i did what you said to do, and now it works.

I owe you one.



Im also getting automatix, just incase.

---

### Post by xyz on 2006-09-11
Well I'm glad to hear that! Just use what works for you!
I always do that (esp. in cases where I don't have sufficient know-how yet!) and then I gladly follow other ways, other people's advice!
There's always something to learn.

---


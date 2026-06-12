---
title: "Opera"
date: 2006-07-27
forum: Absolute Beginner Talk
---

### Post by Ryan H on 2006-07-27
I'm running Ubuntu Drapper Drake 6.06 LTS 64-bit edition. I tried to install 32-bit Opera, and everything went ok, it installed correctly. But when I try to run it I get this error (In terminal):
> ERROR: ld.so: object 'libjvm.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libawt.so' from LD_PRELOAD cannot be preloaded: ignored.
/usr/lib/opera/9.00-20060616.6/opera: error while loading shared libraries: libqt-mt.so.3: cannot open shared object file: No such file or directory

I found a topic where others had the same error but I did what they suggested. I installed the 32-bit lesstif2 package, but still no go.

Any help would be greatly appreciated.:D 

-Ryan H

---

### Post by T700 on 2006-07-27
How did you install Opera?

Paul

---

### Post by Ryan H on 2006-07-27
```
sudo dpkg -i --force-architecture opera_9.0-20060616.6-shared-qt_en_i386.deb
```

Like that.

-Ryan H

---

### Post by Fedcer on 2006-07-28
Here you have how to fix the libqt-mt.so.3 error:

[http://ubuntuforums.org/showpost.php?p=1167982&postcount=62](http://ubuntuforums.org/showpost.php?p=1167982&postcount=62)

-----

The first two messages, mean that you don't have java installed. This happens because Opera is a 32bit browser and needs Java 32bit, not Java 64bit (the one installed with Ubuntu 64).

To install Java 32bit separetely from Java 64bit, go to [http://www.java.com](http://www.java.com), and download the linux self stracting file for 32 bit linux. 

Then, to install, do:

```

sudo bash
chmod 777 ./jre-1_5_0_07-linux-i586.bin
(the file name will depend on the java version you downloaded)
./jre-1_5_0_07-linux-i586.bin
mkdir /usr/local/java32
cp -r -p ./jre1.5.0_07/* /usr/local/java32

```

Finally, go to the Preferences of Opera and tell it that the java path is: /usr/local/java32


-

---

### Post by Ryan H on 2006-07-28
It works! Except for Java. I did what you said but when I try to run a Java applet I get a little box that says > Java a. (The rest of the second word is cut off).

Any idea?

-Ryan H

---

### Post by Fedcer on 2006-07-28
If you go [here]("http://www.java.com/en/download/installed.jsp") and click on "Verify Installation", does it detect Java ?

-

---

### Post by Ryan H on 2006-07-29
Nope didn't work.

-Ryan H

---

### Post by Fedcer on 2006-07-30
cd to the directory "/usr/local/java32" and the do an "ls"; what's the result ?

---

### Post by Ryan H on 2006-07-31
> bin      COPYRIGHT  lib      man     README                       Welcome.html
CHANGES  javaws     LICENSE  plugin  THIRDPARTYLICENSEREADME.txt

-Ryan H

---

### Post by Fedcer on 2006-08-02
Hi, I'm sorry for the delay, but I've been busy.

Now, in Opera go to "Tools - Preferences - Advanced - Content". There make sure "Enable Java" is checked and click on "Java Options". A new window will appear where it says "Java path". In the box below write" "/usr/local/java32/lib/i386/". Then click on "Validate Java path". A new window should appear saying "The Java patgh seems to specify a valid directory". If it says that, then Java sould be working. Otherwise say what the message says.

Hope it helps you,

Fedcer

---

### Post by b1g4L on 2006-08-02
I have Sun Java installed and it works fine with Firefox....when I try to point Opera to the java installation, there is no java32 folder? Any ideas?

---

### Post by Ryan H on 2006-08-03
It gives me the error > Could not find a valid Java installation.
Enter another directory and try again.

-Ryan H

---

### Post by Fedcer on 2006-08-04
Try to enter "/usr/local/java32/" only as the directory and click on Valdiate Java Path. A message sohuld appear saying that the path is not valid but it also should aslo suggest an alternative path; accept it and see if it works.

If it doesn't, go to the "/usr/local/java32/lib/i386/" and say what's inside.

-

---

### Post by Fedcer on 2006-08-04
> **b1g4L said:**
> I have Sun Java installed and it works fine with Firefox....when I try to point Opera to the java installation, there is no java32 folder? Any ideas?

Do you have Ubuntu 64bit ?

---

### Post by b1g4L on 2006-08-04
Nope, but I figured it out. Thanks!

---

### Post by Ryan H on 2006-08-05
It doesn't suggest anything. Could it be that the files and folders are chmoded to drwxr--r--?

-Ryan H

---

### Post by Fedcer on 2006-08-05
It is quite problable. In the way the permissions are set, only the owner (root) can read and execute the files. Try changing the permissions to -rwxr-xr-x

-

---

### Post by cchevy on 2006-11-25
> **Fedcer said:**
> Try to enter "/usr/local/java32/" only as the directory and click on Valdiate Java Path. A message sohuld appear saying that the path is not valid but it also should aslo suggest an alternative path; accept it and see if it works.

If it doesn't, go to the "/usr/local/java32/lib/i386/" and say what's inside.

-


I dont have a folder there and I am having the same problem....

Cant validate JAVA, althought I have it installed...i tried all the mentioned paths, but nothing works

---


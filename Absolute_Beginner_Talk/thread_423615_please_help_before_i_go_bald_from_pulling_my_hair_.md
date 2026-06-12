---
title: "please help before i go bald from pulling my hair out"
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by lilafish on 2007-04-26
Okay here it is.  I have had huge problems with Java6 thought installing feisty would solve them. So I installed feisty but the problem remains:  when I try and install anything, I get this message:

Setting up sun-java6-doc (6-00-2ubuntu2) ...
This package is an installer package, it does not actually contain the
JDK documentation.  You will need to go download one of the
archives:

    jdk-6-doc.zip jdk-6-doc-ja.zip

(choose the non-update version if this is the first installation).
Please visit

    [http://java.sun.com/javase/downloads/](http://java.sun.com/javase/downloads/)

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort] 


So I went to sun and got the jdk-6-doc.zip
but I have no earthly idea how to make it owned by root.root or to copy it to /tmp.

So I thought....my first mistake....I will just uninstall Java 6 and reinstall
When i went to synaptic i got this message.

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem
E: _cache->open() failed, please report.

when I run sudo dpkg etc I get the above java 6 message.

It is a vicious merrygoround and i want off...please please please advise

Thank you

---

### Post by guardsman85 on 2007-04-26
Try:```

sudo apt-get install sun-java6-jdk

```When the installation completes run:
```
sudo update-alternatives --config java
```Type the number of the Sun Java 6 installation from the list.
Then run:
```
sudo nano /etc/jvm
```Add the following to the top of the list:
```
/usr/lib/jvm/java-6-sun
```Ctrl + O saves.  Ctrl + X to exit.

If you also want the JRE and Firefox plugin run:
```
sudo apt-get [FONT=courier new,courier,monospace]install sun-java6-jre sun-java6-plugin
```[/FONT]

[B]
I adapted this info from this website:  [/B][**http://tinyurl.com/2ruo2n**]("http://tinyurl.com/2ruo2n")

---

### Post by lilafish on 2007-04-26
thank you so much for your reply; however I cant get past the first step, which gets me this error


aimee@aimee-desktop:~$ sudo apt-get install sun-java6-jdk
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

and the vicious cycle starts again :confused:

---

### Post by kittyhawk63 on 2007-04-26
> **lilafish said:**
> thank you so much for your reply; however I cant get past the first step, which gets me this error
aimee@aimee-desktop:~$ sudo apt-get install sun-java6-jdk
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
and the vicious cycle starts again :confused:
Open terminal and copy/paste the following:

**sudo dpkg --configure -a**

hit <enter>
Wait until you see yourname@yourname:~$
Then follow the other instructions given earlier by guardsman85.

---

### Post by lilafish on 2007-04-26
oh my gosh it worked...i finally got off the merrygoround   thank you sooooo much:KS

---

### Post by kittyhawk63 on 2007-04-26
Lilafish,

Glad you got it working.

Have you marked your thread "Resolved"?

Go to your original post on this subject. Select "Edit" -> "Advanced Edit" and select the "resolved" box near the top. Click "save".

kh

---

### Post by naughtywill on 2007-04-29
I am having this exact same problem. I tried everything guardsman and kitty hawk said and still I have no luck.  When I run this line----sudo apt-get install sun-java6-jdk----- I still get this :> Please visit

    [http://java.sun.com/javase/downloads/](http://java.sun.com/javase/downloads/)

now and download.  The file should be owned by root.root and be copied
to /tmp.

[Press RETURN to try again, 'no' + RETURN to abort] . It is really getting frustrating. Its the same thing at least 20 times already. What am I doing wrong?

---


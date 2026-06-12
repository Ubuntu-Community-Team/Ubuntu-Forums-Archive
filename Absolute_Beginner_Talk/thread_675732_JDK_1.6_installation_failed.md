---
title: "JDK 1.6 installation failed?"
date: 2008-01-23
forum: Absolute Beginner Talk
---

### Post by sundar22in on 2008-01-23
Hi,

I tried to install JDK 1.6 in Ubuntu 7.04. I downloaded the binary file from Sun and I executed the file. I accepted the license agreement and installation went fine. So far so good.

But after installing I executed *java - version* command I see the default installation of Java which comes with ubuntu 7.04. Is there any environment settings I need to do? Or is the installation unsuccessful(But i did not see any error messages)?


Any pointers is appreciated.

Thank you.


~ Sundar ~

---

### Post by tojge on 2008-01-23
Where have you installed it? I mean, like, in /usr/java, /opt/java, or what?

---

### Post by sundar22in on 2008-01-23
I did not specify for any path during installation. Installation did not ask for it, I assumed it installed in a default path(I dont know where it is).

---

### Post by tojge on 2008-01-23
In that case, it presumably was installed (that is, unpacked) in the directory in which the .bin file was saved after downloading. Was it your home directory (e.g. /home/sundar)?

---

### Post by sundar22in on 2008-01-23
Yes you are right. It was unpacked in the same directory in which the bin file was saved after downloading.

The directory in which the bin file was placed is "/home/sundar/Desktop"

---

### Post by sundar22in on 2008-01-23
Any pointers to make it working?

Thank you.

---

### Post by tojge on 2008-01-23
Ok, fine, if you want to keep it there, you can, it can work...

But I'd like you to paste the output of the following two commands:
```
which java
```
and
```
echo $PATH
```

---

### Post by sundar22in on 2008-01-23
tojge,

Thanks for your response. I am away from my home ubuntu machine. So I cannot give the output for the above commands immediately.

But when I executed java - version command it shows it is the default Java/JRE which comes with Ubuntu 7.04.

It was not showing Java 6 which I unpacked/installed.

Any pointers how to go about this problem, so that I can try it at home.

Thanks in advance.

---

### Post by tojge on 2008-01-23
Ok, what you need to do is to create symbolic links to some of the files in the extracted JDK folder that you need, and create them in one of the folders that is in your path...

So, presumably, which java would output /usr/bin/java. Go to, say, /usr/local/bin
```
cd /usr/local/bin
```
and create the links, for example:
```
sudo ln -s /home/sundar/Desktop/<your_JDK_folder>/bin/java
sudo ln -s /home/sundar/Desktop/<your_JDK_folder>/bin/javac
etc...
```
(I don't have JDK installed ATM, so the exact path may differ, I am typing this from the back of my head), but I hope you do get my point :-)

---

### Post by sundar22in on 2008-01-23
I will do the suggested solution @ home.

Thanks for your kind response. Hope it works!

---


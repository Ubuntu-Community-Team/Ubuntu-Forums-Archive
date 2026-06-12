---
title: "rpm-command"
date: 2007-02-01
forum: Absolute Beginner Talk
---

### Post by inspiron on 2007-02-01
Im installing java and Im following the instruction on: [http://java.com/en/download/help/5000010500.xml#rpm](http://java.com/en/download/help/5000010500.xml#rpm) . I have problem with number 7 in that instruction. I cant get the "rpm"-command to work, it say "rpm: command not found".
How do I get the command to work?
Thanks in advance.

---

### Post by ComplexNumber on 2007-02-01
> **inspiron said:**
> Im installing java and Im following the instruction on: [http://java.com/en/download/help/5000010500.xml#rpm](http://java.com/en/download/help/5000010500.xml#rpm) . I have problem with number 7 in that instruction. I cant get the "rpm"-command to work, it say "rpm: command not found".
How do I get the command to work?
Thanks in advance.
rpm doesn't work on ubuntu because ubuntu is debian based. this means that it uses packages ending in ".deb" rather than ".rpm".
you could install an application called alien which you can download using synaptic. this can convert rpms to debs.

---

### Post by Paerez on 2007-02-01
ooh don't do it that way:
[http://ubuntuforums.org/showthread.php?t=76702](http://ubuntuforums.org/showthread.php?t=76702)

---

### Post by psyne on 2007-02-01
RPM installers are for another version of Linux. You can use a tool called Alien to convert them to the deb or debian format which Ubuntu uses but Java already has a deb and it is in the package manager. 

I am a complete noob as well so if anyone sees that I missed something please let me know.

There are two ways you could attack this problem you can install it manually or use EasyUbuntu which is extreemly easy if your interested in using EasyUbuntu download it from the link below

[http://easyubuntu.freecontrib.org/files/easyubuntu_latest.deb](http://easyubuntu.freecontrib.org/files/easyubuntu_latest.deb)

then open up terminal and input

```

wget -q http://medibuntu.sos-sts.com/repo/medibuntu-key.gpg -O- | sudo apt-key add -

``` 

That will add the key to your system

From there doubleclick to install the package and then when it is installed run Easyubuntu and go to the Web tab and choose install Java.

To do it the manual way

First you have to add the source list from the terminal type

 ```
sudo gedit /etc/apt/sources.list
```

add the following

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper main restricted 
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) dapper universe multiverse 

save and close the file

After this have apt updates its repository 

```
sudo apt-get update 
```

And finally, just tell it to install java  

```
sudo apt-get install sun-java5-jdk
```

---


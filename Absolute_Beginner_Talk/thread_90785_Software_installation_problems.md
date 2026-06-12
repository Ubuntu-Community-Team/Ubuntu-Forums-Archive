---
title: "Software installation problems"
date: 2005-11-15
forum: Absolute Beginner Talk
---

### Post by subways on 2005-11-15
Hi, I am very new to installing software

I have the files j2sdk1.2.0_01 and Netbeans 3.6 both saved on my desktop

I used the command chmod +x j2sdk1.2.0_01 and same on netbeans

I then installed j2sdk and it seemed succesful, however when I try to install netbeans (which is used for java programming) it gives me an error saying that a Java Virtual Machine cannot be found. Im really getting stressed as I have spent many hours scouring the net without success, so any help is muchly appreciated

---

### Post by Manny C on 2005-11-15
How did you install j2sdk? More to the point: where did you install j2sdk?

See the [installation guide for Netbeans]("http://www.netbeans.org/community/releases/41/install.html"):
>  You can also specify which JDK       the installer should use from the command line. For example:
```
$ ./*your_binary_executable* -is:javahome *path_to_your_jdk *
``` 

Have you tried using [Eclipse]("http://www.eclipse.org/")?

---

### Post by subways on 2005-11-15
thankyou for the reply, as i said I am new to this

I did the following


in the folder /home/kev/ I have j2sdk-1_4_0_01-linux-i586.bin and also netbeans-3_6-linux.bin


In root terminal I did the following

chmod +x j2sdk-1_4_0_01-linux-i586.bin

THEN

./j2sdk-1_4_0_01-linux-i586.bin which seems to install as it asks me about if I agree to terms and conditions to which I put a "y"

I then try the same thing with netbeans.......same 2 commands, except with netbeans i get the error...

A suitable JVM could not be found. Please run the program again using the option -is:javahome <JAVA HOME DIR>

I am very new to this, so basic replise are much appreciated.

---

### Post by kruz on 2005-11-15
im hoping u have java installed
which i think u just installed i didnt read the filename

wherever taht installed, put it to that directory

so it will look SOMETHING like this

-is:javahome /home/kev/.j2sdk-1_4_0_01

hope this helps
note: that isnt the directory, you gota find that urself should be in the logs

---


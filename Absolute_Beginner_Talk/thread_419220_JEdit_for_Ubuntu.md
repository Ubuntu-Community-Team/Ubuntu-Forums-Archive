---
title: "JEdit for Ubuntu"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by Jetboat adventurer on 2007-04-22
So... I liked using JEdit on windows and I was told I could use it on Linux. But everytime I install it. It acts like it is opening but it never opens. Please HELP me!!!!!!!

---

### Post by Seisen on 2007-04-22
In which way did you try to install it and what are the specs for your computer

---

### Post by Jetboat adventurer on 2007-04-22
I downloaded the debian package off the Jedit website. Specs are 256mb ram, 60gb hard drive, feisty fawn, um I think that is what your talking about. I don't know much about linux I pretty new.

---

### Post by Seisen on 2007-04-22
Did you install Java if not it won't open?

---

### Post by Jetboat adventurer on 2007-04-22
I'm pretty sure i installed JAVA. I just upgraded to feisty fawn, but in ubuntu 6.1 I did install java and it still didn't open. I'm wondering if I should install 6.06?

---

### Post by Seisen on 2007-04-22
Try following this and see if it works, if not let me know.

[http://www.cs.cornell.edu/~djm/ubuntu/#jedit]("http://www.cs.cornell.edu/~djm/ubuntu/#jedit")

---

### Post by Jetboat adventurer on 2007-04-22
I don't know how to do command line stuff

---

### Post by Seisen on 2007-04-22
Open up the terminal like this Applications>Accessories>Terminal. Then copy and paste.

---

### Post by Jetboat adventurer on 2007-04-22
i tried that. i sent you the message it gave me.

---

### Post by Vomit-Orchestra on 2007-04-22
Just remember some programs don't like being run, like smb4k.

just
Sudo Su 
and then type the programs name and it should run without problems.
Unless it is your Java.

---

### Post by Seisen on 2007-04-22
I messaged you back did it work.

---

### Post by Jetboat adventurer on 2007-04-23
nope, it could be my java, is there a specific package i need to have? Would you recommend switching to 6.06?

---

### Post by mrpeenut24 on 2007-04-24
Open the terminal up and type 'jedit' then press enter.  If it says something about the $JAVA_HOME missing (or something like that), then you'll need to install java6.  At the terminal, type
```
sudo apt-get update
sudo apt-get install sun-java6-jre sun-java6-bin

``` then type in your password.  This should install the java6 and place the java executable in a place where jedit can view it.

---

### Post by mrpeenut24 on 2007-04-24
However, I've found that java6 messes up sometimes... So if it does tell you something about $JAVA_HOME missing, and after you install java6 it works, but the cursor is off a lot, you can let someone here know and they can tell you how to change the alternative using update-alternatives.

---

### Post by Jetboat adventurer on 2007-04-25
it's still not working. i don't know whats going on with this stuff. thanks for the help y'all!!

---


---
title: "[SOLVED] Java?"
date: 2008-03-09
forum: Absolute Beginner Talk
---

### Post by blasteryui on 2008-03-09
Okay, I wanna play Pogo, and Runescape. I need Java, I need Java for firefox etc... 
step by step, please on how to get Java working with firefox. I have Gutsy Ubuntu.

---

### Post by thisiam on 2008-03-09
command to install JAVA in ubuntu

sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin java -version

---

### Post by blasteryui on 2008-03-09
I did then, now when I try to play runscape it's a Grey screen at first then it says Error with tablet. Now what?

---

### Post by thisiam on 2008-03-09
mine says error loading applet.

not sure as i don't play games to often but never had problems before.
i got some reading to do i guess.
maybe someone here knows what we can do.

---

### Post by blasteryui on 2008-03-09
> **thisiam said:**
> mine says error loading applet.

not sure as i don't play games to often but never had problems before.
i got some reading to do i guess.
maybe someone here knows what we can do.

Yeah it be nice if somebody helped us out.

---

### Post by roscopico on 2008-03-09
Yes, a bit of help would be great...
After entering th ecommand listed in a prior post, ```
E: Command line option 'e' [from -version] is not known.
```

This is, after all, the "absolute beginner" section, is it not?  Everyone starts somewhere.

---

### Post by caffienefree on 2008-03-09
Out of curiosity, please open a terminal and enter the following command:

> java -version

Then please post the output. I.e., this is my result.
> mbl:~$ java -version
java version "1.6.0_03"
Java(TM) SE Runtime Environment (build 1.6.0_03-b05)
Java HotSpot(TM) Client VM (build 1.6.0_03-b05, mixed mode, sharing)


---

### Post by roscopico on 2008-03-09
thanks for the attention caffeinefree

```
java version "1.4.2[CODE]"
gij (GNU libgccj) version 4.1.2 20060928 (prerelease) (ubuntu 4.1.1-14 ubuntu7
```[/CODE]

I have tried the instructions on the java site, but they fail at the chmod step, saying package not found.

Thanks again!

---

### Post by FuturePilot on 2008-03-09
```
sudo update-alternatives --config java
```
Make sure Java 6 is set as the default. Then run the java -version command again and see what it says.

---

### Post by roscopico on 2008-03-09
Problem solved:

Found my answer in this thread [JAVA INSTALL]("http://ubuntuforums.org/showthread.php?t=493719&highlight=install+java+for+pogo")

Thanks for the help Ubuntu is awesome!:guitar:

---


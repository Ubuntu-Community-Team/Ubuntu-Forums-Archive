---
title: "Do I have Java on my machine?"
date: 2007-04-04
forum: Absolute Beginner Talk
---

### Post by Dan_472 on 2007-04-04
Hello

I've used the Synaptic Package Manager to install every package that could reasonably be Java,  yet it doesn't seem to be working (while attempting to install a java-based game called "Bang Howdy" [http://www.banghowdy.com/](http://www.banghowdy.com/) , it says in the terminal that /bin/java couldn't be located.

Is there something I could type in a terminal to see if I have Java and where it is?

---

### Post by r4ik on 2007-04-04
Should be in,

/usr/bin/java

---

### Post by mikeyphi on 2007-04-04
Check that you have all the sources enabled in SYSTEM - ADMINISTRATION - SOFTWARE SOURCES     otherwise you will not see Sun Java in Synaptic - which is presumably what you want?

---

### Post by bashologist on 2007-04-04
Maybe this will work?
```
if which java; then sudo ln -s "$(which java)" /bin/java; fi
```

---

### Post by r4ik on 2007-04-04
Or,

sudo  update-alternatives --display java

---

### Post by Dan_472 on 2007-04-04
OK   I think I see the problem    I see java 1.5.0 in there, but the 'best' version is 1.4  (game requires 1.5)    so,  what should I do?  Use Synaptic or terminal command?  I could try either.

Thank you

---

### Post by compmodder26 on 2007-04-04
Do "sudo update-alternatives --config java".

You should then be able to pick the java version you want to use by default.

---

### Post by Dan_472 on 2007-04-04
Java seems to be working OK in that the game will now load  (seems to have lots of lag...maybe graphics card problem)

However, if I take Firefox to the Java test page  [http://www.java.com/en/download/help/testvm.xml](http://www.java.com/en/download/help/testvm.xml)     I get the plain red X instead of the dancing figure.

Thank you

---

### Post by Maestro23 on 2007-04-04
> **Dan_472 said:**
> Java seems to be working OK in that the game will now load  (seems to have lots of lag...maybe graphics card problem)

However, if I take Firefox to the Java test page  [http://www.java.com/en/download/help/testvm.xml](http://www.java.com/en/download/help/testvm.xml)     I get the plain red X instead of the dancing figure.

Thank you

You need the java browser plugin.  Search in Synpatic (sun-java5/6-plugin). Install.

---

### Post by Dan_472 on 2007-04-05
Yay!   It works    thank you

Say, one last thing...   the SYSTEM - ADMINISTRATION - SOFTWARE SOURCES   that Mikeyphi was talking about  (#3 above)  I don't see that when I click SYSTEM, then ADMINISTRATION.    I'm using Ubuntu 6.06 LTS.   Is this something I need to follow-up on?

Thanks

---

### Post by zvacet on 2007-04-05
You don´t have it in Dapper.It is the way to open repos.Yo will do it with synaptic>repositories in dapper but I belive you done it allready.

---


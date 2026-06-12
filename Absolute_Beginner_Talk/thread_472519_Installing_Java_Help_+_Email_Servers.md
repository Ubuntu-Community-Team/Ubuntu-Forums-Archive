---
title: "Installing Java? Help + Email Servers"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by Brendan Hart on 2007-06-13
Some one give me some info on installing Java for the web and also java application servers.

Application servers can wait really but mainly java for web.
and also with evolution mailing, my outgoing mail goes through pop3 and evolution only gives me option of smtp or send mail

help

---

### Post by Znupi on 2007-06-13
I don't know about Java, but I can tell you one thing. Outgoing mail cannot go through pop3.

---

### Post by Anicka on 2007-06-13
Do you mean a plug-in for java in Firefox? Try ```
sudo aptitude sun-java6-plugin
``` If you get a licence agreement message, use the tab-key to get to the ok-box and press enter.

---

### Post by Brendan Hart on 2007-06-13
hold on ill log into my cpanel and show you

anicka that code told me it didnt have super cow powers

---

### Post by Anicka on 2007-06-13
> **Brendan Hart said:**
> hold on ill log into my cpanel and show you

anicka that code told me it didnt have super cow powers

Sorry! Too fast...```
sudo aptitude install sun-java6-plugin
```

---

### Post by Brendan Hart on 2007-06-13
sorry anicka, firefox still crashes when loading java based applications

---

### Post by Anicka on 2007-06-13
Can you post the link? Does it work in other OSs? I can run java-applets with my set-up, so maybe there is something else.

---

### Post by Brendan Hart on 2007-06-13
hold on i just un installed java, and im starting again, making sure i only get the necessities

---

### Post by Brendan Hart on 2007-06-13
[http://www.jagex.com/meltdown.ws](http://www.jagex.com/meltdown.ws)

---

### Post by Anicka on 2007-06-13
My list of packages with a name containing java is:
```
i   java-common                     - Base of all Java packages                 
i   java-gcj-compat                 - Java runtime environment using GIJ        
i   libhsqldb-java                  - Java SQL database engine                  
i   libjaxp1.2-java                 - Java XML parser and transformer APIs (DOM,
i   libjaxp1.3-java                 - Java XML parser and transformer APIs (DOM,
i   libjline-java                   - Java library for handling console input   
i   libservlet2.3-java              - Servlet 2.3 and JSP 1.2 Java classes and d
i   libxalan2-java                  - XSL Transformations (XSLT) processor in Ja
i   libxerces2-java                 - Validating XML parser for Java with DOM le
i   libxt-java                      - An implementation in Java of XSL Transform
i   openoffice.org-java-common      - OpenOffice.org office suite Java support a
i A sun-java6-bin                   - Sun Java(TM) Runtime Environment (JRE) 6 (
i A sun-java6-jre                   - Sun Java(TM) Runtime Environment (JRE) 6 (
i   sun-java6-plugin                - The Java(TM) Plug-in, Java SE 6           

```
Does it help?

---

### Post by Brendan Hart on 2007-06-13
should i delete all my java and re install all those?

---

### Post by Anicka on 2007-06-13
Fun game, reminds me of the C64-good-old-days. And it works in my Ubuntu/firefox... I hope you find the solution, because my resources of knowledge are emptied.

---

### Post by Anicka on 2007-06-13
```
aptitude search '~i' | grep java
``` will give the list of what is installed. Most of them are depending on each other and probably some are totally unrelated to your problem.

---

### Post by Brendan Hart on 2007-06-13
aaahg god dang it, i un installed all my java programs and installed all the ones u had.

currently got:

i   java-common                     - Base of all Java packages                 
i   java-gcj-compat                 - Java runtime environment using GIJ        
i   libhsqldb-java                  - Java SQL database engine                  
i   libjaxp1.2-java                 - Java XML parser and transformer APIs (DOM,
i   libjaxp1.3-java                 - Java XML parser and transformer APIs (DOM,
i   libjline-java                   - Java library for handling console input   
i   libservlet2.3-java              - Servlet 2.3 and JSP 1.2 Java classes and d
i   libxalan2-java                  - XSL Transformations (XSLT) processor in Ja
i   libxerces2-java                 - Validating XML parser for Java with DOM le
i   libxt-java                      - An implementation in Java of XSL Transform
i   openoffice.org-java-common      - OpenOffice.org office suite Java support a
i   sun-java6-bin                   - Sun Java(TM) Runtime Environment (JRE) 6 (
i   sun-java6-jre                   - Sun Java(TM) Runtime Environment (JRE) 6 (

---

### Post by Anicka on 2007-06-13
Sorry! I'm out of suggestions. Anyone else?

---

### Post by nvteighen on 2007-06-13
> **Anicka said:**
> Sorry! I'm out of suggestions. Anyone else?
Yes, a possible package problem. I can't install no version java through apt-get/aptitude/synaptic because it gets different conflicts every time (ttf-lucida, dpkg, no configuration possible).

I could install java without conflicts from Java.com, I didn't get any error message, but I couldn't make it run... I did something wrong when linking Java to Firefox.

---

### Post by Brendan Hart on 2007-06-13
and how does that help me out?

---

### Post by Anicka on 2007-06-13
Do you have bsh, gij-4.1, libgcj-common, libgcj-jar and libgcj7-0 installed? Have no idea if it helps...

---

### Post by Anicka on 2007-06-13
Just one last question: are you by any chance using 64bit Ubuntu or any theme in Firefox? [https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/86002](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/86002) [https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/90201](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/90201) [https://launchpad.net/bugs/81032](https://launchpad.net/bugs/81032) [https://launchpad.net/bugs/84132](https://launchpad.net/bugs/84132)

Look at these threads that I googled. Maybe you find a hint there or in any other bug report.

---

### Post by Brendan Hart on 2007-06-13
Amd64

I Havnt installed any themes

---


---
title: "Do I have to go back to windows? (IE-only website)"
date: 2007-11-18
forum: Absolute Beginner Talk
---

### Post by Padraig1 on 2007-11-18
Hi,
I have to access a website but some of the text can't be seen in Moxilla. I setup IE4Linux but from what I can make out Java applets (which is where the text is) don't work in it. 

Is there is a way of getting around this?

If you have a solution please keep it as simple as possible.

Thanks.

---

### Post by ddrichardson on 2007-11-18
What site is it?

---

### Post by DutyDuty on 2007-11-18
Could you post a link to the text? And have you installed Java for Firefox, Synaptic can do the job.

---

### Post by Padraig1 on 2007-11-18
[http://www.univie.ac.at/future.media/moe/galerie/var/var.html#struk1](http://www.univie.ac.at/future.media/moe/galerie/var/var.html#struk1)

---

### Post by conjur3r on 2007-11-18
Sounds like you haven't installed the java plugin.  Open up Synaptic package manager and search for java.  Install either of the following: sun-java6-plugin or sun-java5-plugin

---

### Post by ddrichardson on 2007-11-18
I agree, I've sun-java6-plugin and its running fine here.

---

### Post by Padraig1 on 2007-11-18
I can view the applet in Firefox but can't view the text ie. the end of the equations are missing

I can't start the applet in IEs4Linux

It's Java 6

---

### Post by CouchMaster on 2007-11-18
I'm running PCLos and the same thing happens to me - the end of the text/equations are cut off in some of the windows and can't be read...

---

### Post by LowSky on 2007-11-18
> **CouchMaster said:**
> I'm running PCLos and the same thing happens to me - the end of the text/equations are cut off in some of the windows and can't be read...

in Firefox, go to edit>preferences>content

change the size of the font

---

### Post by Padraig1 on 2007-11-18
when i change the size of the font the text in the webpage changes but not in the applet

---

### Post by philinux on 2007-11-18
The applet is not resizing the text boxes correctly, not sure what the fix is though.

---

### Post by CouchMaster on 2007-11-18
Yeah, weird - It does work in XP though, I just tried it, but not Kubuntu or Xubuntu either - I'm starting to think that it's a Java RunTime Enviornment/Linux thing...

---

### Post by Niedzwiedz on 2007-11-18
I may be off the wall here. But, Applications > Add/Remove Applications > "Do a Search for JAVA" see if "Sun Java 6 Web Start" is checked? This what I have installed and it works for me, but, this Mozilla and not I.E.

---

### Post by philinux on 2007-11-18
opera does the same thing chops the text off.

---

### Post by ericartman on 2007-11-18
Nevermind

Cart

---

### Post by atlfalcons866 on 2007-11-18
works here using java runtime 6

---

### Post by philinux on 2007-11-18
Had java6 tried 5 still no deal, whats the diff I wonder where some can and some cant see all the text. Very weird.

---

### Post by jordanmthomas on 2007-11-18
works here with java 1.6.0_3-b05 in opera and firefox.
Why are you trying to use IE?  Isn't the point of Java to be cross-platform? :)

---

### Post by philinux on 2007-11-18
He's trying to use IE because like him and me it dont work but seems to be ok for others.

---

### Post by Padraig1 on 2007-11-19
I've had a look on the Java website and i selected "verify Java Installation". It tells me I've version 1.4.2 and they recommend updating to version 6.

On their website they say to view the Java version on your machine use the "java -version" command. When I do this I get:
[COLOR="Red"]
padraig@padraig-laptop:~$ java-version
bash: java-version: command not found
padraig@padraig-laptop:~$ java -version
java version "1.6.0_03"
Java(TM) SE Runtime Environment (build 1.6.0_03-b05)
Java HotSpot(TM) Server VM (build 1.6.0_03-b05, mixed mode)[/COLOR]

Any ideas why the website and the terminal are telling me different things?

---

### Post by asmiller-ke6seh on 2007-11-19
> **philinux said:**
> He's trying to use IE because like him and me it dont work but seems to be ok for others.

This looks, to me, like it might be a font substitution problem.

---

### Post by Padraig1 on 2007-11-19
where does the problem lie?
Is it in my PC or in the code for the applet?

---

### Post by philinux on 2007-11-19
I'm pretty sure it's the code for the applet.

---


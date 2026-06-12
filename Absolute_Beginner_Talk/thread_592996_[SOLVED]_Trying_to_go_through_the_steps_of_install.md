---
title: "[SOLVED] Trying to go through the steps of installing a tarball, but with problems"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by Lacent on 2007-10-26
Well, yes, I have read all the guides, and I fully understand what to do. But ever since I have tried to install packages that arent in the synaptec package manager, I have always had trouble with the ./configure command. Whenever I enter that command, it always says "No such file fr directory". I'm sure its something on my end, so if you guys could help out, that would be great. Thanks

---

### Post by Maestro23 on 2007-10-26
> **Lacent said:**
> Well, yes, I have read all the guides, and I fully understand what to do. But ever since I have tried to install packages that arent in the synaptec package manager, I have always had trouble with the ./configure command. Whenever I enter that command, it always says "No such file fr directory". I'm sure its something on my end, so if you guys could help out, that would be great. Thanks

Stuff you probably already know:

1. You need build-essential installed.

2. You need to be in the extracted directory when you try and run those commands.

3. Every tarball should come with a README/Install doc in the extracted directory with Instructions.

*What are you trying to install?

---

### Post by Lacent on 2007-10-26
I am trying to install Grooveshark, which is a media player, and it has no readme. It has a .jar file, but I cant seem to get java working for it to install from that starter.jar file...is build-essential in the synaptec package manager?


EDIT: Actually, when I right click on the starter.jar file, I have the option of opening it with java runtime 5.0, but when I do that, it never comes up. It just kinda "forgets" that I clicked that. lol

---

### Post by Maestro23 on 2007-10-26
> **Lacent said:**
> I am trying to install Grooveshark, which is a media player, and it has no readme. It has a .jar file, but I cant seem to get java working for it to install from that starter.jar file...is build-essential in the synaptec package manager?

Sure:

> sudo apt-get install build-essential

If your java is installed correctly, should be able to:

> java -jar nameofyour.jar

---

### Post by Lacent on 2007-10-26
> **Maestro23 said:**
> Sure:



If your java is installed correctly, should be able to:


Well, I do have that program. I'm not sure if the problem is the ./configure not working, or if the only way to install this is to run that starter.jar file...

---

### Post by Lacent on 2007-10-26
> **Maestro23 said:**
> Sure:



If your java is installed correctly, should be able to:

Ok, I ran that java command, and it seems to be starting! I wonder why it had to be run in the terminal instead of starting when i right clicked on it?

---

### Post by Maestro23 on 2007-10-26
> **Lacent said:**
> Well, I do have that program. I'm not sure if the problem is the ./configure not working, or if the only way to install this is to run that starter.jar file...

Got a link to the program.

---

### Post by Lacent on 2007-10-26
> **Maestro23 said:**
> Got a link to the program.

Well, Thanks alot maestro!

---

### Post by Maestro23 on 2007-10-26
> **Lacent said:**
> Well, Thanks alot maestro!

No prob man, glad to help.  Don't forget to mark this SOLVED using the Thread Tools.

:guitar:

---


---
title: "Enabling scripts"
date: 2007-03-21
forum: Absolute Beginner Talk
---

### Post by Aurora Borealis on 2007-03-21
How do we enable scripts? (Ubuntu Edgy)

---

### Post by dbbolton on 2007-03-21
what kind of scripts ?

---

### Post by steve.horsley on 2007-03-21
I'm guessing at what you mean, but scripts must be marked as executable before you can run them. Being executable is a file property, like being writeable is. To make a script executable, right-click in nautilus and choose Properties, or from the command line, **chmod +x filename**.

---

### Post by Aurora Borealis on 2007-03-22
Thank you for your replies. I'm trying to enable Javascript. (I'm still a total newbie when it comes to computers.)

---

### Post by devnulljp on 2007-03-22
enable javascript? You mean in a browser? Which browser? 
Ex. in firefox...
Edit->Preferences->Content->Enable javascript 
That help?

---

### Post by Aurora Borealis on 2007-03-22
Yes-thank you very much!

---

### Post by Aurora Borealis on 2007-04-05
New problem-a website is telling me a need a plugin but when I click the install button, it says it didn't install and gives me the option to do that manually. I click on that and it sends me to the Java site. But my browser preferences show Java is enabled, and this is a new updated version of the OS that I just downloaded last night-CE 2.2. Anyone know why?

---

### Post by slimdog360 on 2007-04-05
Im guessing it needs the jre (java runtime environment), just follow the instructions on the java website and you will be alright.

edit: I just realised its in the repositories. 

try this, open a terminal and copy this in there
```
sudo apt-get install sun-java6-plugin 
```
 and restart firefox.

---


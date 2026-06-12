---
title: "Activating java when double clicking a jar file"
date: 2005-11-13
forum: Absolute Beginner Talk
---

### Post by No_Germs on 2005-11-13
currently, when i double click a jar file, it's contents are displayed. in order to open it i need to open a console window and type "java -jar jarname.jar".
if i right-click the jar and choose "open with..."  the other options i have are java web start 1.4, which is ok, but i really want the 1.5 jre to run it. the jre isn't marked as an applicaion, so i can't choose it from all the application's list. what do i do?

---

### Post by Joe_lurker on 2005-11-14
I will try and help you out with this.  I am by no means an expert in the alternatives system but this should al least not explode your computer ;).

Introduce the new Java runtime to the alternatives system:
```
sudo update-alternatives --install java java /path/to/jre1.5.0_05/bin/java 1500
```
replacing /path/to/ with the path to your JRE.

Choose the new Java alternative:
```
sudo update-alternatives --config java
```
The default should be your new Java install, but double check.

Recreate the link in bin?  I don't know if I made a mistake but the link in my bin  folder was deleted.  If you get an error here you should be fine.
```
sudo ln -s /etc/alternatives/java /usr/bin/java
```

Right-click on a .jar file and choose properties.  Then choose the "Open With" tab.  Select the "Java" radio button and click close.  If the radio button for Java is not there then choose "Add".  At the bottom of the "Add Application" dialog expand the "Use custom command" area.  In the command box enter "/usr/bin/java -jar".

I hope this gets you to where you want to be.
-Joe

---


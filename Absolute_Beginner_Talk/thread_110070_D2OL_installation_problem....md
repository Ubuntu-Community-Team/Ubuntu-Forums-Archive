---
title: "D2OL installation problem..."
date: 2005-12-30
forum: Absolute Beginner Talk
---

### Post by pegleg on 2005-12-30
I run a few distributed computing projects on my toasters (I have 14 here at home), so naturally now that I have ubuntu installed, I want to try a few linux DC clients...

I have boincSETI up on this box already, but have had some difficulty getting D2OL to install... I much prefer D2OL because I believe in running altruistic scientific and medical research projects and this is a drug design project for treatment of diseases...

anyway, here's the instructions from the website...
> Linux Instructions:

After downloading open a shell and, cd to the directory where you downloaded the installer.
At the prompt type: sh ./installDDOL.bin

Notes:

A Java virtual machine is included with some of these downloads. It will be run automatically when you run the shell script. 

and heres what I get in response...
> john@ubuntu1:/home$ cd /home/john/D2OL
john@ubuntu1:~/D2OL$ sh ./installDDOL.bin
Preparing to install...
Extracting the JRE from the installer archive...
Unpacking the JRE...
Extracting the installation resources from the installer archive...
Configuring the installer for this system's environment...

Launching installer...

Invocation of this Java Application has caused an InvocationTargetException. Thi s application will now exit. (LAX)

Stack Trace:
java.lang.NoClassDefFoundError
        at java.lang.Class.forName0(Native Method)
        at java.lang.Class.forName(Class.java:140)
        at java.awt.GraphicsEnvironment.getLocalGraphicsEnvironment(GraphicsEnvi ronment.java:62)
        at java.awt.Window.init(Window.java:224)
        at java.awt.Window.<init>(Window.java:268)
        at java.awt.Frame.<init>(Frame.java:398)
        at java.awt.Frame.<init>(Frame.java:363)
        at com.zerog.ia.installer.Main.c(Unknown Source)
        at com.zerog.ia.installer.Main.main(Unknown Source)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl. java:39)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAcces sorImpl.java:25)
        at java.lang.reflect.Method.invoke(Method.java:324)
        at com.zerog.lax.LAX.launch(Unknown Source)
        at com.zerog.lax.LAX.main(Unknown Source)
GUI-
john@ubuntu1:~/D2OL$

any ideas or help is appreciated...

---

### Post by thekiller on 2005-12-30
seems like Java Runtime environment is not properly installed, why dont u compile it first yourself and then try to run the executable.

---

### Post by pegleg on 2005-12-30
thanks...

there was another option with an installer without JRE, so I used syanptic to install JRE, then used the D2OL installer without JRE, and it worked...

thanks again.. :)

---


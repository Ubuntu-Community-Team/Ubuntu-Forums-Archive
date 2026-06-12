---
title: "How to install .jar file"
date: 2007-07-19
forum: Absolute Beginner Talk
---

### Post by K_Soze on 2007-07-19
I am get an error message "unable to access jarfile varsha.jar" which is located on my desktop?

I went to Automatix and installed the java from there so I don't think thats the problem unless it is a different version of java than the one I need.

Any ideas?

---

### Post by misfitpierce on 2007-07-19
Console to where it is

Ex: cd /home/yournamehere/Desktop

Then...

sudo sh name.jar or sh name.jar 

I believe thats the way.

---

### Post by K_Soze on 2007-07-19
> **misfitpierce said:**
> Console to where it is

Ex: cd /home/yournamehere/Desktop

Then...

sudo sh name.jar or sh name.jar 

I believe thats the way.

tried both, sudo sh and just sh, they didn't work

I also tried "java -jar varsha.jar" and got:
root@dad-desktop:/home/dad/Desktop# java -jar varsha.jar
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

Exception in thread "main" java.lang.InternalError: Can't connect to X11 window server using ':0.0' as the value of the DISPLAY variable.
        at sun.awt.X11GraphicsEnvironment.initDisplay(Native Method)
        at sun.awt.X11GraphicsEnvironment.access$100(X11GraphicsEnvironment.java:52)
        at sun.awt.X11GraphicsEnvironment$1.run(X11GraphicsEnvironment.java:155)
        at java.security.AccessController.doPrivileged(Native Method)
        at sun.awt.X11GraphicsEnvironment.<clinit>(X11GraphicsEnvironment.java:131)
        at java.lang.Class.forName0(Native Method)
        at java.lang.Class.forName(Class.java:169)
        at java.awt.GraphicsEnvironment.getLocalGraphicsEnvironment(GraphicsEnvironment.java:68)
        at java.awt.Window.init(Window.java:354)
        at java.awt.Window.<init>(Window.java:407)
        at java.awt.Frame.<init>(Frame.java:402)
        at java.awt.Frame.<init>(Frame.java:367)
        at javax.swing.JFrame.<init>(JFrame.java:163)
        at varsha.ui.Varsha.<init>(Varsha.java:31)
        at varsha.ui.Varsha.main(Varsha.java:1243)0
yikes......

---

### Post by vambo on 2007-07-19
Try

```
cd ~/Desktop
```

then

```
./varsha.jar
```

---

### Post by K_Soze on 2007-07-19
> **vambo said:**
> Try

```
cd ~/Desktop
```

then

```
./varsha.jar
```
 I get "cannot execute binary file"

---

### Post by qamelian on 2007-07-19
A .jar file is a Java archive. You run it from the command line using the syntax below.
```
java -jar /path/to/jar_location/name_of_jarfile
```
You can also create a launcher containing the above.

---

### Post by vambo on 2007-07-19
> **K_Soze said:**
> I get "cannot execute binary file"

Is it set executable?

---

### Post by Shin_Gouki2501 on 2007-07-19
yes this is an wwounderfull example of how u can NOT solve  a problem.

1.Be morespecific: 
What u want to try?

2.If its a jar file/ programm make sure u meet the requirements like: having installed an JRE.

3.IF u have installed java i would try soemthing like: java varsha.jar
;)

---

### Post by kavon89 on 2007-07-19
```
java -jar /home/USERNAME/PATH_TO_JAR/varsha.jar
```

You can also right click the file and open with Java. Obviously make sure you've got Java installed before trying to open .jar files. ;)


From the error you posted, it seems you've got a poorly written program that you are trying to execute.

---

### Post by K_Soze on 2007-07-19
first and formost all I am trying to do is install varsha through the .jar file.

after reading the posts I tried this:
root@dad-desktop:/home/dad/Desktop# java -jar /home/dad/Desktop/varsha.jarXlib: connection to ":0.0" refused by server
Xlib: No protocol specified

Exception in thread "main" java.lang.InternalError: Can't connect to X11 window server using ':0.0' as the value of the DISPLAY variable.
        at sun.awt.X11GraphicsEnvironment.initDisplay(Native Method)
        at sun.awt.X11GraphicsEnvironment.access$100(X11GraphicsEnvironment.java:52)
        at sun.awt.X11GraphicsEnvironment$1.run(X11GraphicsEnvironment.java:155)
        at java.security.AccessController.doPrivileged(Native Method)
        at sun.awt.X11GraphicsEnvironment.<clinit>(X11GraphicsEnvironment.java:131)
        at java.lang.Class.forName0(Native Method)
        at java.lang.Class.forName(Class.java:169)
        at java.awt.GraphicsEnvironment.getLocalGraphicsEnvironment(GraphicsEnvironment.java:68)
        at java.awt.Window.init(Window.java:354)
        at java.awt.Window.<init>(Window.java:407)
        at java.awt.Frame.<init>(Frame.java:402)
        at java.awt.Frame.<init>(Frame.java:367)
        at javax.swing.JFrame.<init>(JFrame.java:163)
        at varsha.ui.Varsha.<init>(Varsha.java:31)
        at varsha.ui.Varsha.main(Varsha.java:1243)

root@dad-desktop:/home/dad/Desktop# java varsha.jar
Exception in thread "main" java.lang.NoClassDefFoundError: varsha/jar

As I posted before, I have installed java through Automatix but I don't know if its the correct one. Is there any possiblity it is not the correct version? How do I check?

Thanks to all btw....):P

---

### Post by K_Soze on 2007-07-19
Well it opened....

I had changed the permissions before but I didn't try to "right click" and open the file with java and presto...:KS

I am just wondering why it didn't open with the command line?

Hmmmmmmmm.

PS. thanks to all for the help. Darn solutions are always so stupidly simple.

---

### Post by Shin_Gouki2501 on 2007-07-20
yes and thats the reason why i think UserInterfaces of Programs should be major diffrent...

---


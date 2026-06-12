---
title: "Java runtime enviroment"
date: 2006-09-14
forum: Absolute Beginner Talk
---

### Post by haxer on 2006-09-14
Hello i have installed java yeasterday and i know it works but it seems like i havent got "Java runtime enviroment" How to install that?

---

### Post by Ben Sprinkle on 2006-09-14
[https://sdlc6e.sun.com/ECom/EComActionServlet;jsessionid=96FC4381E18F1B070F80DEB2D42864D7](https://sdlc6e.sun.com/ECom/EComActionServlet;jsessionid=96FC4381E18F1B070F80DEB2D42864D7)
Download latest JRE.

Go in terminal, cd to directory of jre.
Right click the jre.bin=>permissions=>check all execute.
In terminal, type:

./jre-numbers.bin (numbers being the other part of file name)

---

### Post by skymt on 2006-09-14
Have you read [this](https://help.ubuntu.com/community/Java)?

To save you a bit of reading, try running:```
sudo update-java-alternatives -s java-1.5.0-sun
```

EDIT: Ignore the post above me. Nobody needs to do a manual install since Java is in the repositories now.

---

### Post by Ben Sprinkle on 2006-09-14
JRE in the repo's are not the latest though.
I did a manual install for jdk,jre,firefox, and thunderbird.
Latest update is jre1.5.0_08
Repositories don't have update 08.

---

### Post by skymt on 2006-09-14
Why do you need the latest? Are there any bugs you run into that are fixed in 08? The version in the repositories is the one they've tested and know is fairly stable and problem-free. Always use whatever your distro provides unless there's something *specific* you need.

---

### Post by Ben Sprinkle on 2006-09-14
> **skymt said:**
> Why do you need the latest? Are there any bugs you run into that are fixed in 08? The version in the repositories is the one they've tested and know is fairly stable and problem-free. Always use whatever your distro provides unless there's something *specific* you need.

08 Does have fixed bugs, no code changes but alot of bugs fixed, the one in the rep's are not the latest.

---

### Post by haxer on 2006-09-14
I tried sudo update-java-alternatives -s java-1.5.0-sun didnt work ... im having an homepage where im hanging out with some friends from school a couple a year ago and the homepage has an IRC channel and you can click on a buttom to use it onlin trough the homepage but i cant becouse i havent "java runtime enviroment" should i do it in mirc for linux or should i install the java pack?

---

### Post by skymt on 2006-09-14
All web-based Java IRC clients by definition bite. You should use XChat for IRC.

On the Java issue, do you see a Java plugin if you type about:plugins in the Firefox address bar?

---

### Post by haxer on 2006-09-14
I found this on [http://plugindoc.mozdev.org/linux.html#Java](http://plugindoc.mozdev.org/linux.html#Java)  

How to install? 



Java Runtime Environment
Version: 1.4.2_05 or later
Mozilla 1.7: Supported
Firefox 1.0: Supported
FAQ: Java FAQ

   1. Install Java Runtime Environment.
   2. Make a symbolic link to libjavaplugin_oji.so in your Mozilla Plugins directory. Unless you are using an old version of Mozilla, or one you compiled yourself with gcc 2.9x, use the copy located in the plugin/i386/ns7 directory of JRE 5.0, or plugin/i386/ns610-gcc32 if you are using JRE 1.4.2.

Important! Do not copy the plugin to your plugins directory. If you do, Mozilla will crash any time you attempt to view a page containing a Java applet.
Note: Java Runtime Environment 5.0 (1.5.0) has been released. This update fixes many problems that users are having with Java. Upgrading is highly recommended.
Note: The instructions listed here are for the Sun Java Runtime Environment. Other Java Runtime Environments, such as those available from IBM and the Blackdown project, can also be used with Mozilla.
Downloads Sun JRE 5.0 Update 7, IBM JRE 1.4.x or Blackdown JRE 1.4.x

---

### Post by skymt on 2006-09-14
If you have Java installed, you have the Java runtime installed. The question now is whether you have the Java plugin. What does about:plugins give you?

EDIT: Try this:```
sudo aptitude install sun-java5-plugin
```

---

### Post by haxer on 2006-09-14
When i look at the list i dont have it !!

---

### Post by skymt on 2006-09-14
Did you try the command (sudo aptitude install sun-java5-plugin)?

---

### Post by spur on 2006-09-14
I did the same as haxer then created a link to my firefox plugins. This is done by first using > kdesu konquerorthen moving to the file with the plugin in it. Then > kdesu konqueroragain to open up another window. Move to the file that is your plugin directory for firefox. Then select and drag the plugin to the directory and choose 'link here' rather than copy or move.
Of course if your use gnome you will have to use sudo and the window manager for gnome instead of kdesy konqueror. The actual fie will be specific to where you installed them too.
This worked for me.

---

### Post by haxer on 2006-09-15
Hmm .. it works fine for about 2 sec then my whole "internet webbrowser" closes down dont know why :) :cool:

---

### Post by gorgor_bay on 2006-10-04
Edgy with Firefox 2b2 here, with this morning Firefox update, every time I click on a java popup link I get a massive CTD. Same thing with the website quoted here.
Using sun-java5-jre and sun-java5-plugin...

I filled a bug on Firefox launchpad, don't hesitate to contribute to this bug page if you are experiencing the same issue.
[https://launchpad.net/distros/ubuntu/+source/firefox/+bug/63913](https://launchpad.net/distros/ubuntu/+source/firefox/+bug/63913)

---


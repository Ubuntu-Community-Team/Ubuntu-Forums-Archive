---
title: "Java 6 JRE Plugin for Firefox"
date: 2007-12-13
forum: Absolute Beginner Talk
---

### Post by cubical10 on 2007-12-13
Yes yet another question on this topic.

I installed the Java 6 packages.
$ dpkg --get-selections | grep -i java6
sun-java6-bin                                   install
sun-java6-fonts                                 install
sun-java6-jdk                                   install
sun-java6-jre                                   install
sun-java6-plugin                                install

I then set it as default.
$ sudo update-alternatives --config java

There are 4 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/gij-4.2
*         2    /usr/lib/jvm/java-6-sun/jre/bin/java
          3    /usr/bin/cacao
 +        4    /usr/lib/j2se/1.4/bin/java

Press enter to keep the default[*], or type selection number:

But i cannot get Firefox (2.0.0.11) to use the version 6 plugin, it always reverts to 1.4.2 when i try to verify it using [[COLOR="Blue"]http://www.java.com/en/download/installed.jsp[/COLOR]]("http://www.java.com/en/download/installed.jsp")

Entering about:plugins in the address bar in Firefox shows that its there.
Java(TM) Plug-in 1.6.0_03-b05

    File name: libjavaplugin_oji.so
    Java(TM) Plug-in 1.6.0_03


So what step am I missing?

---

### Post by loverman210 on 2007-12-13
I am having exactly the same issue...

---

### Post by Bert_2 on 2007-12-13
For as far as I know it is java 6 and jre 1.4 that we are now so isn't it just working right ?

---

### Post by ib.lundgren on 2007-12-13
Hey!

I am not sure if it would help but in case you don't really need the 1.4 version, uninstall it and try with only 1.6 installed.

---

### Post by jefferz on 2007-12-13
go to

[http://www.java.com/en/download/help/testvm.xml](http://www.java.com/en/download/help/testvm.xml)

if it doesn;t work then type in your address bar

about:plugins

Check to see if there is a plugin called

"GCJ"

If so, from terminal run this

"sudo apt-get remove gcjwebplugin"

Fixed all my java issues

---

### Post by rsambuca on 2007-12-13
Are you running 32-bit or 64-bit Ubuntu?

---

### Post by jefferz on 2007-12-13
32 bit ubuntu gutsy 7.10 (clean istall, not upgrade)

---

### Post by SunnyRabbiera on 2007-12-13
installing java is a little rough on ubuntu but I have a fix:
I also have a method:
this is an easy fix (sorta),
first you go to the java website:
[here]("http://www.java.com/en/download/linux_manual.jsp?locale=en&host=www.java.com")

after that download the self extracting file (dont bother with the RPM, its not worth your time)
after that is done downloading go to where you downloaded your file (if all your files download to the desktop though, please take the file to your home folder or something, just open up your home directory and drag and drop.)
after this you will need to open up synaptic
now what you will need is something called nautilus-open-terminal, as this will allow you to open a terminal inside your desired directory (for some odd reason this is not enabled in ubuntu, it honestly should be)
now after installing it you will have to restart your session... there is no real easy way to do this bit I am afraid.
now after restart go to whatever directory you put the java installer in and under "file" in the menu go to "open in terminal"
after this type in:
sudo sh jre-6u3-linux-i586.bin
now you will have to go through the license junk of java, just keep on pressing space until it asks
Do you agree to the above license terms? [yes or no]
its annoying to get to it, but just type in "yes" and all will be fine
after the installation is done just close the terminal (it will say done after its completed)

---

### Post by cubical10 on 2007-12-14
> **jefferz said:**
> go to about:plugins

Check to see if there is a plugin called

"GCJ"

If so, from terminal run this

"sudo apt-get remove gcjwebplugin"

Fixed all my java issues

Thank you, that did the trick!

---


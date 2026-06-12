---
title: "Help installing eclipse PDT"
date: 2007-11-02
forum: Absolute Beginner Talk
---

### Post by rungss on 2007-11-02
Hello,
I am trying to switch to Linux completely and hopefully will succeed this time.

I want to know how do I install Applications which are not listed in any of the Repositories in Synaptic Package manager.

For example the first application that I want to install is Eclipse PDT.
I could install it through Update manager but I prefer to keep different copies of Eclipse for different Development Purpose separate this is what I used to do in Windows.

I downloaded the zipped package for eclipse PDT.
I hope I will be able to run it if I unzip it into any folder and run the exe file in the root folder.

I want to know whats the best way to install such applications.

If I just have to unzip the tarball and use it should I unzip it to a location like /var/lib/eclipse-pdt(I choose this location as the Eclipse classic that I installed through the package manager used this location) I tried to do that but I couldn't create a directory in this folder.
In this scenario what is advised. Should I unzip them in a folder inside my home Directory? or should it be in a folder structure as for other application.

Or is there a way that I can use from command lie or through the package manager to install the application so that the Package manager has the information about this application and can be monitored.

Thanks in advance.
Bijay

---

### Post by overdrank on 2007-11-02
> **rungss said:**
> Hello,
I am trying to switch to Linux completely and hopefully will succeed this time.

I want to know how do I install Applications which are not listed in any of the Repositories in Synaptic Package manager.

For example the first application that I want to install is Eclipse PDT.
I could install it through Update manager but I prefer to keep different copies of Eclipse for different Development Purpose separate this is what I used to do in Windows.

I downloaded the zipped package for eclipse PDT.
I hope I will be able to run it if I unzip it into any folder and run the exe file in the root folder.

I want to know whats the best way to install such applications.

If I just have to unzip the tarball and use it should I unzip it to a location like /var/lib/eclipse-pdt(I choose this location as the Eclipse classic that I installed through the package manager used this location) I tried to do that but I couldn't create a directory in this folder.
In this scenario what is advised. Should I unzip them in a folder inside my home Directory? or should it be in a folder structure as for other application.

Or is there a way that I can use from command lie or through the package manager to install the application so that the Package manager has the information about this application and can be monitored.

Thanks in advance.
Bijay

Hi and welcome, you can not use exe on Ubuntu but if this is the Eclipse that you are referring too
[http://flurdy.com/docs/eclipse/install.html](http://flurdy.com/docs/eclipse/install.html)
Also for future reference 
[http://cutlersoftware.com/ubuntuinstall/](http://cutlersoftware.com/ubuntuinstall/)
Good luck! :KS

---

### Post by rungss on 2007-11-02
> **overdrank said:**
> Hi and welcome, you can not use exe on Ubuntu but if this is the Eclipse that you are referring too
[http://flurdy.com/docs/eclipse/install.html](http://flurdy.com/docs/eclipse/install.html)
Also for future reference 
[http://cutlersoftware.com/ubuntuinstall/](http://cutlersoftware.com/ubuntuinstall/)
Good luck! :KS

The first link doesn't work.

I tried the 2nd link but couldn't resolve it..
still trying...

---

### Post by rungss on 2007-11-03
Strangely I can run the exe file..

but am having other issues now..

am getting an error message "Error creating view.."

Basically am getting one kind of error or another I guess for permission issues or may bebecause of the two diff instances of Eclipse.

I see a hidden folder named .eclipse in my home folder.

is there by chance any conflict for the two eclipse instances which might probably be sharing the same .eclipse folder.

the Workspace choosen for the two are different.

any idea???

---

### Post by pstracha on 2007-12-08
I was having the same problem with Eclipse, I fixed it by downloading a new JRE and launching Eclipse with the -vm switch.

**1. Download & Install JRE**
[http://java.sun.com/javase/downloads/index_jdk5.jsp](http://java.sun.com/javase/downloads/index_jdk5.jsp)

**2. Launch Eclipse**
```
eclipse -vm /full/path/to/java/bin/java
```

See for more info:
[http://wiki.eclipse.org/IRC_FAQ#I_just_installed_Eclipse_on_Linux.2C_but_it_does_not_start._What_is_the_problem.3F](http://wiki.eclipse.org/IRC_FAQ#I_just_installed_Eclipse_on_Linux.2C_but_it_does_not_start._What_is_the_problem.3F)

---

### Post by csbened on 2008-02-24
Hello,
There is a possibility to install bothe Eclipse for Java and Eclipse PDT for PHP
1. install Eclipse normally, using synaptic package manager or aptitute install eclipse
(check if you have java installed , if not install it. Please be aware gij is not
as good as sun java) 
2. Download eclipse pdt from 
[http://download.eclipse.org/tools/pdt/downloads/](http://download.eclipse.org/tools/pdt/downloads/)
3. unpack the whole thing (using tar and gzip or simply the archive manager) in
/usr/lib/eclipsepdt
4. copy the file  usr/bin/eclipse as usr/bin/eclipsepdt
5. modify this file, replacing all directory names eclipse to eclipsepdt
(please dont modify filename eclipse, just the directories). Also comment line 
# STARTUP=
The only place where I did not modify the directory name was /etc/eclipse/java_home 
6. Create shortcuts to your desktop/menu to usr/bin/eclipsepdt
7. You might want to use a different icon.
Everything done, should work. Now if you add a plugin please copy it to eclipsepdt, or
do it twice.

---

### Post by irvinpl on 2008-03-11
Well, this is only one working solution for me! Very big thx!
:guitar:

---


---
title: "*frustrated* Java not working"
date: 2008-02-03
forum: Absolute Beginner Talk
---

### Post by AutumnPhoenix on 2008-02-03
I have tried every trick to get Java working.  Termanal, synaptic, and simply add/remove new programs.

I'm not sure if its Java or firefox.  I'm runing Gusty Gibson xubuntu on a Thinkpad z60m.  I simply dosn't work in my browser.

---

### Post by Bothered on 2008-02-03
Just to be sure, have you tried:

```
sudo apt-get install sun-java6-plugin
```

Does this command give any error messages? Which browser are you using?

---

### Post by AutumnPhoenix on 2008-02-03
> Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.1.11) Gecko/20071204 Ubuntu/7.10 (gutsy) Firefox/2.0.0.11

and tried the command...still nothing

---

### Post by billgoldberg on 2008-02-03
It might be worth it to check out [this program ]("http://ubuntuforums.org/showthread.php?t=613462").

It will install java on your system (amonst many).

I'm pretty sure it just uses the same command as the  previous poster mentioned but you never know.

---

### Post by AutumnPhoenix on 2008-02-03
I'm having problems with that, anything more?

> E: Couldn't find package lib32z1

---

### Post by omi291 on 2008-02-03
> **AutumnPhoenix said:**
> E: Couldn't find package lib32z1

I'm pretty nooby at linux myself, but i would suggest going to synaptic package manager and trying to install that package...or using the terminal to install it:)

---

### Post by AutumnPhoenix on 2008-02-03
how would I do that?

(I'm disgustingly n00b)

---

### Post by st33med on 2008-02-03
Are you using a 64-bit operating system?

---

### Post by AutumnPhoenix on 2008-02-03
I don't know...how would I find that out?  I'm using xubuntu...

---

### Post by AutumnPhoenix on 2008-02-03
*bump*

---

### Post by bruce89 on 2008-02-03
> **AutumnPhoenix said:**
> I don't know...how would I find that out?  I'm using xubuntu...

```
uname -a
```

---

### Post by AutumnPhoenix on 2008-02-03
> Linux PhoenixWolf 2.6.22-14-generic #1 SMP Tue Dec 18 08:02:57 UTC 2007 i686 GNU/Linux

I still don't get it...I'm sorry..how can I tell if thats 64?

---

### Post by bruce89 on 2008-02-03
> **AutumnPhoenix said:**
> I still don't get it...I'm sorry..how can I tell if thats 64?

It isn't. The last bit is *i686*, not *x86_64*.

Is Java listed in about:plugins? (put in the the location bar of the browser)

---

### Post by arijarot on 2008-02-03
1. Make sure you've installed "sun-java6-bin" "sun-java-6jre" and "sun-java6-plugin"

2. Once that's done, you need to make a (soft/symbolic) link of libjavaplugin_oji.so from your .mozilla's plugin directory to its directory, that is, 

   a. open terminal
   b. change directories to:

```
cd ~/.mozilla/plugins
```
   
   c. add the link:

```
ln -s /usr/lib/jvm/java-6-sun-1.6.0.03/jre/plugin/i386/ns7/libjavaplugin_oji.so 
```

Restart firefox, and make sure java is enabled in the preferences and that you've got the latest version of firefox.

---

### Post by AutumnPhoenix on 2008-02-03
no, not in the Help --> about in firefox...

however the boxes are checked in Edit --> preferances

---

### Post by AutumnPhoenix on 2008-02-03
> bash: cd: /root/.mozilla/plugins: No such file or directory


is what I get when I do the second step

---

### Post by arijarot on 2008-02-03
> **AutumnPhoenix said:**
> is what I get when I do the second step

```
cd /home/<username>/.mozilla/plugins
```

---

### Post by bruce89 on 2008-02-03
> **AutumnPhoenix said:**
> no, not in the Help --> about in firefox...

however the boxes are checked in Edit --> preferances

about:config in the address bar.

---

### Post by AutumnPhoenix on 2008-02-03
arijarot thank you!  I fixed it with that!  I solved a week-long problem!

---

### Post by arijarot on 2008-02-03
> **AutumnPhoenix said:**
> arijarot thank you!  I fixed it with that!  I solved a week-long problem!

No problem:)

---

### Post by PaulSipot on 2008-02-03
I usually do a manual installation, I find it much better. Download java from java.sun.com (the binary one that extracts all contents into a directory), move that directory to where you want it. Then you use it as default by issuing simmilar commands to this:

sudo alternatives --install /usr/bin/java java /pathToWhereThatJavaDirectoryIs/bin/java 1

and the same for the other bin files from the java installation, ex:

sudo alternatives --install /usr/bin/jar jar /pathToWhereThatJavaDirectoryIs/bin/jar 1


Then you can try it, 
java -version
And it should print the version that you just installed

If it does not do that then:
sudo alternatives --config java
And choose the one you just installed.

(Also the command might be 'update-alternatives' instead of 'alternatives')

---

### Post by Bothered on 2008-02-05
> **AutumnPhoenix said:**
> bash: cd: /root/.mozilla/plugins: No such file or directory 
is what I get when I do the second step

Did you run the command as root? Or with sudo? Your home directory should be /home/[username], not /root.

---

### Post by SusieSA on 2008-02-07
I am also trying to get Java to work and I have installed the files, but I don't seem to have a plugin directory.

Previous instructions said that I should:

cd ~/.mozilla/plugins

I can see the .mozilla directory, but I do not have the plugins directory.  

When I try "about:plugins" in the address line, the java stuff looks like this:

	Description 	Suffixes 	Enabled
application/x-java-vm 	Java 		Yes
application/x-java-applet 	Java 		Yes
application/x-java-applet;version=1.1 	Java 		Yes
application/x-java-applet;version=1.1.1 	Java 		Yes
application/x-java-applet;version=1.1.2 	Java 		Yes
application/x-java-applet;version=1.1.3 	Java 		Yes
application/x-java-applet;version=1.2 	Java 		Yes
application/x-java-applet;version=1.2.1 	Java 		Yes
application/x-java-applet;version=1.2.2 	Java 		Yes
application/x-java-applet;version=1.3 	Java 		Yes
application/x-java-applet;version=1.3.1 	Java 		Yes
application/x-java-applet;version=1.4 	Java 		Yes
application/x-java-applet;version=1.4.1 	Java 		Yes
application/x-java-applet;version=1.4.2 	Java 		Yes
application/x-java-applet;version=1.5 	Java 		Yes
application/x-java-applet;version=1.6 	Java 		Yes
application/x-java-applet;jpi-version=1.6.0_03 	Java 		Yes
application/x-java-bean 	Java 		Yes
application/x-java-bean;version=1.1 	Java 		Yes
application/x-java-bean;version=1.1.1 	Java 		Yes
application/x-java-bean;version=1.1.2 	Java 		Yes
application/x-java-bean;version=1.1.3 	Java 		Yes
application/x-java-bean;version=1.2 	Java 		Yes
application/x-java-bean;version=1.2.1 	Java 		Yes
application/x-java-bean;version=1.2.2 	Java 		Yes
application/x-java-bean;version=1.3 	Java 		Yes
application/x-java-bean;version=1.3.1 	Java 		Yes
application/x-java-bean;version=1.4 	Java 		Yes
application/x-java-bean;version=1.4.1 	Java 		Yes
application/x-java-bean;version=1.4.2 	Java 		Yes
application/x-java-bean;version=1.5 	Java 		Yes
application/x-java-bean;version=1.6 	Java 		Yes
application/x-java-bean;jpi-version=1.6.0_03 	Java 		Yes

Nothing much about Java 6.  What am I doing wrong?

Thanks.

---

### Post by arijarot on 2008-02-07
> **SusieSA said:**
> I am also trying to get Java to work and I have installed the files, but I don't seem to have a plugin directory.

Previous instructions said that I should:

cd ~/.mozilla/plugins

I can see the .mozilla directory, but I do not have the plugins directory.  

When I try "about:plugins" in the address line, the java stuff looks like this:

	Description 	Suffixes 	Enabled
application/x-java-vm 	Java 		Yes
application/x-java-applet 	Java 		Yes
application/x-java-applet;version=1.1 	Java 		Yes
application/x-java-applet;version=1.1.1 	Java 		Yes
application/x-java-applet;version=1.1.2 	Java 		Yes
application/x-java-applet;version=1.1.3 	Java 		Yes
application/x-java-applet;version=1.2 	Java 		Yes
application/x-java-applet;version=1.2.1 	Java 		Yes
application/x-java-applet;version=1.2.2 	Java 		Yes
application/x-java-applet;version=1.3 	Java 		Yes
application/x-java-applet;version=1.3.1 	Java 		Yes
application/x-java-applet;version=1.4 	Java 		Yes
application/x-java-applet;version=1.4.1 	Java 		Yes
application/x-java-applet;version=1.4.2 	Java 		Yes
application/x-java-applet;version=1.5 	Java 		Yes
application/x-java-applet;version=1.6 	Java 		Yes
application/x-java-applet;jpi-version=1.6.0_03 	Java 		Yes
application/x-java-bean 	Java 		Yes
application/x-java-bean;version=1.1 	Java 		Yes
application/x-java-bean;version=1.1.1 	Java 		Yes
application/x-java-bean;version=1.1.2 	Java 		Yes
application/x-java-bean;version=1.1.3 	Java 		Yes
application/x-java-bean;version=1.2 	Java 		Yes
application/x-java-bean;version=1.2.1 	Java 		Yes
application/x-java-bean;version=1.2.2 	Java 		Yes
application/x-java-bean;version=1.3 	Java 		Yes
application/x-java-bean;version=1.3.1 	Java 		Yes
application/x-java-bean;version=1.4 	Java 		Yes
application/x-java-bean;version=1.4.1 	Java 		Yes
application/x-java-bean;version=1.4.2 	Java 		Yes
application/x-java-bean;version=1.5 	Java 		Yes
application/x-java-bean;version=1.6 	Java 		Yes
application/x-java-bean;jpi-version=1.6.0_03 	Java 		Yes

Nothing much about Java 6.  What am I doing wrong?

Thanks.

Try to make the plugins folder in .mozilla and add the link.

---

### Post by SusieSA on 2008-02-08
I was getting little response out of this post, so I posted a new entry called "Java Plugin." and that was resolved.  Please refer to that posting.

---


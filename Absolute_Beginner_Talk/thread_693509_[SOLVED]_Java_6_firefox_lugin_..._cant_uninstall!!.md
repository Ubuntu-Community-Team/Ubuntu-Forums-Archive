---
title: "[SOLVED] Java 6 firefox lugin ... cant uninstall!!!"
date: 2008-02-11
forum: Absolute Beginner Talk
---

### Post by drtre on 2008-02-11
i've installed jre-6u3-linux-amd64 on my ubuntu amd 64 box supposing it contains a plugin for firefox but it doesn't. now i dont know how to uninstall it. any help?

---

### Post by jordanmthomas on 2008-02-11
```
sudo apt-get remove jre-6u3-linux-amd64
```
That's odd, though, I would think it has the firefox plugin as well

---

### Post by drtre on 2008-02-11
no it aint got any plugin for firefox. the latest jre that have a plugin for firefox is jre 1.4 by blackdown. crazy though. hope they reealease the java 6 plugin soon. anyway thank you.

---

### Post by drtre on 2008-02-11
sorry but i've have not installed it by synaptic or repos. i've downloaded it from java website and installed it.

---

### Post by drtre on 2008-02-11
excuse me .... no one knows how to remove a jre???? please my computer is full of different jres and i dont one no new one so i have to uninstall it.

---

### Post by jan quark on 2008-02-11
try

```
sudo dpkg -r name of package
```

---

### Post by drtre on 2008-02-11
let me explain how i installed it.

first i downloaded it from java.com
the filename is  jre-6u3-linux-amd64.bin
then i follow the instructions in [java.com]("http://www.java.com/en/download/help/5000011400.xml")
and i found out that there is no plugin for firefox in java 6.
now i want to remove it. and "sudo dpkg -r " didn't work cuz i aint got no package to remove.
i know the instruction is for redhat and suse but i thought it could be apply to ubuntu as well.

---

### Post by HereInOz on 2008-02-11
Check out these instructions for creating the symbolic link from the Java directory to the Firefox plugins directory.

[http://www.mozilla.org/support/firefox/faq#q2.2](http://www.mozilla.org/support/firefox/faq#q2.2)

Essentially you need to create a symbolic link from the java plugin (libjavaplugin_oji.so) to the Firefox plugins directory which is /usr/lib/firefox/plugins.

---

### Post by drtre on 2008-02-11
thank you.. but i know that there is no plugin at all in java 6 there is no such plugin to make a link of. the latest one is java 1.4 that supports firefox. i just want to remove this java6 please. do i have to delete the folder?is it enough? god....

---

### Post by gandaran on 2008-02-11
> **drtre said:**
> thank you.. but i know that there is no plugin at all in java 6 there is no such plugin to make a link of. the latest one is java 1.4 that supports firefox. i just want to remove this java6 please. do i have to delete the folder?is it enough? god....

check on sun java site for instructions on removal, if there aren't any then you just have to delete everything related to sun java 6 on your file system.
 use synaptic to install java, just select sun java 6 plugin, it will install all java packages needed.

---

### Post by drtre on 2008-02-11
thank you. i've installed java 6 from synaptic but it aint got any plugin so i thought maybe this one from sun have one. but it didnt either. 
so as i guessed i should delete it manually. thank you anyway guys.

---

### Post by ThrobbingBrain66 on 2008-02-11
To get the Firefox plugin, you have to install the sun-java6-plugin package.

You may have to update your java alternatives as well:

```
update-alternatives --config java
```

---

### Post by gandaran on 2008-02-11
> **drtre said:**
> thank you. i've installed java 6 from synaptic but it aint got any plugin so i thought maybe this one from sun have one. but it didnt either. 
so as i guessed i should delete it manually. thank you anyway guys.

it does have , look it up on synaptic « sun java6 plugin » if it doesn't work maybe it's due to having two java installed

---

### Post by drtre on 2008-02-11
there is no such package in my synaptic. iced tea 7 have a plugin for firefox. but it doesnt work as good as sun-java plugins. but unfortunately there is no plugin for java 6 . the only and latest one is java 1.4 that have the plugin. and i'm talking about ubuntu amd64 if you've mentioned. maybe there is sun-java 6 plugins for 32bit systems.

---

### Post by gandaran on 2008-02-11
> **drtre said:**
> there is no such package in my synaptic. iced tea 7 have a plugin for firefox. but it doesn't work as good as sun-java plugins. but unfortunately there is no plugin for java 6 . the only and latest one is java 1.4 that have the plugin. and i'm talking about ubuntu amd64 if you've mentioned. maybe there is sun-java 6 plugins for 32bit systems.

okay I don't know about 64-bit, but I'm supposing it must be the same as the 32-bit.
assuming you have all the repos enabled, and there is no plugin on synaptic could be due to java all ready installed, it's sometimes happens.
you must get rid of that java first then install using synaptic.

---

### Post by drtre on 2008-02-11
well... i think this is getting a bit complicated. let's flat it out. i just want to remove the sun-java6 for amd 64 bit system that i've downloaded it from java.com. i'll get to installing or removing synptic packages later.:)

---

### Post by gandaran on 2008-02-11
you will find the sun java packages on the multiverse repository, have you enabled this repo?
there is also a sun java5 plugin alongside the sun java6 plugin, you can also use this one.

---

### Post by drtre on 2008-02-11
yes i've enabled it and i've already had sun-java-6 (repos)  installed on my system. i dont want to know how to install java from synaptic. i just wanna know how to remove this java i've installed from java.com. i dont care about plugins and synaptic nomore. i just wanna know hpow to remove this folder. deleting it will suffice?:confused:

---

### Post by gandaran on 2008-02-11
> **drtre said:**
> yes i've enabled it and i've already had sun-java-6 (repos)  installed on my system. i dont want to know how to install java from synaptic. i just wanna know how to remove this java i've installed from java.com. i dont care about plugins and synaptic nomore. i just wanna know hpow to remove this folder. deleting it will suffice?:confused:

yes deleting will do the job, check /usr for java  also /usr/lib and /usr/share
user the file finder, search for java, java 6 and jvm

before deleting anything check /usr/lib/mozilla/plugins/ for a libjavaplugin.so file, post back here if you find it there.

---

### Post by drtre on 2008-02-11
> **gandaran said:**
> yes deleting will do the job, check /usr for java  also /usr/lib and /usr/share
user the file finder, search for java, java 6 and jvm

before deleting anything check /usr/lib/mozilla/plugins/ for a libjavaplugin.so file, post back here if you find it there.
thank you very much. you did me a real big favor. by the way there was a plugin in /usr/lib/mozilla/plugins
but as i told you it is for the icedtea 7. it is not a sun java plugin. if i want to install sunjava plugin i have to install jre 1.4 cuz there is no support for firefox plugin in later versions in ubuntu amd64.

---

### Post by gandaran on 2008-02-11
> **drtre said:**
> thank you very much. you did me a real big favor. by the way there was a plugin in /usr/lib/mozilla/plugins
but as i told you it is for the icedtea 7. it is not a sun java plugin. if i want to install sunjava plugin i have to install jre 1.4 cuz there is no support for firefox plugin in later versions in ubuntu amd64.

I find it hard to believe there is no plugin for 64-bit, I haven't seen any post's complaining about that! you'll just have to ask the 64-bit user's if it's true.

---

### Post by drtre on 2008-02-11
> **gandaran said:**
> I find it hard to believe there is no plugin for 64-bit, I haven't seen any post's complaining about that! you'll just have to ask the 64-bit user's if it's true.

i know its weird. but its true. if you want a latest plugin you have to install icedtea which is a implementation of java by redhat. but if you want sun-java itself you have to stick with java 1.4 cuz its the only version that supports firefox plugins for 64-bit ubuntu.

---

### Post by bollix47 on 2008-02-11
There is no reliable 64-bit browser plugin for java until sun brings out version 7.

Most people that require a java plugin that 'just works' install a 32-bit browser on their 64-bit ubuntu systems.

There are scripts that will do this fairly automatically including plugins.

One is found [here]("http://ubuntuforums.org/showthread.php?t=202537&highlight=swiftweasel").

---

### Post by schaumkeks on 2008-02-11
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/sun-java6/+bug/104512](https://bugs.launchpad.net/ubuntu/+source/sun-java6/+bug/104512) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
[Bug also reported upstream at sun's site]("http://bugs.sun.com/bugdatabase/view_bug.do?bug_id=4802695").

Bye, Sven

---

### Post by drtre on 2008-02-11
thank you guys very much . i think i should mark it as solved.:popcorn:

---


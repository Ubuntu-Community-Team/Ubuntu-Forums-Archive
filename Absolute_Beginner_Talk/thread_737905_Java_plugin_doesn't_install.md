---
title: "Java plugin doesn't install"
date: 2008-03-28
forum: Absolute Beginner Talk
---

### Post by Tepear on 2008-03-28
I have read many many many google pages, many of which were from this very website. No matter what I do, I can't seem to get the java to install. I've done it through the package manager, and the terminal. The packages seem to install but when I check the about:plugin page, it is not listed, and things such as runescape do not load. I am using
7.1 The Gutsy Gibbon.


I just installed it today and am already frustrated :lolflag:


Edit: I forgot to mention that I have tried both v5 and v6. I have tried installing and uninstalling completely  each several times with no success. I have uninstalled any cgi java items on my computer.

All I want is to be able to play runescape =P (I love games... I need at least one)

---

### Post by nebu on 2008-03-28
u have to get the right jvm to be ur default choice.....

try this...
> sudo update-alternatives --config java

select the jvm which is produced by sun microsystems and it should be labelled as java 6.....

to check if u selected the right one just do...
> java -version

ur jvm should be version *Java(TM) SE Runtime Environment (build 1.6.0_03-b05)* if u have the latest versions from the repositories

---

### Post by gandaran on 2008-03-28
> **Tepear said:**
> I have read many many many google pages, many of which were from this very website. No matter what I do, I can't seem to get the java to install. I've done it through the package manager, and the terminal. The packages seem to install but when I check the about:plugin page, it is not listed, and things such as runescape do not load. I am using
7.1 The Gutsy Gibbon.


I just installed it today and am already frustrated :lolflag:


Edit: I forgot to mention that I have tried both v5 and v6. I have tried installing and uninstalling completely  each several times with no success. I have uninstalled any cgi java items on my computer.

All I want is to be able to play runescape =P (I love games... I need at least one)

did you install the java plugin ?
which version of ubuntu you running 32-bit or 64-bit?
for the 32-bit you install the sun-java6-plugin
for 64-bit you install icedtea-java plugin, as there is no 64-bit sun-java plugin

---

### Post by Tepear on 2008-03-28
When I did the sudo update, it said
There is only 1 program which provides java
(/usr/lib/jvm/java-6-sun/jre/bin/java). Nothing to configure.

And when I did java-version it said
The program 'java' can be found in the following packages:
 * cacao
 * j2re1.4
 * kaffe
 * jamvm
 * java-gcj-compat
 * gij-4.1
 * gij-4.2
 * sablevm
Try: sudo apt-get install <selected package>
bash: java: command not found

Yes I install the plugin, and I am using the 32 bit version

---

### Post by gandaran on 2008-03-28
check firefox settings » edit » preferences » content, see if java is enabled

---

### Post by Tepear on 2008-03-28
It is, I've checked it a few times (and just did again.)

---

### Post by gandaran on 2008-03-28
can you confirm that the plugin is installed?
go to synaptic, look up sun-java6-plugin see if the little box next to it is green, that means it's installed.

---

### Post by Tepear on 2008-03-28
[http://img182.imageshack.us/img182/6748/plugintr8.png](http://img182.imageshack.us/img182/6748/plugintr8.png)


Its installed.

---

### Post by gandaran on 2008-03-28
okay, now check these two folders on the file system, /usr/lib/mozilla/plugins and /usr/lib/firefox/plugins, in the plugins folder there should be a libjavaplugin.so file in both folders, see if correct.

---

### Post by nebu on 2008-03-28
install these!!

the jre and the pluggin

---

### Post by Tepear on 2008-03-28
> **nebu said:**
> install these!!

the jre and the pluggin

I have those installed >>; like I said I've read a lot of sites.


Yes the plugin is in both folders (But they both have green circles next to them?)
Edit2: Ok, so the links are broken and linking to the cgj that used to be on there. How do I link it to the new sun java?

---

### Post by gandaran on 2008-03-28
> **Tepear said:**
> I have those installed >>; like I said I've read a lot of sites.


Yes the plugin is in both folders (But they both have green circles next to them?)
Edit2: Ok, so the links are broken and linking to the cgj that used to be on there. How do I link it to the new sun java?

green circles next to them ? can you post an image?
look, in this case, I don't know how to make a link to sun java, but I guess you have run some commands or installed other java packages or maybe another installed program that is conflicting, you must have done something to get the plugin blocked.
I recommend you to uninstall all java packages, use synaptic for that, choose _complete removal_, then go to your home folder and delete any java folder or file you can find, only then select sun-java6-plugin for install, synaptic will install all other packages that are necessary.
try it , I would !

one way to make a link is to just copy the libjavaplugin.so file to a plugin folder where it can be used, try coping to home/user/.mozilla/plugins (you'll have to make the plugins folder) just to see how it behaves (without the green circles).

---

### Post by jaredssix on 2008-03-28
I'm not really one to answer questions, but I feel your pain so perhaps I can help. 
I believe gandaran is on the right track. I just spent nearly two hours on the phone with a tech guy, and we tried everything, and finally learned that Mozilla was only looking in the home/.mozilla hidden directory for plug-ins. We installed a symbolic link in ~/.mozilla/plugins to the plug-in's place of residence, and we were good to go!

Again, I'm fairly new, and this is my understanding of the process. If I'm completely misguided, let me know and I'll remove this post!

Don't forget to restart Mozilla before checking Java.

Code for reference:
```
jared@JaredsDellUbuntu:/usr/lib/mozilla-firefox/plugins$ cd
jared@JaredsDellUbuntu:~$ ls
brother.log  Desktop  Documents  EWB  Examples  Music  PDF  Pictures  Project  Public  SchoolSpring08  Templates  Travis_Jared_Resume2008.pdf  Videos
jared@JaredsDellUbuntu:~$ cd .mozilla
.mozilla/             .mozilla-thunderbird/ 
jared@JaredsDellUbuntu:~$ cd .mozilla
[email]jared@JaredsDellUbuntu:~/.mozi[/email]lla$ cd plugins
[email]jared@JaredsDellUbuntu:~/.mozi[/email]lla/plugins$ ls -l
total 7948
-rw-r--r-- 1 jared jared     856 2006-12-15 13:51 flashplayer.xpt
-rwxr-xr-x 1 jared jared 8119784 2007-11-20 15:24 libflashplayer.so
[email]jared@JaredsDellUbuntu:~/.mozi[/email]lla/plugins$ sudo ln -s /usr/lib/jvm/java-1.5.0-sun-1.5.0.13/jre/plugin/i386/ns7/libjavaplugin_oji.so
[email]jared@JaredsDellUbuntu:~/.mozi[/email]lla/plugins$ ls -l
total 7952
-rw-r--r-- 1 jared jared     856 2006-12-15 13:51 flashplayer.xpt
-rwxr-xr-x 1 jared jared 8119784 2007-11-20 15:24 libflashplayer.so
lrwxrwxrwx 1 root  root       77 2008-03-28 15:03 libjavaplugin_oji.so -> /usr/lib/jvm/java-1.5.0-sun-1.5.0.13/jre/plugin/i386/ns7/libjavaplugin_oji.so
```

---

### Post by Tepear on 2008-03-28
Thanks for all the replies guys, I found out what the problem was.

I had to go into the user/whatever thing and delete the messed up plugin. Then I removed all java type things. I reinstalled java-6 and all its dependencies, and then had to find the plugin by searching through my files. After finding it, I right clicked on it and made a link. Then I moved the link to the appropriate folders and renamed them properly.

I can play runescape now ^^;

---

### Post by demarshall on 2008-03-30
I just read through this conversation and I'm having problems with the Firefox Java plugin. I followed the directions on Sun's web site to make a link in the /usr/lib/firefox/plugin directory from the file as per the instructions with the following command but with that link in the Firefox plugin directory, Firefox crashes as soon as it starts up.

sudo ln -s /usr/lib/jvm/java-6-sun/jre/plugin/i386/ns7-gcc29/libjavaplugin_oji.so

Does anybody see anything wrong with my command or have any idea why the link causes Firefox to crash.

---


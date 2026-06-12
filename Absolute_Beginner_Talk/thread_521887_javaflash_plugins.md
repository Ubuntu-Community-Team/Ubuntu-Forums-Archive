---
title: "java/flash plugins"
date: 2007-08-09
forum: Absolute Beginner Talk
---

### Post by FireStorm102389 on 2007-08-09
ok, i recently got my internet on my computer working...so im using kubuntu...now the only problem is i need the java and flash plugins to work on here...idk if they r installed or not, but i need to know how to turn them on or get them...im using konqueror...unless there is a website that uno of that i could install firefox easily...but i would still need to know how to get the plugins/make them work

---

### Post by bjarneh on 2007-08-09
to get firefox type

sudo apt-get install firefox

into a terminal or shell, or use the synaptic package manager

System-> Adm. -> Synaptic

firefox will ask you to install flash first time you enter at flash file...


for Java there is a bit more fiddeling... but there is a howto on the firefox website

first install the sun-java instead of the gij

$ sudo apt-get install sun-java5-jdk

for instance, then it's only a matter of creating a symbolik link to a file

something like this (in a terminal)

cd  /usr/lib/firefox/plugins

sudo ln -s  /usr/lib/jvm/java-1.5.0-sun-1.5.0.11/jre/plugin/i386/ns7/libjavaplugin_oji.so .

that shoud be it...

---

### Post by UltraMathMan on 2007-08-09
Java is available throught the repositories ```
sudo apt-get install java2-runtime
``` Flash is available on the web from Adobe [http://www.adobe.com/products/flashplayer/]("http://www.adobe.com/products/flashplayer/") and is accompanied by installation instructions.

-Hope this helps :)

---

### Post by FireStorm102389 on 2007-08-09
im sorry but none of that worked...but i did find out how to install java...i installed it but the screen in the terminal came up and I couldn't click the OK button at the bottom, i tried everything in the termina, but it didn't work so im going to b rebooting my comp, and hopefully that works...idc what browser I have as long as it works, and i just need the plugins for konquerer.

---

### Post by FireStorm102389 on 2007-08-09
ok, im having a problem here...how do i get it so that it cancels the java thing?...in the terminal i got it to install a java and it went to this screen that i couldn't press ok on, and then i restart it and open the adept manager and it says i can't do anything till the process in the terminal is done and idk how to cancel it and i cant even see it ne more cuz i restarted my comp.

---

### Post by UltraMathMan on 2007-08-09
> **FireStorm102389 said:**
> ok, im having a problem here...how do i get it so that it cancels the java thing?...in the terminal i got it to install a java and it went to this screen that i couldn't press ok on, and then i restart it and open the adept manager and it says i can't do anything till the process in the terminal is done and idk how to cancel it and i cant even see it ne more cuz i restarted my comp.

Try reinstalling the package with ```
sudo apt-get --reinstall *packagename*
``` To "click" on an option in the terminal use Tab to select it and then press Enter.

-Hope this helps :)

---

### Post by ellgor on 2007-08-10
Hi,

If you are still finding that the Java you installed is not working (not displaying applets?) I've found that the j2re1.4 blackdown edition (as listed in synaptic, with all reps enabled) works for me, it self installs, apart from agreeing to the licence, and thats it. A quick tip, if you click on the box with a  s  above the repositries list and start typing, it will bring it straight up for you, hope this is of help.

Regards, Ellgor.

---


---
title: "Mozilla java plugin not working"
date: 2006-05-11
forum: Absolute Beginner Talk
---

### Post by gslater on 2006-05-11
Hi

I am having problems getting java to work on my mozilla browser...it was working a few weeks ago and then I accepted one of the system updates which installed a new version of mozilla...it is only since then that I am having the problems.

When I go to the about:plugin page it appears that java is installed and enabled...what can the problem be?

---

### Post by gslater on 2006-05-11
When I look at my java console it is showing the following errors:

Error: uncaught exception: [Exception... "Component returned failure code: 0x80570009 (NS_ERROR_XPC_BAD_CONVERT_JS) [nsIXPCComponents.lookupMethod]"  nsresult: "0x80570009 (NS_ERROR_XPC_BAD_CONVERT_JS)"  location: "JS frame :: chrome://global/content/XPCNativeWrapper.js :: anonymous :: line 91"  data: no]

Error: wmLaunch is not defined
Source File: javascript:wmLaunch()
Line: 1

....any suggestions?

---

### Post by Kobalt on 2006-05-11
What version of Java did you install at first ? What's the version of your Firefox as well ?

---

### Post by gslater on 2006-05-11
I installed via synaptic...when I look from the terminal it says:

gavin@ubuntuPC:~$ java -version
java version "1.5.0_06"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_06-b05)
Java HotSpot(TM) Client VM (build 1.5.0_06-b05, mixed mode, sharing)

---

### Post by Sef on 2006-05-11
I would reinstall java.  The launcher for it has gone bad.

---

### Post by Kobalt on 2006-05-11
I think my friend Sef is right, try reinstalling Java, it should rock'n'roll well after this... ;)

---

### Post by gslater on 2006-05-11
I have tried this (again usig synaptic...mark for reinstallation) but it still does not work

...also when I look for the package on synaptic it shows as j2re1.4 but when I look for the installed version of java from the terminal is comes back with:

Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_06-b05)
Java HotSpot(TM) Client VM (build 1.5.0_06-b05, mixed mode, sharing)

...does this mean I may have conflicting packages installed?

---

### Post by joshrobinson on 2006-05-11
[QUOTE=gslater]I have tried this (again usig synaptic...mark for reinstallation) but it still does not work

...also when I look for the package on synaptic it shows as j2re1.4 but when I look for the installed version of java from the terminal is comes back with:

Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_06-b05)
Java HotSpot(TM) Client VM (build 1.5.0_06-b05, mixed mode, sharing)

...does this mean I may have conflicting packages installed?[/QUOTE]

id redo your sym links for java and java plugin
where did you isntall the java 1.5.0 to?

did you do 1.5.0 manual install or did that come from synaptic

---

### Post by gslater on 2006-05-11
If I did do a manual install I dont recall doing it....so unfortunately I cannot tell where I would have installed it to.

How to I check the sym links?

---

### Post by joshrobinson on 2006-05-11
[QUOTE=gslater]If I did do a manual install I dont recall doing it....so unfortunately I cannot tell where I would have installed it to.

How to I check the sym links?[/QUOTE]

type 

which java 

into your terminal for me and see what it says

---

### Post by gslater on 2006-05-11
/usr/bin/java

---

### Post by joshrobinson on 2006-05-11
[QUOTE=gslater]/usr/bin/java[/QUOTE]

ok and java -version comes back with 1.5.0_06 correct?

do you use firefox? if so go into /usr/firefox/plugins with nautilus 
do you see libjavaplugin_oji.so? does it have a red X on it?

---

### Post by gslater on 2006-05-11
ok and java -version comes back with 1.5.0_06 correct?.....yes

do you use firefox? if so go into /usr/firefox/plugins with nautilus...dont appear to have nautilus...can I check from command line?

---

### Post by joshrobinson on 2006-05-11
[QUOTE=gslater]ok and java -version comes back with 1.5.0_06 correct?.....yes

do you use firefox? if so go into /usr/firefox/plugins with nautilus...dont appear to have nautilus...can I check from command line?[/QUOTE]

yeah you can check with command line
```
 cd /usr/share/firefox/plugins
then type ls to get a listing 
```

the libjavaplugin_oji.so will appear red if the link is broken

---

### Post by joshrobinson on 2006-05-11
i typed this up just in case you want to reinstall java and start over clean, if you follow this howto by copying and pasteing my commands or typing them in exactally how they are, you should have no problems

download this file
[http://192.18.108.229/ECom/EComTicketServlet/BEGINEBB1413F4B292719EC7F361D35AF1B30/-2147483648/1476494055/1/682154/682058/1476494055/2ts+/westCoastFSEND/jre-1.5.0_06-oth-JPR/jre-1.5.0_06-oth-JPR:20/jre-1_5_0_06-linux-i586.bin](http://192.18.108.229/ECom/EComTicketServlet/BEGINEBB1413F4B292719EC7F361D35AF1B30/-2147483648/1476494055/1/682154/682058/1476494055/2ts+/westCoastFSEND/jre-1.5.0_06-oth-JPR/jre-1.5.0_06-oth-JPR:20/jre-1_5_0_06-linux-i586.bin)

in a terminal type 

```
 sudo nautilus 
```

now in that browser go to /usr  create a folder named java
drag and drop the file you downloaded into that folder and rename it java.bin
close nautilus
in terminal type
```
 cd /usr/java 
```
then
```
 sudo chmod +x java.bin 
```
then
```
 sudo ./java.bin 
```

hit q to get past the terms of use, and type yes to install

in terminal

```
 cd /usr/bin 
sudo mv java java2
sudo ln -s /usr/java/jre1.5.0_06/bin/java

```

now to create a symlink from the java plugin into the firefox plugin directory

```
 cd /usr/share/firefox/plugins 
sudo ln -s /usr/java/jre1.5.0_06/plugin/i386/ns7/libjavaplugin_oji.so
```

restart firefox and give it a try

---

### Post by gslater on 2006-05-11
excellent....will give it a try...thanks!

---

### Post by joshrobinson on 2006-05-11
[QUOTE=gslater]excellent....will give it a try...thanks![/QUOTE]
oh i forgot to add something.. if it says that libjavaplugin_oji.so already exists when you try to do the ln -s command in the firefox plugin folder, just rename the old file with

sudo mv libjavaplugin_oji.so oldfile.so
then do the ln -s command again

sudo ln -s /usr/java/jre1.5.0_06/plugin/i386/ns7/libjavaplugin_oji.so

---


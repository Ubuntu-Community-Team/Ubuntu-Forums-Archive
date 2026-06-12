---
title: "Plugins not installing in Firefox"
date: 2006-06-03
forum: Absolute Beginner Talk
---

### Post by larryni on 2006-06-03
I have been trying to get this to work for the past couple of days, but am not getting anywhere. I simply can't get any plugins working in Firefox whatsoever - flash, java, mplayer ... nothing shows up in about:plugins either. I've tried installing them manually, using Automatix, Easy Ubuntu, nothing works. Most people on here seem to get their plugins installed and then run into problems but I can't even get that far.

Any pointers in the right direction would be greatly appreciated :-?

---

### Post by Rackerz on 2006-06-03
If you've tried installing flash and java see if they work, go to these pages;

Java Test: [http://java.com/en/download/installed.jsp?detect=jre&try=1](http://java.com/en/download/installed.jsp?detect=jre&try=1)
Flash Test: [http://www.adobe.com/shockwave/welcome/](http://www.adobe.com/shockwave/welcome/)

On the Flash Player test site, Shockwave will not work but the flashplayer should.

---

### Post by larryni on 2006-06-03
Nothing shows. 

As I mentioned before, nothing apart from the default plugin libnullplugin.so is showing in about:plugins. I do have java installed, Azureus works. Well, when I say works, then it does so with a few problems. But that's the same problems as other people on here have like the tray icon and notification popups that don't close.

---

### Post by larryni on 2006-06-03
I forgot to mention that I have another problem in Firefox, not sure if it is related. I installed the Foxytunes extension and when I try to select a player it says 'No player modules found. Check installation'.

---

### Post by Rackerz on 2006-06-03
Hmmm very strange. Ok install Java manually doing this;

Java's download page; [http://www.java.com/en/download/manual.jsp](http://www.java.com/en/download/manual.jsp) - Download the 'Linux (self-extracting file)' NOT the RPM.

Then run the following commands from the terminal:
cd to your download directory.
Then First install the required packages:
```
sudo apt-get install fakeroot java-package java-common
```
Create the Deb file for the install:
```
fakeroot make-jpkg jre-1_5_0_07-linux-i586.bin
```
Install The deb file
```
sudo dpkg -i sun-j2re1.5_1.5.0+update07_i386.deb
```
Now make Sun's java the default by running this command and selecting it.
```
sudo update-alternatives --config java
```
Sun's java is usually option '3'. 

Install the flash plug in by putting this into the terminal;
```
sudo apt-get install flashplugin-nonfree
```
If flash still doesn't work after that try this;
```
sudo update-flashplugin
```

Then restart Firefox. Credit goes to Adamal for Java tutorial.

---

### Post by larryni on 2006-06-03
Java seemed to install correctly without any errors, but it still doesn't work in the browser. And still no entry in about:plugins. Also, I now have 5 alternatives for java:

/usr/bin/gij-wrapper-4.1
/usr/lib/jvm/java-gcj/jre/bin/java
/usr/lib/jvm/java-1.5.0-sun/jre/bin/java
/usr/lib/j2se/1.4/bin/java
/usr/lib/j2re1.5-sun/bin/java

Which ones can I get rid off, or should I just leave them?

I tried the same flash instructions before and all I get after 'sudo update-flashplugin' is 'installation failed'.

---

### Post by Rackerz on 2006-06-03
All I can really suggest is a re-install, it's possible when you used Automatix it corrupted something. I don't use automatix anymore, I install all the things it does manually.

---

### Post by darckhart on 2006-06-03
also make sure your plugins/etc are compatible. i just noticed that dapper ships with FF 1.5.0.3, whereas in breezy i was using 1.0.8.

---

### Post by larryni on 2006-06-03
Ugh, I was hoping not to read these words ;)

Oh well, it'll have to wait until tomorrow morning. Maybe someone will come up with an idea until then.

Thanks guys.

---

### Post by marilynks on 2006-06-03
Same problem, sun java installed, but does not work in firefox, saying I need a plugin.

---

### Post by marilynks on 2006-06-03
ah, found in another thread that I just needed to install sun-java5-plugin from synaptic.

---

### Post by larryni on 2006-06-04
I'm just after re-installing Ubuntu and java and flash installed without any problems using the above instructions. Now on to configure the rest of my system :)

---

### Post by aarujnic on 2006-06-04
[QUOTE=larryni]I have been trying to get this to work for the past couple of days, but am not getting anywhere. I simply can't get any plugins working in Firefox whatsoever - flash, java, mplayer ... nothing shows up in about:plugins either. I've tried installing them manually, using Automatix, Easy Ubuntu, nothing works. Most people on here seem to get their plugins installed and then run into problems but I can't even get that far.

Any pointers in the right direction would be greatly appreciated :-?[/QUOTE
try using add/remove in the application menu and install java and flash from there, it worked for me.

---

### Post by _simon_ on 2006-06-04
If you have java installed then all you need to do is make a symbolic link.

```

sudo ln -fs /usr/java/jre1.5.0_07/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib/firefox/plugins/libjavaplugin_oji.so

```

Note the last bit - your firefox directory location may differ.

---


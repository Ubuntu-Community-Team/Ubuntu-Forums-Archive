---
title: "Firefox 2 and Java don't like play nice."
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by thelocust on 2007-05-02
So I installed Firefox 2 and java stopped working I used Automatix2 with no luck and I installed 

java-common
java-package
sun-java6-bin
sun-java6-jre
sun-java6-plugin
j2re1.4-mozilla-plugin


There's something about making a link to some file. Any help is appreciated.

---

### Post by [S|G] on 2007-05-02
You could try this:
```
sudo update-alternatives --config java
```
And then select which java to use

---

### Post by DSn0wMan on 2007-05-02
I am not certain, but java may have an issue with the 1.4 plugin. I don't recall needing j2re1.4-mozilla-plugin. Perhaps everything will work better without it.

---

### Post by jiminycricket on 2007-05-02
What happens when you type 'java --version' into a terminal?

Try 'sudo update-java-alternatives -s java-6-sun' into a teriminal

Also, try uninstalingl j2re1.4-mozilla-plugin

---

### Post by thelocust on 2007-05-03
the j2re1.4-mozilla-plugin was just a last ditch effort it didnt work before then. I tried **[COLOR=Red]sudo update-java-alternatives -s java-6-sun[/COLOR]**[COLOR=Red][COLOR=Black] it did work. it did out put a line 

[/COLOR][/COLOR]```
Using `/usr/lib/jvm/java-6-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so' to provide `firefox-javaplugin.so'.

```I think this might be the file I need to link to from my ~./mozilla/plugins. That folder is currently empty.

I also tried **[COLOR=Red]sudo update-alternatives --config java[/COLOR]**[COLOR=Red][COLOR=Black] it gave me the option to choose from 4 java alternates to choose from

[/COLOR][/COLOR]```
There are 4 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
      1        /usr/bin/gij-wrapper-4.1
      2        /usr/lib/jvm/java-gcj/jre/bin/java
*+    3        /usr/lib/j2se/1.4/bin/java
      4        /usr/lib/jvm/java-6-sun/jre/bin/java
```I tried 3 and 4 with no luck any other ideas or am I missing something?
[COLOR=Red][COLOR=Black]
[/COLOR][/COLOR]

---

### Post by crimesaucer on 2007-05-03
Pressing 4 and enter should be the way to select the newest java version.

You should make sure you have the correct mozilla plugin:

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_J2SE_Runtime_Environment_.28JRE.29_v6.0_with_Plug-in_for_Mozilla_Firefox](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_J2SE_Runtime_Environment_.28JRE.29_v6.0_with_Plug-in_for_Mozilla_Firefox)

---

### Post by thelocust on 2007-05-03
Thats the whole problem how do I install the plugin j2re1.4-mozilla-plugin doesn't work.

---

### Post by thelocust on 2007-05-03
OK so I finally got it to work. I had to put a link in my ~/.mozilla/plugins/ folder to java using this
```

ln -f -s /usr/lib/jvm/java-6-sun-1.6.0.00/jre/plugin/i386/ns7/libjavaplugin_oji.so /home/bob/.mozilla/plugins/javaplugin_oji.so
```So I tested it on a number of sites and all seems good. Thanks for all the inputs.:cool:

---

### Post by stevebakerj on 2007-05-04
> **thelocust said:**
> OK so I finally got it to work. I had to put a link in my ~/.mozilla/plugins/ folder to java using this
```

ln -f -s /usr/lib/jvm/java-6-sun-1.6.0.00/jre/plugin/i386/ns7/libjavaplugin_oji.so /home/bob/.mozilla/plugins/javaplugin_oji.so
```So I tested it on a number of sites and all seems good. Thanks for all the inputs.:cool:

Just installed Fx 2.0.0.4 had the same prob, used the above (changing the relevant bits) now sorted. Thanks:)

---

### Post by Thistleknot on 2007-05-06
Thank you so much!  I've been looking for how to install this for a while, I was reading on making a link but I didn't make it to their, I made it to some /lib folder where firefox was installed.  How would you install something like this for all the users?

---

### Post by piovisqui on 2007-05-07
Thanks everybody. I did not know about that there are Sun's official Java plugin and the Blackdown. I was using blackdown and it was not working -.-. Sun works now :)

---


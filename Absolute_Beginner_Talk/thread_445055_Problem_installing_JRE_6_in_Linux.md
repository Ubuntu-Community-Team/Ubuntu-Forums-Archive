---
title: "Problem installing JRE 6 in Linux"
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by qprfact on 2007-05-15
I want JRE so I can access the bulk uploader in XDrive.

I couldn't find it in Synaptic, but a search on Google recommended this command:

```
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts
```

The following came back in terminal:
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
sun-java6-jre is already the newest version.
sun-java6-jre set to manual installed.
sun-java6-plugin is already the newest version.
sun-java6-plugin set to manual installed.
The following NEW packages will be installed
  sun-java6-fonts
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 1814B of archives.
After unpacking 115kB of additional disk space will be used.
Get: 1 http://gb.archive.ubuntu.com feisty/multiverse sun-java6-fonts 6-00-2ubuntu2 [1814B]
Fetched 1814B in 0s (5673B/s)          
X Error: BadDevice, invalid or uninitialized input device 154
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 154
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Selecting previously deselected package sun-java6-fonts.
(Reading database ... 124417 files and directories currently installed.)
Unpacking sun-java6-fonts (from .../sun-java6-fonts_6-00-2ubuntu2_all.deb) ...
Setting up sun-java6-fonts (6-00-2ubuntu2) ...
No CIDSupplement specified for KochiMincho-Regular, defaulting to 0.
No CIDSupplement specified for Batang-Regular, defaulting to 0.
No CIDSupplement specified for Gulim-Regular, defaulting to 0.
No CIDSupplement specified for KochiMincho-Regular-JaH, defaulting to 0.
No CIDSupplement specified for KochiGothic-Regular, defaulting to 0.
No CIDSupplement specified for Dotum-Regular, defaulting to 0.
No CIDSupplement specified for Headline-Regular, defaulting to 0.
No CIDSupplement specified for KochiGothic-Regular-JaH, defaulting to 0.
```

I thought I'd try java -version, just in case (though it looked doubtful) - I got this message back:

```
Exception in thread "main" java.lang.NoClassDefFoundError: =version
```

Can anyone help with next steps please?!!

Thanks!

---

### Post by taurus on 2007-05-15
Which release are you running?

---

### Post by Happy_Man on 2007-05-15
uh, the code for version is ```
java -version
```
not ```
java =version
```

---

### Post by Detonate on 2007-05-15
You also need to set the sun java as the default by 
```

sudo update-alternatives --config java
```

and select the sun java.

---

### Post by zvacet on 2007-05-15
**synaptic>search box** type** sun**

---

### Post by qprfact on 2007-05-15
Answering the questions:

7.04 Feisty
Yes, did inadvertently type =version!

On typing ```
sudo update-alternatives --config java
```  I get 
```
There are 5 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/lib/jvm/java-1.5.0-sun/jre/bin/java
*+        2    /usr/lib/j2se/1.4/bin/java
          3    /usr/bin/gij-wrapper-4.1
          4    /usr/lib/jvm/java-gcj/jre/bin/java
          5    /usr/lib/jvm/java-6-sun/jre/bin/java

Press enter to keep the default[*], or type selection number: 
```

Which do I want?

In Synaptic, what package do I choose after searching for Sun? There's a pretty long list!

Thanks in advance!

---

### Post by chamberlain2006 on 2007-05-15
#5 is the 1.6 version

---

### Post by qprfact on 2007-05-15
java -version now says:

```
java version "1.6.0"
Java(TM) SE Runtime Environment (build 1.6.0-b105)
Java HotSpot(TM) Client VM (build 1.6.0-b105, mixed mode, sharing)
```

But XDrive still keeps saying I need to install Java! What have I missed out?

(And, BTW, how did you get your Hauppauge TV card working?!!)

---

### Post by chamberlain2006 on 2007-05-15
The WinTV-Go-Plus was simple.  It auto-loaded the Bt878 Video/Audio drivers, so I just had to install the tvtime application.  It works great. 

Now, about Java.  It's loaded correctly, judging by your java -version.  Maybe try rebooting.  Also, what is the exact output from XDrive?

---

### Post by qprfact on 2007-05-16
I did wonder about rebooting (I've restarted browser - thinking about it, there's nothing I need to do in Firefox itself is there?)

What is tvtime?

---

### Post by jessecollins on 2007-05-16
> **Detonate said:**
> You also need to set the sun java as the default by 
```

sudo update-alternatives --config java
```

and select the sun java.

Detonate:

Thanks for this info.  Fixed my problem.

Cheers

---

### Post by esoterica on 2007-05-16
You may want to revert back to running the JRE 5 instead, the JRE 6 seems very buggy in both Windows and Linux and no one at Sun seems to be in any hurry to fix the problems. I actually use the JDK, the compiler and everything seems to work great, but I and other people have nothing but problems when ever you fire up the JRE portion. Have to reboot the computer every time it fires up or things begin to absolutely crawl, lock up, not run and a host of other issues, all of which only happen when the JRE 6 had been started up. I'm on powerful new systems as well, so it isn't just a system resource issue.

Other people have reported the same issues as well.

---

### Post by Detonate on 2007-05-16
I have not had any problems with JRE 6, but I do know that some web sites that require JRE, may require a specific version.  I remember I was recently trying to sign in to a VPN that would not let me in until I identified the problem as that particular site wanted a specific version.  So it may be worthwhile to try different versions using the update alternatives and see if that gets you into the XDrive (whatever that is).

---

### Post by fastpakr on 2007-05-17
I'm having the same problem as the OP.  Had no problems installing the latest 64 bit JRE from Sun (I'm on 64 bit 7.04 Ubuntu).  However, I regularly run into sites that indicate I need to install the JRE.  Running java -version shows:
java version "1.6.0"
Java(TM) SE Runtime Environment (build 1.6.0-b105)
Java HotSpot(TM) Client VM (build 1.6.0-b105, mixed mode, sharing)


[Here](http://www.wastelandwar.com/irc/chat.html)'s an example of a page I can't load.

---

### Post by esoterica on 2007-05-17
I've gotten so frustrated with Java 6 that I just resorted all the way back to java version "1.4.2-02" and finally found something moderately stable for Linux. The page in your link works fine for me, and I haven't had any problems getting pages or apps to work with this old of a version. Newer is not always better, you'll find stable is better than newer and shiny sometimes.

On Vista I've fallen back to java 5, which isn't even supposed to be for Vista, yet it runs better in Vista than Java 6 which is supposed to be for Vista does. I just finished a semester of Java programming in school, and even in school we all used Java 5 because 6 is so full of problems.

Java 6 just came out, so I seriously doubt your going to have apps that exclusively require it already, especially since very few java developers have embraced it with open arms yet and most are doing as I have done and going back to the older version for system stability and better compatibility.

---

### Post by jiminycricket on 2007-05-17
> **fastpakr said:**
> I'm having the same problem as the OP.  Had no problems installing the latest 64 bit JRE from Sun (I'm on 64 bit 7.04 Ubuntu).  However, I regularly run into sites that indicate I need to install the JRE.  Running java -version shows:
java version "1.6.0"
Java(TM) SE Runtime Environment (build 1.6.0-b105)
Java HotSpot(TM) Client VM (build 1.6.0-b105, mixed mode, sharing)


[Here](http://www.wastelandwar.com/irc/chat.html)'s an example of a page I can't load.


Can you load the java applet [test ]("http://www.java.com/en/download/help/testvm.xml")site?

Is java listed anywhere in ```
about:plugins
```? ( which you should type into Firefox's address bar)

What is the output on ```
ls -l /usr/lib/firefox/plugins/
```

Are you using a different browser than Firefox?  There might be a 64 bit issue here because I didn't know Sun had a 64 bit plugin; I thought nspluginwrapper or a 32-bit Firefox was the only way to accomplish that.

---

### Post by qprfact on 2007-05-17
Hmm! A few things to ponder over there!

XDrive helpfully gives no error messages, other than saying I need to go to Java and download!

---

### Post by Detonate on 2007-05-17
I have no problems at all running the web site above, or the Java test site with JRE 6.  I am running 32 bit Kubuntu on a 64 bit machine.  Are all of you having these problems running 32 or 64?

---

### Post by fastpakr on 2007-05-17
> **jiminycricket said:**
> Can you load the java applet [test ]("http://www.java.com/en/download/help/testvm.xml")site?
No, on the test site it indicates I need to install the plugin.

> Is java listed anywhere in ```
about:plugins
```? ( which you should type into Firefox's address bar)
No, for some reason it doesn't appear to have been added to the plugins list.

> What is the output on ```
ls -l /usr/lib/firefox/plugins/
```
total 6904
-r--r--r-- 1 root root     856 2007-04-24 00:46 flashplayer.xpt
-rwxr-xr-x 1 root root 7040080 2007-04-24 00:47 libflashplayer.so
lrwxrwxrwx 1 root root      36 2007-04-23 18:42 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so
lrwxrwxrwx 1 root root      37 2007-04-23 18:42 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt
lrwxrwxrwx 1 root root      34 2007-04-23 18:42 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so
lrwxrwxrwx 1 root root      35 2007-04-23 18:42 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt
lrwxrwxrwx 1 root root      36 2007-04-23 18:42 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so
lrwxrwxrwx 1 root root      37 2007-04-23 18:42 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt
lrwxrwxrwx 1 root root      42 2007-04-23 18:42 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 root root      43 2007-04-23 18:42 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt
-rw-r--r-- 1 root root   11072 2007-04-03 11:30 libunixprintplugin.so


> Are you using a different browser than Firefox?  There might be a 64 bit issue here because I didn't know Sun had a 64 bit plugin; I thought nspluginwrapper or a 32-bit Firefox was the only way to accomplish that.
I'm running FIrefox 2.0.0.3.

---

### Post by Detonate on 2007-05-17
You don't have the plugin installed.  The plugin is found at:

/usr/lib/jvm/java-6-sun-1.6.0.00/jre/plugin/i386/ns7/libjavaplugin_oji.so

Merely copy that file to /usr/lib/firefox/plugins and see what happens.  (Restart firefox).

---

### Post by fastpakr on 2007-05-17
I didn't have a plugin folder under /usr/lib/jvm/java-6-sun-1.6.0.00/jre/, so I did a search and found it under /usr/java/jre1.6.0_01/plugin/i386/ns7, which I copied to /usr/lib/firefox/plugins as you suggested.  However, I still don't see it in about:plugins after a Firefox restart.  Any ideas?  Thanks for the help so far.  Why wouldn't the JRE install process put the plugin in the folder as part of the installation?

---

### Post by Detonate on 2007-05-17
Because you did not use the package manager to install.  Open Synaptic, search for "sun", select the sun-java6-jre and the sun-java6-plugin and install them that way.  Whenever a package is available in the repositories it's always better to install them from there.  This will automatically install the java6 plugin in your mozilla applications plugins.

But I don't think it will work in the 64 bit system.  That and flash are the main reasons I'm running the 32 bit system.

---

### Post by fastpakr on 2007-05-17
sun-java6-jre indicates that it's already installed in package manager.  I don't see sun-java6-plugin on the list at all?

---

### Post by Detonate on 2007-05-17
Probably doesn't list it, because you are on 64 Bit.  You might take this problem over to the 64 bit section of the forum and see if anyone over there has a solution.  I'm not running 64 bit and have no experience with it.

---

### Post by qprfact on 2007-05-19
I'm running Firefox 2.0.0.3.

Typing```
 ls -l /usr/lib/firefox/plugins/
``` gives:

```
total 12
lrwxrwxrwx 1 root root   41 2007-04-21 13:52 flashplayer.xpt -> ../../flashplugin-nonfree/flashplayer.xpt
lrwxrwxrwx 1 root root   43 2007-04-21 13:52 libflashplayer.so -> ../../flashplugin-nonfree/libflashplayer.so
lrwxrwxrwx 1 root root   54 2007-03-10 21:52 libjavaplugin_oji.so -> /etc/alternatives/libjavaplugin_oji_mozilla_firefox.so
lrwxrwxrwx 1 root root   39 2007-04-20 07:01 libjavaplugin.so -> /etc/alternatives/firefox-javaplugin.so
lrwxrwxrwx 1 root root   36 2007-04-19 23:19 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so
lrwxrwxrwx 1 root root   37 2007-04-19 23:19 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt
lrwxrwxrwx 1 root root   34 2007-04-19 23:19 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so
lrwxrwxrwx 1 root root   35 2007-04-19 23:19 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt
lrwxrwxrwx 1 root root   36 2007-04-19 23:19 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so
lrwxrwxrwx 1 root root   37 2007-04-19 23:19 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt
lrwxrwxrwx 1 root root   42 2007-04-19 23:19 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 root root   43 2007-04-19 23:19 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt
-rw-r--r-- 1 root root 8936 2007-04-03 16:44 libunixprintplugin.so
lrwxrwxrwx 1 root root   37 2007-04-21 12:42 libvlcplugin.so -> ../../mozilla/plugins/libvlcplugin.so
lrwxrwxrwx 1 root root   35 2007-04-21 18:02 mozplugger.so -> ../../mozilla/plugins/mozplugger.so
lrwxrwxrwx 1 root root   42 2007-04-19 23:17 mplayerplug-in-qt.so -> ../../mozilla/plugins/mplayerplug-in-qt.so
lrwxrwxrwx 1 root root   43 2007-04-19 23:17 mplayerplug-in-qt.xpt -> ../../mozilla/plugins/mplayerplug-in-qt.xpt
lrwxrwxrwx 1 root root   42 2007-04-19 23:17 mplayerplug-in-rm.so -> ../../mozilla/plugins/mplayerplug-in-rm.so
lrwxrwxrwx 1 root root   43 2007-04-19 23:17 mplayerplug-in-rm.xpt -> ../../mozilla/plugins/mplayerplug-in-rm.xpt
lrwxrwxrwx 1 root root   39 2007-04-19 23:17 mplayerplug-in.so -> ../../mozilla/plugins/mplayerplug-in.so
lrwxrwxrwx 1 root root   43 2007-04-19 23:17 mplayerplug-in-wmp.so -> ../../mozilla/plugins/mplayerplug-in-wmp.so
lrwxrwxrwx 1 root root   44 2007-04-19 23:17 mplayerplug-in-wmp.xpt -> ../../mozilla/plugins/mplayerplug-in-wmp.xpt
lrwxrwxrwx 1 root root   40 2007-04-19 23:17 mplayerplug-in.xpt -> ../../mozilla/plugins/mplayerplug-in.xpt
```

As an earlier poster suggested reverting to an earlier version of Java, I tried that, so About Plugins says:

> Java(TM) Plug-in Blackdown-1.4.2-02

    File name: libjavaplugin_oji.so
    Blackdown Java-Linux Java(TM) Plug-in 1.4.2

MIME Type 	Description 	Suffixes 	Enabled
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
application/x-java-applet;jpi-version=1.4.2 	Java 		Yes
application/x-java-applet;jpi-version=1.4.2_01 	Java 		Yes
application/x-java-applet;jpi-version=1.4.2_02 	Java 		Yes
application/x-java-applet;jpi-version=1.4.2_03 	Java 		Yes
application/x-java-applet;jpi-version=1.4.2_04 	Java 		Yes
application/x-java-applet;jpi-version=1.4.2_05 	Java 		Yes
application/x-java-applet;jpi-version=1.4.2_06 	Java 		Yes
application/x-java-applet;jpi-version=1.4.2_07 	Java 		Yes
application/x-java-applet;jpi-version=1.4.2_08 	Java 		Yes
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
application/x-java-bean;jpi-version=1.4.2 	Java 		Yes
application/x-java-bean;jpi-version=1.4.2_01 	Java 		Yes
application/x-java-bean;jpi-version=1.4.2_02 	Java 		Yes
application/x-java-bean;jpi-version=1.4.2_03 	Java 		Yes
application/x-java-bean;jpi-version=1.4.2_04 	Java 		Yes
application/x-java-bean;jpi-version=1.4.2_05 	Java 		Yes
application/x-java-bean;jpi-version=1.4.2_06 	Java 		Yes
application/x-java-bean;jpi-version=1.4.2_07 	Java 		Yes
application/x-java-bean;jpi-version=1.4.2_08 	Java 		Yes

Not sure what to do now, as XDrive still refusing to work!!! As my PC is pretty old, I don't think it's 64 bit

---

### Post by qprfact on 2007-05-19
Take pity on me as I'm a lowly sort and get confused enough about Java in Windows, let alone in Linux. But, I don't know if or how much this is relevant, but in Applications / Internet, I have three Java related entries:

Java Web Start 1.4
Sun Java 5.0 Web Start
Sun Java 6 Web Start

In System / Preferences I have:

Java Plugin Control Panel (1.4)
Java Policy Tool (1.4)
Sun Java 5.0 Plugin Control Panel 
Sun Java 5.0 Policy Tool 
Sun Java 6 Plugin Control Panel 
Sun Java 6 Policy Tool 

Do I have too many versions of Java installed? What is my best way to clean them up?!!

Thanks!

---

### Post by Detonate on 2007-05-19
I don't know what to tell you, everything looked OK.  The Java plugin is there.  Did you go to the java test site?

[http://www.java.com/en/download/help/testvm.xml](http://www.java.com/en/download/help/testvm.xml)

---

### Post by qprfact on 2007-05-22
I'll try that. I'm coming to the conclusion that it's XDrive related rather than Java though!

---

### Post by Alcibiades Mystery on 2007-06-28
> **qprfact said:**
> I'll try that. I'm coming to the conclusion that it's XDrive related rather than Java though!

Do you have firefox installed in opt/firefox rather than in /usr?

---

### Post by qprfact on 2007-06-30
No, I used Firefox as installed by Ubuntu anyway, but it's not in opt

---


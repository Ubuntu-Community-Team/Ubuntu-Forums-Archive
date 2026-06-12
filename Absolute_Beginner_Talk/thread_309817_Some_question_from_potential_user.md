---
title: "Some question from potential user"
date: 2006-11-30
forum: Absolute Beginner Talk
---

### Post by x4444 on 2006-11-30
Hello
I'm planing to install Ubuntu desktop edition on my pc.
I want to ask some question about the distro.

1. Does it plays mp3, mpeg4, divx, dvd from the box or is it simple to install additional packages to provide this functionality? 
2. It will be great if totem browser plugin plays divx video in the web browser.
3. Does it have flash plugin for firefox?
4. Does it have jdk 1.5 or is it simple to install it?

Thank you

---

### Post by an.echte.trilingue on 2006-11-30
If you read one document, all of your questions will be answered.

[Restricted Formats]("https://help.ubuntu.com/community/RestrictedFormats")

It is pretty easy.  There also exist some automation tools to do this for you, such as automatix, but I don't recommend them, personally.

Take care,
-mat

---

### Post by feest on 2006-11-30
> **x4444 said:**
> Hello
I'm planing to install Ubuntu desktop edition on my pc.
I want to ask some question about the distro.

1. Does it plays mp3, mpeg4, divx, dvd from the box or is it simple to install additional packages to provide this functionality? 
2. It will be great if totem browser plugin plays divx video in the web browser.
3. Does it have flash plugin for firefox?
4. Does it have jdk 1.5 or is it simple to install it?

Thank you

mp3 can easily be playerd with xmms (apt-get install xmms) the others can easily be installed with an app called (automatix [www.getautomatix.com](www.getautomatix.com)) the flash plugin can be found on google (search for "flashplayer 9 linux beta" or something). jdk can also be installed with automatix i think

---

### Post by xyz on 2006-11-30
and/or:
[Automatix]("http://www.getautomatix.com")
...if Restricted Formats causes you hassles being a new user.
And Welcome to Ubuntu!!!

---

### Post by daniminas on 2006-11-30
To play the MP3, etc i totem:

> gstreamer0.10-plugins-bad 
> gstreamer0.10-plugins-bad-multiverse 
> gstreamer0.10-plugins-ugly 
> gstreamer0.10-plugins-ugly-multiverse 
> gstreamer0.10-ffmpeg 
> gstreamer0.10-pitfdll

(i like the xmms too :))

-------------------------------------------------------------
No problem with dvds

-------------------------------------------------------------
to install flash plugin in Firefox 1.5(Breezy 5.10 y Dapper 6.06)..

> flashplugin-nonfree

to firefox 2.0 (Edgy): 

Download the Flash player 9 from here: [http://www.ubuntu.org.ve/www.adobe.com/go/fp9_update_b1_installer_linuxplugin](http://www.ubuntu.org.ve/www.adobe.com/go/fp9_update_b1_installer_linuxplugin)

Uncompressit:
And like root copy the folder to:  /usr/lib/firefox/plugins

---------------------------------------------------------------------
Java:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Java_Development_Kit_.28JDK.29_v5.0](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Java_Development_Kit_.28JDK.29_v5.0) (with automatix)

---

### Post by daniminas on 2006-11-30
Other installation of the JDK ( this is my dump.. =) ):

**> sudo apt-get install java-package**
**> sudo apt-get install fakeroot**

Download the java from:
[https://sdlc3b.sun.com/ECom/EComActionServlet;jsessionid=2DDBD27B48832335755C8B71F7E6E24A](https://sdlc3b.sun.com/ECom/EComActionServlet;jsessionid=2DDBD27B48832335755C8B71F7E6E24A)


[B]> fakeroot make-jpkg jdk-1_5_0_09-linux-i586.bin
> sudo dpkg -i sun-j2sdk1.5_1.5.0+update09_i386.deb
> sudo update-alternatives --config java[/B]

And it will show somethig like this:

[I]Selection Alternative
-----------------------------------------------
1 /usr/bin/gij-wrapper-4.1
+ 2 /usr/lib/jvm/java-gcj/jre/bin/java
3 /usr/lib/jvm/java-1.5.0-sun/jre/bin/java
* 4 /usr/lib/j2re1.5-sun/bin/java
5 /usr/lib/j2sdk1.5-sun/bin/java

Press enter to keep the default[*], or type selection number: 5[/I]

*/usr/lib/j2sdk1.5-sun/bin/java*

And if it ok:

**> java -version**
[I]java version "1.5.0_09"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_09-b01)
Java HotSpot(TM) Client VM (build 1.5.0_09-b01, mixed mode, sharing)[/I]

To end the configuration:
**> sudo update-alternatives --config jar**

[I]Selection Alternative
-----------------------------------------------
1 /usr/bin/fastjar
+ 2 /usr/lib/jvm/java-gcj/jre/bin/jar
* 3 /usr/lib/jvm/java-1.5.0-sun/bin/jar
4 /usr/lib/j2sdk1.5-sun/bin/jar

Press enter to keep the default[*], or type selection number: 4
Using `/usr/lib/j2sdk1.5-sun/bin/jar' to provide `jar'.[/I]

**> sudo update-alternatives --config javac**

[I]There are 2 alternatives which provide `javac'.

Selection Alternative
-----------------------------------------------
* 1 /usr/lib/jvm/java-1.5.0-sun/bin/javac
+ 2 /usr/lib/j2sdk1.5-sun/bin/javac

Press enter to keep the default[*], or type selection number: 2
Using `/usr/lib/j2sdk1.5-sun/bin/javac' to provide `javac'.[/I]

**> sudo update-alternatives --config javadoc**

[I]There are 2 alternatives which provide `javadoc'.

Selection Alternative
-----------------------------------------------
* 1 /usr/lib/jvm/java-1.5.0-sun/bin/javadoc
+ 2 /usr/lib/j2sdk1.5-sun/bin/javadoc

Press enter to keep the default[*], or type selection number: 2
Using `/usr/lib/j2sdk1.5-sun/bin/javadoc' to provide `javadoc'.[/I]

**> sudo update-alternatives --config javah**

[I]There are 2 alternatives which provide `javah'.

Selection Alternative
-----------------------------------------------
* 1 /usr/lib/jvm/java-1.5.0-sun/bin/javah
+ 2 /usr/lib/j2sdk1.5-sun/bin/javah

Press enter to keep the default[*], or type selection number: 2
Using `/usr/lib/j2sdk1.5-sun/bin/javah' to provide `javah'.[/I]

**> sudo update-alternatives --config javap**

[I]There are 2 alternatives which provide `javap'.

Selection Alternative
-----------------------------------------------
* 1 /usr/lib/jvm/java-1.5.0-sun/bin/javap
+ 2 /usr/lib/j2sdk1.5-sun/bin/javap

Press enter to keep the default[*], or type selection number: 2
Using `/usr/lib/j2sdk1.5-sun/bin/javap' to provide `javap'.[/I]

**> sudo update-alternatives --config javaws**

[I]There are 3 alternatives which provide `javaws'.

Selection Alternative
-----------------------------------------------
1 /usr/lib/jvm/java-1.5.0-sun/jre/bin/javaws
*+ 2 /usr/lib/j2re1.5-sun/bin/javaws
3 /usr/lib/j2sdk1.5-sun/bin/javaws

Press enter to keep the default[*], or type selection number: 3
Using `/usr/lib/j2sdk1.5-sun/bin/javaws' to provide `javaws'.[/I]

---

### Post by x4444 on 2006-11-30
Is it possible that totem browser plugin (or other video player plugin) plays mpg and avi video in the web browser?

What I need? Just install additional gstreamer codecs you mentioned above?

---

### Post by xyz on 2006-11-30
If you type  "about:plugins" in Firefox, do you see:
> browser plugin (or other video player plugin) plays mpg and avi video in the web browser
If not, you need to get them!

---

### Post by daniminas on 2006-11-30
This is what i do in Ubuntu Breezy:

> sudo apt-get install mozilla-mplayer

> sudo apt-get install totem-xine totem-xine-firefox-plugin
o

> sudo apt-get install totem-gstreamer totem-gstreamer-firefox-plugin

Because mozzilla need to read again the plugins:

> cd /home/daniel/.mozilla/firefox/

> rm pluginreg.dat



This thread: :)

[http://ubuntuforums.org/showthread.php?t=138889&highlight=multimedia+y%27all](http://ubuntuforums.org/showthread.php?t=138889&highlight=multimedia+y%27all)

---

### Post by b1g4L on 2006-11-30
The "Starter Guide" is an excellent place to learn how to get exactly what you need.

[http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)


edit: whoops, just noticed daniminas had already given you this as a reference.

---


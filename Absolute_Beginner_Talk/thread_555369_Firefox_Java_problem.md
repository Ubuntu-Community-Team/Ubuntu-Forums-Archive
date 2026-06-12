---
title: "Firefox Java problem"
date: 2007-09-20
forum: Absolute Beginner Talk
---

### Post by berZirker on 2007-09-20
One more person with Java issues.  This started by trying to access this site: [http://linuxsurvival.com/](http://linuxsurvival.com/) to learn a bit more about the command line.  I can read the text, but the interactive (java) part is missing.  Java.com tells me: "Oops! You don't have the recommended Java installed. Your Java version is 1.6.0. Please click the button below to get the recommended Java for your computer."  I have tried about every solution that seemed even remotely possible, including downloading and installing the .bin file from [http://www.java.com/en/download/linux_manual.jsp?locale=en&host=www.java.com:80](http://www.java.com/en/download/linux_manual.jsp?locale=en&host=www.java.com:80)
The java -version command outputs:
java version "1.6.0"
Java (TM) SE Runtime Environment (build 1.6.0-b105)
Java HotSpot(TM) Client VM (build 1.6.0-b105, mixed mode, sharing)

I hate for this to be a re-hash of a problem already solved, but like I said, I tried everything I found.  I am admittedly new to linux/ubuntu so I'm hoping this is some easy fix that I have looked over.  Thanks in advance

---

### Post by alienexplorers on 2007-09-20
Did you reboot after installing java?

---

### Post by yabbadabbadont on 2007-09-20
They are probably wanting version 1.4 or 1.5 to be installed, but don't know enough about webpage design to be able to figure out that 1.6 will work.  :lol:

---

### Post by alienexplorers on 2007-09-20
Do you mean that a site may be running a older version of java and because you are running the most current your out of luck.  They should have rules for all websites to make sure all are compatible with jave, flash, ect...

---

### Post by yabbadabbadont on 2007-09-20
> **alienexplorers said:**
> Do you mean that a site may be running a older version of java and because you are running the most current your out of luck.  They should have rules for all websites to make sure all are compatible with jave, flash, ect...

I meant that the webpage was probably coded to only check for specific versions, such as 1.4 or 1.5, and it displays an error if it doesn't find any of those versions.  (even if it would work with a newer one)

---

### Post by alienexplorers on 2007-09-20
I was never aware of that.

---

### Post by rsambuca on 2007-09-20
Strange.  It seems to work on my rig and I am running 1.6.  Do you have the Firefox plugin installed?

---

### Post by yabbadabbadont on 2007-09-20
> **rsambuca said:**
> Strange.  It seems to work on my rig and I am running 1.6.  Do you have the Firefox plugin installed?

I agree.  I looked at the webpage source and it doesn't seem to check for anything.  Check the about:plugins page in Firefox and make sure that Java is listed.

---

### Post by berZirker on 2007-09-20
I followed the "enable and configure" steps on the java website which are as follows:
 Mozilla 1.4 and later

   1. Go to the plugins sub-directory under the Mozilla installation directory
      cd <Mozilla installation directory>/plugins
   2. In the current directory, create a symbolic link to the JRE ns7/libjavaplugin_oji.so file Type:
      ln -s <JRE installation directory>/plugin/i386/ns7/libjavaplugin_oji.so

      Example:
          * If Mozilla is installed in this directory:
            /usr/lib/mozilla-1.4/
          * and if the JRE is installed at this directory:
            /usr/java/jre1.5.0
          * Then type at the terminal to go to the browser plug-in directory:
            cd /usr/lib/mozilla-1.4/plugins
          * Enter the following command to create a symbolic link to the Java Plug-in for the Mozilla browser.
            ln -s /usr/java/jre1.5.0/plugin/i386/ns7
            /libjavaplugin_oji.so .
   3. Start Mozilla browser or restart it if it is already running. Note that if you have other Mozilla components (ie: Messenger, Composer, etc) running, you will need to restart them as well.
   4. Go to Edit > Preferences. Under Advanced category > Select Enable Java

I was under the impression that that should have taken care of the Firefox plugin.
(My directories are a little different btw.  The instructions were configured for Red Hat, but I'm pretty sure I adapted it correctly for Ubuntu/my system... yet one more possible weak link)

---

### Post by berZirker on 2007-09-20
Oh boy are the java plugins ever enabled:

Java(TM) Plug-in 1.6.0-b105

    File name: libjavaplugin_oji.so
    Java(TM) Plug-in 1.6.0

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
application/x-java-applet;version=1.5 	Java 		Yes
application/x-java-applet;version=1.6 	Java 		Yes
application/x-java-applet;jpi-version=1.6 	Java 		Yes
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
application/x-java-bean;jpi-version=1.6 	Java 		Yes

...sorry for the formatting, issues, but you get the idea.

---

### Post by alienexplorers on 2007-09-20
In firefox under Edit>Preferences>Content do you have enable java and javascript checked.

---

### Post by berZirker on 2007-09-20
Yup, both.  Is there a more recent version than 1.6.0?  Is there another reason that the java website would be telling me that 1.6.0 is not the recommended version?

---

### Post by alienexplorers on 2007-09-20
Java is Version 6 Update 2
> [http://www.java.com/en/download/installed.jsp](http://www.java.com/en/download/installed.jsp)

Test your java here:
> [http://www.java.com/en/download/help/testvm.xml](http://www.java.com/en/download/help/testvm.xml)

---

### Post by berZirker on 2007-09-20
When I test it, I can see the animation.  When I do the verification it says Oops, you don't have the recommended java installed... I'm baffled

---

### Post by alienexplorers on 2007-09-20
Mine is the same way.  I have Version 6 Update 1.

---

### Post by rsambuca on 2007-09-20
I would definitely uninstall all of the old java versions from 1.1 up to 1.5.

---

### Post by berZirker on 2007-09-20
We have reached the limit of my limited 1337 H4X0R skills.  (Bass, snare, crash)  I can't find versions 1-4 to delete them...?  Is there a way to wipe java clean and then simply install 1.6?  I have a feeling the answer is no, so what are my other options and how do I go about it?

---

### Post by rsambuca on 2007-09-20
It depends on how you installed them.  If you used the repos, you can just use Synaptic Package Manager.

---

### Post by berZirker on 2007-09-20
The only one I have tried to install was 1.6 so I don't know how the other ones got there.  I guess I would have to undo it from the command line, but i dont know where to start... Doh

---

### Post by berZirker on 2007-09-20
Can anyone tell me how to uninstall a whole slew of java versions?

---

### Post by FuturePilot on 2007-09-20
Just search in Synaptic for sun-java and uninstall all the old ones.

---

### Post by berZirker on 2007-09-21
Synaptic only sees java 5 and 6.  Whats...going on?

---

### Post by rsambuca on 2007-09-21
Synaptic is only a front-end for 'apt', so it will only have things listed that you installed via a .deb package.  If you compiled them or used some binary installer, it may not be listed.  You might just try a complete removal of java6, and then re-install it to see if that version works.

---

### Post by berZirker on 2007-09-21
output of sudo apt-get remove sun-java6-plugin:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  flashplugin-nonfree
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  sun-java6-plugin
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking, 73.7kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 155615 files and directories currently installed.)
Removing sun-java6-plugin ...
dpkg - warning: while removing sun-java6-plugin, directory `/usr/lib/iceape/plugins' not empty so not removed.
dpkg - warning: while removing sun-java6-plugin, directory `/usr/lib/iceape' not empty so not removed.
dpkg - warning: while removing sun-java6-plugin, directory `/usr/lib/iceweasel/plugins' not empty so not removed.
dpkg - warning: while removing sun-java6-plugin, directory `/usr/lib/iceweasel' not empty so not removed.

Why does a directory have to be empty before you can delete it?  Does nautilus not like deleting files inside a directory?  Is it even Nautilus?

---

### Post by luvr on 2008-05-25
I installed **sun-java6-plugin,** which works--I can successfully [Test my Java Virtual Machine]("http://www.java.com/en/download/installed.jsp"), which is correctly identified as *Java 6 Update 6.*

**However,** when I go to the [Java Plug-in 1.4.1 Demo Page]("http://java.sun.com/products/plugin/1.4.1/demos/plugin/applets.html"), and I try to run any of the applets from the page, I get a message stating that *"Additional plugins are required to display all the media on this page,"* and I'm invited to *"Install Missing Plugins..."*--but when I try that, I'm told that **"No suitable plugins were found."**

[FONT="Arial"][SIZE="7"][COLOR="Sienna"]**I have identified the problem**:[/COLOR][/SIZE][/FONT]

The pages that contain these applets, all specify a type of ***"application/x-java-applet;jpi-version=1.4.1"***. When you take a look at the *"about:****plugins"* page, however, the only *"jpi-version"* that the plugin will run, is **"1.6.0_06"**.

I remember having encountered this very same problem with an earlier Java plugin version under an earlier Ubuntu release. What's more, I even **solved** it back then. The solution was, simply, to add the required *"jpi-version"* definitions to some plain-text file. Trouble is, I cannot for the life of me, remember **WHERE THAT :evil: FILE SITS, AND I CANNOT SEEM TO FIND IT THIS TIME AROUND!** :mad: :confused: :evil:

Anyway, if *you* also run into this problem: **No need to uninstall, reinstall, test, re-test, re-re-test, whatever!** It should be a simple matter of editing the appropriate file; the issue, now, is **FINDING** the file.

By the way: The **real** problem, in my opinion, is with the web pages involved--I believe that they should really specify a **"version"** instead of a *"jpi-version."*

---

### Post by luvr on 2008-05-26
[CENTER][FONT="Arial"][SIZE="7"][COLOR="Sienna"]**AHA! FOUND IT!**[/COLOR][/SIZE][/FONT][/CENTER]

***First, let me recapitulate the problem:***
[LIST]
[*]I installed the **sun-java6-plugin** and I am running it from the Firefox browser.
[*]I can successfully [test my Java Virtual Machine]("http://www.java.com/en/download/installed.jsp")--that tells me that I am running *Java 6 Update 6.*
That's a fairly reliable indication that the Java plugin is correctly installed, and that it is working fine.
[*]The applets from the [Java Plug-in 1.4.1 Demo Page]("http://java.sun.com/products/plugin/1.4.1/demos/plugin/applets.html"), however, do **NOT** work--when I try them, I get a message that *"Additional plugins are required to display all the media on this page."* When I subsequently attempt to install the required plugins, no suitable plugins can be found.
[/LIST]
***My Diagnosis:***
[LIST]
[*]When I view the source of any of the demo applet pages (*"View"* -> *"Page Source"* in Firefox)--e.g., [A Clock]("http://java.sun.com/products/plugin/1.4.1/demos/plugin/applets/Clock/example1.html")--I notice that it specifies the following type for the content that it attempts to display:
```
"application/x-java-applet;jpi-version=1.4.1"
```
[*]When I watch the list of installed plugins--i.e., the [FONT="Courier New"]about:****plugins[/FONT] page in Firefox--I find the following entry for a Java applet:
```
"application/x-java-applet;jpi-version=1.6.0_06"
```
Thus, the Java plugin supports Java applets with a *"jpi-version"* of **1.6.0_06--*not* 1.4.1.**
[/LIST]
For more information on the *"jpi-version"* and *"version"* attributes as they apply to the Java plugin, cfr. [Encountering[FONT="Courier New"] OBJECT, EMBED, [/FONT]and[FONT="Courier New"] APPLET [/FONT]Tags With Different Plug-in Versions and Browsers]("http://java.sun.com/products/plugin/versions.html"); as explained on that page, *"jpi-version"* forces **static** versioning (i.e., it requires *exactly* the specified version of the Java plugin on the client computer), while *"version"* supports **dynamic** versioning (i.e., it requests *at least* the specified version of the Java plugin on the client computer).

***My Workaround:***

To support Java applets with a *"jpi-version=1.4.1"* attribute, I **could,** obviously, try and install version 1.4.1 of the Java plugin, next to the existing version. However, that would be overkill, since I already have a Java plugin that should flawlessly support Java 1.4.1 applets. *(Furthermore, the Java plugin 1.4.1 is not available as a standard package in any of the common Ubuntu repositories.)*

As an alternative, I discovered that there exists a way to add support for specific *"jpi-version"* attribute values to the Java plugin. The secret lies hidden in a file named **"pluginreg.dat"**--which is located somewhere in the *".mozilla"* subdirectory tree of my home directory.

[COLOR="Red"]**IMPORTANT: The following procedure is not officially supported. Use at your own risk. I applied it to my system, and I don't experience any problems with it, but your mileage may vary.**[/COLOR]

To add support for *"jpi-version=1.4.1"* applets to a Java 6 (or Java 5) plugin, follow these steps:
[LIST]
[*]Go to your home directory, then to the *".mozilla/firefox"* subdirectory, and list the filesystem objects there:
```
$ cd
$ cd .mozilla/firefox
$ ls
```
[*]One of the  objects listed, will be a subdirectory with a name of the form "*xxxxxxxx*.default" (where "*xxxxxxxx*" represents a seemingly random sequence of characters); enter that subdirectory, and verify that it contains a file named **"pluginreg.dat"**:
```
$ cd *xxxxxxxx*.default
$ ls pluginreg.dat
```
[*]Make a backup copy of the file (better safe than sorry :))--e.g.:
```
$ cp pluginreg.dat pluginreg.dat_Saved
```
[*]Open the file in your favourite text editor--e.g., *gedit*:
```
$ gedit pluginreg.dat
```
[*]The very first line of the file contains the text:
```
Generated File. Do not edit.
```
Ignore that warning, and edit the file anyway. :biggrin:

[*]Locate the first few lines that describe the Java plugin--e.g.:
```
/usr/lib/jvm/java-6-sun-1.6.0.06/jre/plugin/i386/ns7/libjavaplugin_oji.so:$
:$
1206435800000:1:5:$
Java(TM) Plug-in 1.6.0_06:$
Java(TM) Plug-in 1.6.0_06-b02:$
33
```
That number on the last line shown above, i.e., *"33,"* specifies how many object types are defined for the plugin. Immediately following this line, are the actual definitions--one per line; they are numbered, beginning with 0. The last definition, then, will be number 32:
```
32:application/x-java-bean;jpi-version=1.6.0_06:Java::$
```
[*]You will be adding *two* lines to the list of definitions for this plugin--one for a Java *applet* version, and one for a Java *bean* version. Therefore, you will have to increment the number of objects by two--i.e., change the *"33"* shown above to *"35"*:
```
/usr/lib/jvm/java-6-sun-1.6.0.06/jre/plugin/i386/ns7/libjavaplugin_oji.so:$
:$
1206435800000:1:5:$
Java(TM) Plug-in 1.6.0_06:$
Java(TM) Plug-in 1.6.0_06-b02:$
[COLOR="Navy"]**35**[/COLOR]
```
[*]Add the following two lines to the list of definitions for the Java plugin; note that the lines **must** be numbered sequentially, so the lines will have to be added immediately following the currently last line (i.e., line *"32"*) of the list:
```
33:application/x-java-applet;jpi-version=1.4.1:Java::$
34:application/x-java-bean;jpi-version=1.4.1:Java::$
```
[*]Save the file.
[/LIST]
Next, close any Firefox windows that you may have open, then restart Firefox. Go to the [FONT="Courier New"]about:****plugins[/FONT] page, and you will find that there are two new lines appearing for the Java plugin:
```
application/x-java-applet;jpi-version=1.4.1
application/x-java-bean;jpi-version=1.4.1
```

You should now be able to run the applets from the [Java Plug-in 1.4.1 Demo Page.]("http://java.sun.com/products/plugin/1.4.1/demos/plugin/applets.html")

---


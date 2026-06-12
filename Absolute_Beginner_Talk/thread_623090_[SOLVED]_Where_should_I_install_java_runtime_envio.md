---
title: "[SOLVED] Where should I install java runtime enviorment?"
date: 2007-11-25
forum: Absolute Beginner Talk
---

### Post by staticvoid on 2007-11-25
/usr/java? thats where my jre is...

sv

---

### Post by rsambuca on 2007-11-25
Why don't you just install it from the repos and let Synaptic handle everything?

---

### Post by Pumalite on 2007-11-25
+1

---

### Post by staticvoid on 2007-11-25
i tried to do it from the repos. didn't work. I'll try doing it fresh though, what exactly do I need to install? jre and jdk from sun is in the repos? I need to be able to javac stuff.

thanx

sv

---

### Post by Pumalite on 2007-11-25
Why didn't work?

---

### Post by rsambuca on 2007-11-25
Just make sure you have your multiverse repositories active and then you can install them via Synaptic or apt-get.

---

### Post by ubuntu27 on 2007-11-25
[Make sure all the repositories are enabled]("https://help.ubuntu.com/community/Repositories") (e.g. Multiverse, Universe, )

Open the Termianl and type:

```
sudo apt-get install ubuntu-restricted-extras
```

That will install the runtime enviroment.

To program with Java also install:

sun-java6-jdk

```
sudo apt-get install sun-java6-jdk
```

More info on [Java]("https://help.ubuntu.com/community/Java") and [Restricted Formats]("https://help.ubuntu.com/community/RestrictedFormats")

---

### Post by nickpaton on 2007-11-25
What browser are you using?

If you are not using Firefox, you may need to create a symlink to the plugin folder of the browser you are using.

Let us know which one you are using and we can advise you further.  You say it doesn't work.  What test are you using to test Java?

Nick

---

### Post by rsambuca on 2007-11-25
> **ubuntu27 said:**
> [Make sure all the repositories are enabled]("https://help.ubuntu.com/community/Repositories") (e.g. Multiverse, Universe, )

Open the Termianl and type:

```
sudo apt-get [COLOR="Red"]**install**[/COLOR] ubuntu-restricted-extras
```

That will install the runtime enviroment.

To program with Java also install:

sun-java6-jdk

```
sudo apt-get install sun-java6-jdk
```

More info on [Java]("https://help.ubuntu.com/community/Java") and [Restricted Formats]("https://help.ubuntu.com/community/RestrictedFormats")

Just a little typo in there.  I added a word in red.

---

### Post by aysiu on 2007-11-25
> **staticvoid said:**
> /usr/java? thats where my jre is...

sv
Here's a step-by-step guide with screenshots:
[http://www.psychocats.net/ubuntu/java](http://www.psychocats.net/ubuntu/java)

---

### Post by ubuntu27 on 2007-11-25
> **rsambuca said:**
> Just a little typo in there.  I added a word in red.

Oh! Thanks :) I've corrected it now.

---

### Post by staticvoid on 2007-11-26
Hey thanks everybody! I got it installed. one last question: 
What plugin should I install for firefox?
[IMG]http://i71.photobucket.com/albums/i123/broinjc/Screenshot-5.png[/IMG]
someone mentioned I need to symlink some directories to my firefox plugin folder?

Anyway, I have jre and jdk install and I successfully compiled some java code, but when I went to view it in the browser, it wanted me to install a plugin. so many choices!

sv

---

### Post by staticvoid on 2007-11-26
[IMG]http://i71.photobucket.com/albums/i123/broinjc/Screenshot-1-1.png[/IMG]

oh great, now what? it still says "missing plugin"

---

### Post by GSF1200S on 2007-11-26
> **staticvoid said:**
> [IMG]http://i71.photobucket.com/albums/i123/broinjc/Screenshot-1-1.png[/IMG]

oh great, now what? it still says "missing plugin"

64bit or 32bit Ubuntu? DO NOT USE GJC PLUGIN. GJC doesnt have a security manager and can harm the system if malicious java code is in a website!

---

### Post by staticvoid on 2007-11-26
fewf thanx for the advice! I hav e 32 bit.

sv

---

### Post by staticvoid on 2007-11-26
so i tried java5 plugin and I still get a "missing plugin error" what can I try? Maybe I just need to start over with a fool proof tutorial.

---

### Post by GSF1200S on 2007-11-26
nah.. just open add/remove and remove all java plugins, and try java 6 plugin again.. I wish i could tell you specifically which packages, but im on 64 bit and my java listings are a bit of a mess :)

---

### Post by staticvoid on 2007-11-26
ok

update:
aaggg.... its still not working. "install missing plugin"  "plugin already installed" "sorry, you need to install this plugin" over and over again... I took the tutorial and redid everything. it still doesn't work...

sv

---

### Post by nickpaton on 2007-11-26
The problem may be due to having a broken link from the jre directory to the firefox plugin directory.  This will stop a new one being created in its place.

To sort this out it's best to start from scratch.

_**Remove old Java jre**_

Synaptic uninstall all of the following:

j2re1.4
j2re1.4 mozilla-plugin
sun-java5-plugin and any associated files
sun-java6-plugin and any associated files
icedtea-java7-jre
and anything else relating to java, j2re etc.

Search under 'j2re' and 'jre' should find them all.
There should now be nothing installed relating to Java.
DONT reinstall anything yet.
Close Synaptic

Check that all java related plugin links are removed from Firefox and Mozilla plugin folders:

Terminal:

```
gksudo nautilus
```

**[COLOR="Red"]**Remember you now have root priviledges so can do considerable damage if you accidently delete the wrong file**[/COLOR]**

Navigate to:

Places > Computer > Filesystem > usr > lib > firefox > plugins, and look for libjavaplugin.so or libjavaplugin_oji.so.

If either or similar files relating to Java or jre are present, delete them.

Go to usr > lib > mozilla > plugins and do the same thing.

Close Nautilus.

**_Reinstall Java jre_**

Synaptic install:
sun-java-6-plugin

That should install the plugin and automatically create a link to the firefox and mozilla plugin folders.

**_Testing Java jre_**

Test at: 

[http://www.java.com/en/download/help/testvm.xml]("http://www.java.com/en/download/help/testvm.xml")

for the little dancing man, or if that doesn't work try

[http://www.javatester.org/]("http://www.javatester.org/")

Click on the orange box at the top tells you what version of Java you've got.

**_Still not working_**

If both sites show no Java installed or the dreaded 'Install Plugin' box, check the firefox plugins folder for libjavaplugin.so (or libjavaplugin_oji.so) and 'Link to shared library'.
If it is not present or shows 'broken link' or similar, then the plugin has not linked from the Java plugin folder.
If it shows 'broken link' remove it using Nautilus again before proceeding further.

Close all firefox browsers.

Now check if Java has installed correctly.

**Not using Nautilus **- navigate to usr > lib > jvm > java-6-sun > jre > plugin > i386 > ns7 > and check libjavaplugin_oji.so is present.  If it is not present or the whole directory is missing, get back to me and I'll show you what to then do.

If it is present then Java has been installed correctly.

Now create a symlink between  libjavaplugin_oji.so and the firefox plugin folder:

```
sudo ln -s /usr/lib/jvm/java-6-sun /jre/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib/firefox/plugins/
```

and the Mozilla Plugin folder:

```
sudo ln -s /usr/lib/jvm/java-6-sun /jre/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib/mozilla/plugins/
```


Test once again, and hopefully should be working.

If it's still not working, can you post the contents of:

/usr/lib/fireflox/plugins

/usr/lib/mozilla/plugins

and the contents of ns7 folder at:

/usr/lib/jvm/java-6-sun /jre/plugin/i386/ns7/

Also in Synaptic, please list what is under j2re and jre relating to Java.

Good luck and come back with any questions you have.

Nick

---

### Post by staticvoid on 2007-11-26
**Thank you all so much!!! Heres a cake for your effort. I'll have java working in no time. and Nick, that is perfect, i'll get he linking working with this i'm sure :D**
[IMG]http://i71.photobucket.com/albums/i123/broinjc/birthday-cake-773619.jpg[/IMG]

sincerly,

Static Void

---

### Post by nickpaton on 2007-11-26
Love the rasberries and all that cream!!

It's a pleasure.

Nick

---

### Post by staticvoid on 2007-11-26
now i'll go help someone else :)

thanx again, 
sv

i'll post when i get it up and running

---

### Post by ubername on 2007-11-26
> **nickpaton said:**
> The problem may be due to having a broken link from the jre directory to the firefox plugin directory.  This will stop a new one being created in its place.

To sort this out it's best to start from scratch.

_**Remove old Java jre**_

Synaptic uninstall all of the following:

j2re1.4
j2re1.4 mozilla-plugin
sun-java5-plugin and any associated files
sun-java6-plugin and any associated files
icedtea-java7-jre
and anything else relating to java, j2re etc.

Search under 'j2re' and 'jre' should find them all.
There should now be nothing installed relating to Java.
DONT reinstall anything yet.
Close Synaptic

Check that all java related plugin links are removed from Firefox and Mozilla plugin folders:

Terminal:

```
gksudo nautilus
```

**[COLOR="Red"]**Remember you now have root priviledges so can do considerable damage if you accidently delete the wrong file**[/COLOR]**

Navigate to:

Places > Computer > Filesystem > usr > lib > firefox > plugins, and look for libjavaplugin.so or libjavaplugin_oji.so.

If either or similar files relating to Java or jre are present, delete them.

Go to usr > lib > mozilla > plugins and do the same thing.

Close Nautilus.

**_Reinstall Java jre_**

Synaptic install:
sun-java-6-plugin

That should install the plugin and automatically create a link to the firefox and mozilla plugin folders.

**_Testing Java jre_**

Test at: 

[http://www.java.com/en/download/help/testvm.xml]("http://www.java.com/en/download/help/testvm.xml")

for the little dancing man, or if that doesn't work try

[http://www.javatester.org/]("http://www.javatester.org/")

Click on the orange box at the top tells you what version of Java you've got.

**_Still not working_**

If both sites show no Java installed or the dreaded 'Install Plugin' box, check the firefox plugins folder for libjavaplugin.so (or libjavaplugin_oji.so) and 'Link to shared library'.
If it is not present or shows 'broken link' or similar, then the plugin has not linked from the Java plugin folder.
If it shows 'broken link' remove it using Nautilus again before proceeding further.

Close all firefox browsers.

Now check if Java has installed correctly.

**Not using Nautilus **- navigate to usr > lib > jvm > java-6-sun > jre > plugin > i386 > ns7 > and check libjavaplugin_oji.so is present.  If it is not present or the whole directory is missing, get back to me and I'll show you what to then do.

If it is present then Java has been installed correctly.

Now create a symlink between  libjavaplugin_oji.so and the firefox plugin folder:

```
sudo ln -s /usr/lib/jvm/java-6-sun /jre/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib/firefox/plugins/
```

and the Mozilla Plugin folder:

```
sudo ln -s /usr/lib/jvm/java-6-sun /jre/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib/mozilla/plugins/
```


Test once again, and hopefully should be working.

If it's still not working, can you post the contents of:

/usr/lib/fireflox/plugins

/usr/lib/mozilla/plugins

and the contents of ns7 folder at:

/usr/lib/jvm/java-6-sun /jre/plugin/i386/ns7/

Also in Synaptic, please list what is under j2re and jre relating to Java.

Good luck and come back with any questions you have.

Nick

Lovely guide, but I'm still stuck

Herre are my files:

john@Dell4620:/usr/lib/firefox/plugins$ ls -l
total 6900
lrwxrwxrwx 1 root root      37 2007-11-05 17:04 flashplugin-alternative.so -> /etc/alternatives/firefox-flashplugin
-rwxr-xr-x 1 root root 7040036 2007-11-11 11:05 libflashplayer.so
lrwxrwxrwx 1 root root      34 2007-11-08 18:21 libgcjwebplugin.so -> ../../classpath/libgcjwebplugin.so
lrwxrwxrwx 1 root root      39 2007-11-26 23:34 libjavaplugin.so -> /etc/alternatives/firefox-javaplugin.so
lrwxrwxrwx 1 root root      36 2007-11-05 16:23 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so
lrwxrwxrwx 1 root root      37 2007-11-05 16:23 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt
lrwxrwxrwx 1 root root      34 2007-11-05 16:23 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so
lrwxrwxrwx 1 root root      35 2007-11-05 16:23 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt
lrwxrwxrwx 1 root root      36 2007-11-05 16:23 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so
lrwxrwxrwx 1 root root      37 2007-11-05 16:23 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt
lrwxrwxrwx 1 root root      42 2007-11-05 16:23 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 root root      43 2007-11-05 16:23 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt
-rw-r--r-- 1 root root    9104 2007-10-22 15:12 libunixprintplugin.so
lrwxrwxrwx 1 root root      37 2007-11-26 22:12 libvlcplugin.so -> ../../mozilla/plugins/libvlcplugin.so


john@Dell4620:/usr/lib/mozilla/plugins$ ls -l
total 104
lrwxrwxrwx 1 root root    37 2007-11-05 17:04 flashplugin-alternative.so -> /etc/alternatives/mozilla-flashplugin
lrwxrwxrwx 1 root root    34 2007-11-08 18:21 libgcjwebplugin.so -> ../../classpath/libgcjwebplugin.so
lrwxrwxrwx 1 root root    39 2007-11-26 23:34 libjavaplugin.so -> /etc/alternatives/mozilla-javaplugin.so
lrwxrwxrwx 1 root root    36 2007-11-05 16:24 libtotem-basic-plugin.so -> ../../totem/libtotem-basic-plugin.so
lrwxrwxrwx 1 root root    37 2007-11-05 16:24 libtotem-basic-plugin.xpt -> ../../totem/libtotem-basic-plugin.xpt
lrwxrwxrwx 1 root root    34 2007-11-05 16:24 libtotem-gmp-plugin.so -> ../../totem/libtotem-gmp-plugin.so
lrwxrwxrwx 1 root root    35 2007-11-05 16:24 libtotem-gmp-plugin.xpt -> ../../totem/libtotem-gmp-plugin.xpt
lrwxrwxrwx 1 root root    36 2007-11-05 16:24 libtotem-mully-plugin.so -> ../../totem/libtotem-mully-plugin.so
lrwxrwxrwx 1 root root    37 2007-11-05 16:24 libtotem-mully-plugin.xpt -> ../../totem/libtotem-mully-plugin.xpt
lrwxrwxrwx 1 root root    42 2007-11-05 16:24 libtotem-narrowspace-plugin.so -> ../../totem/libtotem-narrowspace-plugin.so
lrwxrwxrwx 1 root root    43 2007-11-05 16:24 libtotem-narrowspace-plugin.xpt -> ../../totem/libtotem-narrowspace-plugin.xpt
-rw-r--r-- 1 root root 99460 2007-10-09 01:03 libvlcplugin.so


john@Dell4620:/usr/lib/jvm/java-6-sun-1.6.0.03/jre/plugin/i386/ns7$ ls -l
total 140
-rw-r--r-- 1 root root 137085 2007-09-25 07:10 libjavaplugin_oji.so

In synaptic:

searching for j2re gives 3 results: j2re1.4, j2re1.4mozilla plugin and openoffice. Only openoffice is installed

searching for jre gives 14 results of which 3 are installed, sun-java6-bin, sun-jave6-jre and sun-java6-plugin.

When I run the test from [http://www.java.com/en/download/installed.jsp](http://www.java.com/en/download/installed.jsp)

I get 

Oops! You don't have the recommended Java installed.
Your Java version is 1.4.2. Please click the button below to get the recommended Java for your computer.  

I am at a loss, any help very gratefully received!

---

### Post by rsambuca on 2007-11-26
This has nothing to do with the plugins, but what happens when you enter```
sudo update-alternatives --config java
```

---

### Post by ubername on 2007-11-27
> **rsambuca said:**
> This has nothing to do with the plugins, but what happens when you enter```
sudo update-alternatives --config java
```

Thanks, here is the output

john@Dell4620:~$ sudo update-alternatives --config java
[sudo] password for john:

There are 3 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/gij-4.2
          2    /usr/bin/cacao
*+        3    /usr/lib/jvm/java-6-sun/jre/bin/java

Press enter to keep the default[*], or type selection number: 3
Using `/usr/lib/jvm/java-6-sun/jre/bin/java' to provide `java'.

I then tried restarting firefox and got the same error message from the java test.

---

### Post by staticvoid on 2007-11-27
Hi, try symlinking the plugin manuelly:
[http://ubuntuforums.org/showthread.php?t=624631](http://ubuntuforums.org/showthread.php?t=624631)

I just restarted, uninstalled all the java stuff, and installed java-6-common and all the sun-java stuff, plus 6jdk's and jre's.

then I went to the firefox plugins directory and MIDDLE clicked the plugin with the broken link and linked it to the plugin. I just had a broken link the whole time!

Hope you get it figured out. maybe you can give these kind people a cake as well.

Static V

---

### Post by ubername on 2007-11-27
> **staticvoid said:**
> Hi, try symlinking the plugin manuelly:
[http://ubuntuforums.org/showthread.php?t=624631](http://ubuntuforums.org/showthread.php?t=624631)

I just restarted, uninstalled all the java stuff, and installed java-6-common and all the sun-java stuff, plus 6jdk's and jre's.

then I went to the firefox plugins directory and MIDDLE clicked the plugin with the broken link and linked it to the plugin. I just had a broken link the whole time!

Hope you get it figured out. maybe you can give these kind people a cake as well.

Static V

Hi thanks for this and your patience.
My symlinks are not (don't appear to be) broken.

Now  if I can figure out how to add pictures to my posts I can

A) give people a cake [http://www.mouseplanet.com/paris/BirthdayParCake.jpg](http://www.mouseplanet.com/paris/BirthdayParCake.jpg) for now

and

B) give screenshots of System>Preferences>Sun Java 6 plugin control panel
Which shows that I am using /usr/lib/jvm/java-6-sun-1.6.0.03/jre

Thanks

---

### Post by staticvoid on 2007-11-27
The cake looks great.

So the symlinks is not an issue. **You want to be able to view java applets in firefox and compile java source code then?** first at least try symlinking, it will take two seconds.

run this in a terminal:

cd /usr/lib/jvm/java-6-sun-1.6.0.03/jre/plugin/i386/ns7
ls

see that file? libjavaplugin_oji.so? it has to be symlinked into firefox plugins directory.
open up a file manager via gksu to be root (BE VERY VERY CAREFUL!) and make two windows with these two locations:

/usr/lib/firefox/plugins
/usr/lib/jvm/java-6-sun-1.6.0.03/jre/plugin/i386/ns7

 and then you can hold down both mouse buttons (middle mouse button) and drag libjavaplugin_oji.so into /usr/lib/firefox/plugins. then choose "link here"

Please just try that :) I have exactly the same stuff as you have installed I believe, because the file path in your scrrenshot is the same as mine.

sv

---

### Post by ubername on 2007-11-27
> **staticvoid said:**
> The cake looks great.

So the symlinks is not an issue. **You want to be able to view java applets in firefox and compile java source code then?** first at least try symlinking, it will take two seconds.

run this in a terminal:

cd /usr/lib/jvm/java-6-sun-1.6.0.03/jre/plugin/i386/ns7
ls

see that file? libjavaplugin_oji.so? it has to be symlinked into firefox plugins directory.
open up a file manager via gksu to be root (BE VERY VERY CAREFUL!) and make two windows with these two locations:

/usr/lib/firefox/plugins
/usr/lib/jvm/java-6-sun-1.6.0.03/jre/plugin/i386/ns7

 and then you can hold down both mouse buttons (middle mouse button) and drag libjavaplugin_oji.so into /usr/lib/firefox/plugins. then choose "link here"

Please just try that :) I have exactly the same stuff as you have installed I believe, because the file path in your scrrenshot is the same as mine.

sv

Hi and thanks again for comments.

I tried the synlinking thing, but no success, still get the 'Oops' message from java.com. If it makes any difference, I don't (yet) need to compile Java source, just to use applets.

Sorry this is being so painful.

---

### Post by ubername on 2007-11-27
Hi
I finally got the java working by uninstalling (via synaptic) everything to do with 'jre' and 'classpath' 

Then I went to firefox and opened a 'java' page' 

Got the Missing plugin link, which told me to do a manual install.

Abandoned that and went to synaptic and reinstalled  sun java6plugin from there

All's well.

(I hope I haven't annoyed people, I had no real idea that classpath was an issue. I just reacted to a message which talked about GNU classpath being incomplete when I loaded a java page)

Please let me know if this has hampered your diagnoses, I really tried to post everything relevant.

A large quantity of fresh cream filled chocolate éclairs, with a side order of Jus from forest berries would be available, if this were only the real world.

---

### Post by nickpaton on 2007-11-27
Hi Ubername.  No you haven't annoyed anyone at all, so no worries there M8.

Love the cake too!!

Useful bit of information about classpath, which i'd never heard of and now have.

I think your posts have been very useful in giving a different slant on the problem and another area for people to go looking into, and all in all it's turning into a great thread for the future too.

So thanks for that - in general the more information you post the better to try and sort out problems.

Just tucking into an eclair now......

Nick

---


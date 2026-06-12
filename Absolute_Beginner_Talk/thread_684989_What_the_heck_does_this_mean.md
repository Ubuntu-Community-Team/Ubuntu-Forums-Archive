---
title: "What the heck does this mean?"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by Mosod on 2008-02-01
I'm trying to get Eclipse 3.3 up and running but I'm running into problem after problem.  A lot of them seem like they wouldn't be too hard to overcome if I had a clue as to what I was doing.

Here is my latest greatest problem.  When I try and run eclipse I get this ungodly error message:
```
JVM terminated. Exit code=13
/usr/bin/java
-Dosgi.requiredJavaVersion=1.5
-Xms40m
-Xmx256m
-jar /home/joel/.eclipse/plugins/org.eclipse.equinox.launcher_1.0.1.R33x_v20070828.jar
-os linux
-ws gtk
-arch x86
-showsplash
-launcher /home/joel/.eclipse/eclipse
-name Eclipse
--launcher.library /home/joel/.eclipse/plugins/org.eclipse.equinox.launcher.gtk.linux.x86_1.0.2.R331_v20071019/eclipse_1021.so
-startup /home/joel/.eclipse/plugins/org.eclipse.equinox.launcher_1.0.1.R33x_v20070828.jar
-exitdata 2128022
-vm /usr/bin/java
-vmargs
-Dosgi.requiredJavaVersion=1.5
-Xms40m
-Xmx256m
-jar /home/joel/.eclipse/plugins/org.eclipse.equinox.launcher_1.0.1.R33x_v20070828.jar 
```

I'm guessing those first two lines mean I dont have Java setup correctly.  I've tried searching for "sun-java" in synaptic and I have a smattering of the results already installed but I really have no clue which pieces I need and don't need.

ps how do you thank people (the thanked stats in the profiles that head posts).  I love to know how to do that and show some "official" appreciation to the people here who have been helping me out.

---

### Post by davec64 on 2008-02-01
I had something similar.
What Idid to solve the problem was uninstall the Java JRE 1.5 and installed Sun-Java6-jre and the sun-java6-plugin. There in the repositories.

Solved my problem!
Hope it helps you!

---

### Post by davec64 on 2008-02-01
I forgot!
Haven't got a clue how to thank people!

---

### Post by mgmiller on 2008-02-01
Just click on the icon to thank someone.

---

### Post by Mosod on 2008-02-01
Thanks for the response.  Unfortunately I still get the same error.  Do I need any files besides sun-java6-jre and sun-java6-bin?

---

### Post by mgmiller on 2008-02-01
You may have installed java6, but are you using it?

Enter the following in a terminal and you can see what is installed and easily switch to the one you want:

```
sudo update-alternatives --config java
```

---

### Post by mgmiller on 2008-02-01
Also, the best way to install java, flash and a host of other things is to install the metapackage ubuntu-restricted-extras.

You can search for it in synaptic or add/remove programs or from the command line:
```
sudo apt-get install ubuntu-restricted-extras
```

This is assuming you are running ubuntu.  If you have kubuntu or xubuntu, just change the first word accordingly, eg: kubuntu-restricted-extras

---

### Post by Mosod on 2008-02-01
> **mgmiller said:**
> You may have installed java6, but are you using it?

Enter the following in a terminal and you can see what is installed and easily switch to the one you want:

```
sudo update-alternatives --config java
```

Looks java6 is selected.  Here is what I get:

```
There are 2 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
          1    /usr/bin/gij-4.2
*+        2    /usr/lib/jvm/java-6-sun/jre/bin/java

Press enter to keep the default[*], or type selection number: 

```

---

### Post by mgmiller on 2008-02-01
I have the following java 6 packages installed:
sun-java6-bin
sun-java6-fonts
sun-java6-jre
sun-java6-plugin

Also, do you have the ubuntu-restricted-extras meta package installed?

---

### Post by Mosod on 2008-02-01
Hmmm.   I don't seem to be able to find sun-java6-plugin anywhere in synaptic which is the only way I know how to find things.  This may be the problem  Know how I can get it?

Everything else on the list including the restricted extras (thank you for that by the way) is installed.

EDIT:  Some searching around on the web seems to be shedding some light on the issue.  I'm running the AMD64 version of Ubuntu.  Its looking like the plugin just isnt available.

---

### Post by mgmiller on 2008-02-01
sun-java6-plugin is in multiverse.  

Make sure all your repositories are turned on.
In Synaptic go to Settings > Repositories and in the first tab that opens (Software Sources), make sure everything except maybe Source code is checked.  

I think the one you are missing is multiverse.

Edit:
After doing that, you will need to click the reload button.  It will probably prompt you to do that anyway.

---

### Post by Mosod on 2008-02-01
Looks like I am out of luck.  I'm using the AMD64 version of Ubuntu and I've come across some bug reports about it not being available for this version.

---

### Post by mgmiller on 2008-02-01
Ahhh.  I didn't know you were using the 64 bit version.  
I have avoided it for just this kind of reason.  You really won't have much of a performance change by installing the 32 bit ubuntu.  I have been running 32 bit on my 64 bit AMD cpu for a long time and it runs great.  

If this is a show stopping problem for you, consider reinstalling using the 32 bit installer.

Good luck.  :popcorn:

---

### Post by Mosod on 2008-02-06
Problem Solved!!!  It seems the eclipse page gave me the wrong file.  Even though the link I clicked was clearly labeled as being the 64 bit version of eclipse, what I was given was a 32 bit version.  If I had not installed a 32 bit version of java to get firefox java plugins, eclipse wouldn't have even started up.  In any event, Now that I have told eclipse to go look for the 32 bit java binary, everything works.

I can't believe I spent like a week trying to fix a problem caused by a bad link.

---

### Post by nikoPSK on 2008-02-06
hrm, I'm pretty sure you're not supported...

---

### Post by jordanmthomas on 2008-02-06
Just to throw it out there, I don't think the message you were getting was an error, but just the options with which eclipse was being started.  I think the only error message was the one saying the jvm had exited.

It's solved now, so it's really a moot point, but whatever.  :)

---


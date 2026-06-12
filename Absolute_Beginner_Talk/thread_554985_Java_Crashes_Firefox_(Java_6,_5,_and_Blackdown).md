---
title: "Java Crashes Firefox (Java 6, 5, and Blackdown)"
date: 2007-09-19
forum: Absolute Beginner Talk
---

### Post by MrKirby on 2007-09-19
So I've installed Sun Java 6, after uninstalling my previous versions of Java that I have tried. I believe this problem first began when I installed Java 6 (just ASSUMING I could just DO that), when I already had the Java 5 runtime environment installed (came with Limewire Pro), and whatever my computer was using before as default from install.  All of a sudden, I noticed many java functions were not working correctly, and loading a Java applet caused Firefox to crash with no message.

I proceeded to uninstall and reinstall various versions of java runtime and test them individually, after uninstalling all of them.  Each one now seems to fail me. I tried Java 5, verified that when I typed about:plugins into firefox that the plugin was recognized -- same.  I uninstalled that and installed Java 6, verified the plugin -- same. I uninstalled Java 6 and installed Blackdown Java -- same. I've proceeded to play around for awhile now to no avail.

Here is my current setup:

Installed Java 6 and plugin using Synaptic.

about:plugins shows the Java 6 plugin recognized.

i type "sudo update-alternatives --config java" and get
There is only 1 program which provides java
(/usr/lib/jvm/java-6-sun/jre/bin/java). Nothing to configure.

sudo gedit /etc/jvm
gives me

/usr/lib/jvm/java-6-sun
/usr/lib/jvm/java-1.5.0-sun
/usr/lib/jvm/java-gcj
/usr

however, typing "java -version" simply gives me a list of packages containing that program. That seems suspicious, but I'm not going to touch it for now until I get some advice.

Now, I've followed several online How Tos for each java version, and all three that I've mentioned have yielded the same result, all three respective browser plugins being recognized.

At that point, I proceeded to uninstall and reinstall firefox, hitting a brick wall.  As you can see, I am still resorting to making a post.

There's gotta be something I'm not checking or doing right.
Please forgive my noobieness.
OH, and yes, I uninstalled Limewire. It stopped working when all this started up.

---

### Post by MrKirby on 2007-09-19
I'm running Feisty, Firefox 2

---

### Post by MrKirby on 2007-09-19
I also forgot to mention how when I installed Blackdown Java, when I tested my Java on the Java website, instead of crashing firefox, it simply failed to load the applet.

---

### Post by nielsolij on 2007-12-11
Hi,
I had the same problems with Java crashing firefox in a non-reporducible way. I recently installed firefox 3 beta and this seems to run OK. No crashes since I installed it (running now about three weeks). I got it from [http://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0b1/](http://releases.mozilla.org/pub/mozilla.org/firefox/releases/3.0b1/)
I am aware that running a beta and not in a repository is not favorable, but I was helped with this version.

---


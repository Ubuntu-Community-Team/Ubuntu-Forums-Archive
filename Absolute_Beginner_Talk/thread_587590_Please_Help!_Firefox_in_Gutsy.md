---
title: "Please Help! Firefox in Gutsy"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by vertexoflife on 2007-10-22
Okay, firefox applets continually lock up my firefox rendering it useless. Following this guide [https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java) I tried sudo apt-get install sun-java6-plugin and I already had it.

There is a Java plugin in my aboutlugins for firefox.

Java -version output below.
```


java -version
java version "1.6.0_03"
Java(TM) SE Runtime Environment (build 1.6.0_03-b05)
Java HotSpot(TM) Client VM (build 1.6.0_03-b05, mixed mode, sharing)
```

How can I resolve this?
__________________

---

### Post by Sef on 2007-10-22
I would delete all the applets and then start adding them back one by one.   Find out which applet is giving you problems.

---

### Post by vertexoflife on 2007-10-22
How do I delete applets one by one?

I only have this problem with one site, which is an important one. It's at the Blackboard.com site, which is a website for professors to contact their students.

---

### Post by vertexoflife on 2007-10-22
bump de bump

---

### Post by vertexoflife on 2007-10-23
-sigh- bump

---

### Post by vertexoflife on 2007-10-23
bump bump bump

---

### Post by philinux on 2007-10-23
If you mean addons then in a terminal type

firefox -safe-mode then you can tools addons then make a note of what you had and try uninstalling  them and then you can add them back and see which caused the problem.

---

### Post by vertexoflife on 2007-10-23
It seems that running an applet from a particular website is causing this.
A security certificate will come up that will say "Security Certificate Expired" and asks if I want to accept it or not. By now, firefox is using about 80 or 90% of the CPU. Even if I accept or don't accept it, it does not change the problem, because the same thing will happen when I visit the site again.

---

### Post by vertexoflife on 2007-10-23
Bada-bump

---

### Post by rudeboyskunk on 2007-10-23
I've been having a lot of trouble like this as well.  I think the big memory stealer applet is the sidebar (for me at least, don't know about you).  I think Compiz also causes Firefox to freeze up and either get the smoky look or the blindingly-bright look.

---

### Post by vertexoflife on 2007-10-23
Sidebar? No, I don't have that thing. I only have this problem with one website, and it is mostly caused by rhe java plugin, is there a way to work around this particular website? This site is very important and I need to be able to use it.

---

### Post by vertexoflife on 2007-10-23
I will bump until someone helps or tells me it is hopeless. =(

---

### Post by mandrill on 2007-10-23
> **rudeboyskunk said:**
> I've been having a lot of trouble like this as well.  I think the big memory stealer applet is the sidebar (for me at least, don't know about you).  I think Compiz also causes Firefox to freeze up and either get the smoky look or the blindingly-bright look.

for a quick fix install iceape navigator from the repositories (system>admin>synaptic) - I think that will work - it is the gnu version of mozilla seamonkey, has mail client etc...I use it in addition to firefox, maybe it will bypass the current problem until you can spend the time to figure it out.....

---

### Post by alienexplorers on 2007-10-23
Here is a list of problematic extensions in Firefox.
> [http://kb.mozillazine.org/Problematic_extensions](http://kb.mozillazine.org/Problematic_extensions)
You can also try disabling compiz (Visual Effects) since they seem to cause the grey Smokey screen.
You could also rebuild your Firefox profile using from the terminal
> Firefox -profilemanager
Then copy your important data over to the new profile.
> [http://kb.mozillazine.org/Migrating_settings_to_a_new_profile](http://kb.mozillazine.org/Migrating_settings_to_a_new_profile)

As for the java make sure the plugin is linked to:
> ln -s /usr/lib/jvm/java_version/jre/plugin/i386/ns7/libjavaplugin_oji.so

---

### Post by vertexoflife on 2007-10-23
Thank you so much! AdBlock Plus was the one that was causing issues with my Firefox. You have no idea how relieving this is! Thank you! :)

Solution:
Uninstall AdBlock Plus

---


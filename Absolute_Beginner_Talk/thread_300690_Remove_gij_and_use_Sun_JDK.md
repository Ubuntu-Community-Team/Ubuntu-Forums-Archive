---
title: "Remove gij and use Sun JDK"
date: 2006-11-16
forum: Absolute Beginner Talk
---

### Post by sri1025 on 2006-11-16
Hi all,

I want to use the Sun JDK which I have it on '/java' but when I go to command prompt and type java -version, it show this....
```

java version "1.4.2"
gij (GNU libgcj) version 4.1.0 (Ubuntu 4.1.0-1ubuntu8)

Copyright (C) 2006 Free Software Foundation, Inc.
This is free software; see the source for copying conditions.  There is NO
warranty; not even for MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.

```

I don't want to use this JRE, I want to use the one that is there on my root (/java)... 

Can someone help me...???

---

### Post by sri1025 on 2006-11-17
Can someone tell me atleast how to remove gij...?

I used Synaptic Package Manager and I searched for the word 'gij' and I selected it for a complete removal.

But when I Apply the changes, it is fetching JRE 1.5 from some ubuntu website. I already have it in my '/java' directory and I want just want to uninstall gij and use this...

How can I do it...???

---

### Post by yota on 2006-11-17
There's no need to remove gij, which is needed as a dependency by other packages, ubuntu handles the coexistence of more applications that handle the same service, open a terminal and do this:
> 
yota@linbook:~$ sudo update-alternatives --config java

There are 5 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
*+    1        /usr/lib/j2se/1.4/bin/java
      2        /usr/bin/gij-wrapper-4.0
      3        /usr/bin/gij-wrapper-4.1
      4        /usr/lib/jvm/java-gcj/jre/bin/java
      5        /usr/lib/jvm/java-1.5.0-sun/jre/bin/java

Press enter to keep the default[*], or type selection number:

The chosen one will be the default.
If you want to use the sun JDK install the package with:
```

aptitude install sun-java5-jdk

```
Hope this helps.

---

### Post by hod139 on 2006-11-17
Yota, that's not quite right.  To change the java preferences you should use: 
```

sudo update-java-alternatives -s java-1.5.0-sun
```In dapper or edgy, the official sun packages are in the multiverse repository,  so you will have to enable that (I'm sure it will get moved to the official ones after the source is available in the spring, probably before feisty is released).  Also, unless you want to do development, you only need the JRE package, not the JDK.

---

### Post by yota on 2006-11-17
Thanks hod139, I missed the OP just needs JRE.

And I didn't know that there were a specilized update-alternatives for java: I supposed I've tryed to help someone and got a lot back for myself :-D

---

### Post by dsagastume on 2006-11-17
hi hod139, look i'm having this same problem of modifying java config, does this solution you posted modifies the PATH

---

### Post by sri1025 on 2006-11-17
When I execute the following command:

$ update-alternatives --config java

It only shows me 2 JREs, and none of them are from Sun. But I would like to point Ubuntu to use my own JDK which is J2SDK 1.4.2_11 downloaded from Sun and I installed it separately under my root.

I don't want to use any of the ones bundled with Ubuntu by default.

Is there a way to do it...? Or do I need to change the location from '/java' to '/usr/lib/jvm/my_jdk1.4' and execute this command:

$ sudo update-java-alternatives -s my_jdk1.4

Thank you,
Srikanth

---

### Post by yota on 2006-11-20
If you want to use an alternative java, you have manually installed, you must inform the system of it's existence in this way:
> 
root@linbook:/usr/lib/jvm# update-alternatives --install java13 java /opt/jdk1.3.1_19/bin/java 0
root@linbook:/usr/lib/jvm# update-alternatives --config java

There are 6 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
*+    1        /usr/lib/j2se/1.4/bin/java
      2        /usr/bin/gij-wrapper-4.0
      3        /usr/bin/gij-wrapper-4.1
      4        /usr/lib/jvm/java-gcj/jre/bin/java
      5        /usr/lib/jvm/java-1.5.0-sun/jre/bin/java
      6        /opt/jdk1.3.1_19/bin/java

Press enter to keep the default[*], or type selection number:

As you can see I added this way jdk1.3.1 that I've downloaded from Sun, and which is not provided by ubuntu.
Look at 'man update-alternatives' to learn details about the command.

With --config you can chose the default, but don't forget to export JAVA_HOME="the/path/of/your/jre" in your profile.

update-java-alternatives requires instead a .jinfo file that describe the java files location; probably the jre from sun doesn't containt it (let me know), so I suppose that update-alternatives is easier in this case.

Hope this helps.

---

### Post by steve.horsley on 2006-11-20
Whenever I installed the JRE/JDK from Sun, I just deleted the java symlink in **/etc/alternatives** and replaced it with one that points to my java installetion. Never had any problems. e.g.
cd /etc/alternatives
sudo rm java
ln -s /opt/whateverTheNameIsThisWeek/java java

---

### Post by yota on 2006-11-20
> **steve.horsley said:**
> I just deleted the java symlink in **/etc/alternatives** and replaced it with one that points to my java installetion.

Although there's nothing particularly wrong, that's the quick&dirty way: update-alternatives is just a clean interface to manage symlinks in /etc/alternatives for you, but you're not bind to use it.

You can move the symlinks by hand or let the system handle them, IMHO the latter is safer and enables you to quick switch beetween different releases.

---

### Post by sri1025 on 2006-11-21
> **yota said:**
> If you want to use an alternative java, you have manually installed, you must inform the system of it's existence in this way:

As you can see I added this way jdk1.3.1 that I've downloaded from Sun, and which is not provided by ubuntu.
Look at 'man update-alternatives' to learn details about the command.

With --config you can chose the default, but don't forget to export JAVA_HOME="the/path/of/your/jre" in your profile.

update-java-alternatives requires instead a .jinfo file that describe the java files location; probably the jre from sun doesn't containt it (let me know), so I suppose that update-alternatives is easier in this case.

Hope this helps.
Thank you Yota,

That did it!

---


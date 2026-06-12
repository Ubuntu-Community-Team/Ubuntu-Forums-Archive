---
title: "i need help installing Sun Java and plugin for Firefox"
date: 2006-03-30
forum: Absolute Beginner Talk
---

### Post by slipk487 on 2006-03-30
i can figure out how to install Sun Java and the plugin for Firefox and automatix will not install firefox and the other programs so can someone help me

---

### Post by slipk487 on 2006-03-31
ive done this but it didnt work


I hope this will be useful to someone. I couldn't find java-package in the repositories because I hadn't added multiverse. So, I installed java in a different way.

First, download the linux runtime installer here. Do NOT get the rpm! Get the one that says Linux (self-extracting file).

After downloading, cd to where you downloaded the file and run:
Code:

sudo mv jre-1_5_0_05-linux-i586.bin /usr/local cd /usr/local sudo chmod a+x jre-1_5_0_05-linux-i586.bin sudo sh jre-1_5_0_05-linux-i586.bin

Say 'yes' to the license agreement and watch it extract the files into a folder called jre1.5.0_05
You're almost done. Now you want to install the plugin for firefox:
Code:

cd /usr/lib/mozilla-firefox/plugins sudo ln -s /usr/local/jre1.5.0_05/plugin/i386/ns7/libjavaplugin_oji.so

Firefox is now happily running java applets.
The final steps are:
Code:

sudo ln -sf /usr/local/jre1.5.0_05/bin/java_vm /usr/bin/java_vm sudo update-alternatives --install /usr/bin/java java /usr/local/jre1.5.0_05/bin/java 1


And now the java runtime environment appears in your list of choices when running 'sudo update-alternatives --config java'! Go ahead and run that, and chose the sun java option. Then to check to make sure it worked, run 'java -version', which should output something like this:
Code:

java version "1.5.0_05" Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_05-b05) Java HotSpot(TM) Client VM (build 1.5.0_05-b05, mixed mode, sharing)

Done!

If you want to do some configurating with the java control pannel, run 'sh /usr/local/jre1.5.0_05/bin/ControlPanel'.

---

### Post by Sef on 2006-03-31
The link below tells how to install Sun Java.  (It's toward the bottom of the page.)

[https://wiki.ubuntu.com/RestrictedFormats]("https://wiki.ubuntu.com/RestrictedFormats")

---

### Post by wolfee on 2006-03-31
try this then run it and then install firefox with plugins from menu

[http://ubuntuforums.org/showthread.php?t=138405](http://ubuntuforums.org/showthread.php?t=138405)

---

### Post by dcstar on 2006-03-31
[QUOTE=slipk487]
.......
cd /usr/lib/mozilla-firefox/plugins sudo ln -s /usr/local/jre1.5.0_05/plugin/i386/ns7/libjavaplugin_oji.so
.......[/QUOTE]
An important thing to remember is that the Java plugin **must be a link** in the Firefox plugins directory, and cannot be the actual file (as other plugins can be).

---

### Post by slipk487 on 2006-03-31
so i how should i do it or wat do i need to do

---

### Post by slipk487 on 2006-04-01
Is there anyway of installing Sun Java from the SPM

---

### Post by Robsteranium on 2007-12-26
Perhaps this is a bit late but in case it's of help to somebody else:

Have you tried installing the sun-java6-plugin through synaptic?

---

### Post by capink on 2007-12-26
Try [this]("/usr/lib/jvm/java-6-sun-1.6.0.00/jre/plugin/i386").

Note: You might have to change the pathname in the second step to reflect the correct java direcotry, depending on which java update you install.

---

### Post by zvacet on 2007-12-26
```
sudo apt-get install ubuntu-restricted-extras
```

and you will get Java and other things you probably want to install anyway.

---


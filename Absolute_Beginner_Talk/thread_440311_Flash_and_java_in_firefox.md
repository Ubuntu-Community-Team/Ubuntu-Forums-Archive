---
title: "Flash and java in firefox"
date: 2007-05-11
forum: Absolute Beginner Talk
---

### Post by 5ER on 2007-05-11
I have 64-bit kubuntu and I have both 64-bit and 32-bit firefox installed. I'm centering on the 32bit one.
Where can I get plugins for flash and java?

Automatic firefox plugins download fails (I agree with agreement, download, then simply says it failed) on both plugins.

Manual download for flash sucks. Bin installer says that it does not work on 64-bit, while rpm alien converted to deb also does not work.

Manual download for java also does not work. Bin installing makes no difference than take space on my hdd.
Debs in the repos don't seem to include v6 plugin. Help me.

Why don't they just tar.gzip files to put in firefox plugins dir and not put it in some installers :roll: 

Can anyone do that and attach the files?

---

### Post by vikram on 2007-05-11
try this

```


 sudo apt-get install flashplugin-nonfree

 sudo apt-get install sun-java5-jre sun-java5-fonts sun-java5-plugin
 sudo update-alternatives --set java /usr/lib/jvm/java-1.5.0-sun/jre/bin/java

```you may need to enable non free repositories. I found this very helpful:
[http://http://users.piuha.net/martti/comp/ubuntu/install.html]("http://http//users.piuha.net/martti/comp/ubuntu/install.html")

---

### Post by 5ER on 2007-05-11
Well, flashplugin-nonfree isn't in the non-free repos. I have real-player and stuff, but not flashplugin.

I would really appreciate if someone who's got flash would tar.gz the flash files in firefox/plugins directory and then attach it.

---

### Post by 5ER on 2007-05-13
How do I use the non-free repos?

---


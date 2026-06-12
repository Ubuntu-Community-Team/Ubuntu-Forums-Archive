---
title: "Help Installing JRE/Vassal"
date: 2005-07-23
forum: Absolute Beginner Talk
---

### Post by grofaz on 2005-07-23
I'm trying to manually install the java runtime environment, which I seem to have successfully accomplished. However, I'm having trouble enabling the mozilla-firefox plugin. I have been following Suns instructions but this is what I get at the terminal:

kudu@ubuntu:~/apps/java$ ls
jre1.5.0_04  jre-1_5_0_04-linux-i586.bin
kudu@ubuntu:~/apps/java$ cd /usr/lib/mozilla-firefox/plugins
kudu@ubuntu:/usr/lib/mozilla-firefox/plugins$ ln -s /usr/java/jre1.5.0/plugin/i3 86/ns7
ln: creating symbolic link `./ns7' to `/usr/java/jre1.5.0/plugin/i386/ns7': Perm ission denied
kudu@ubuntu:/usr/lib/mozilla-firefox/plugins$ /libjavaplugin_oji.so .

How do I enable the java plugin?? I'm trying to get VASSAL up and running but it ain't easy!

regards,
grofaz

---

### Post by poofyhairguy on 2005-07-23
[QUOTE=grofaz]I'm trying to manually install the java runtime environment, which I seem to have successfully accomplished. However, I'm having trouble enabling the mozilla-firefox plugin. I have been following Suns instructions but this is what I get at the terminal:

kudu@ubuntu:~/apps/java$ ls
jre1.5.0_04  jre-1_5_0_04-linux-i586.bin
kudu@ubuntu:~/apps/java$ cd /usr/lib/mozilla-firefox/plugins
kudu@ubuntu:/usr/lib/mozilla-firefox/plugins$ ln -s /usr/java/jre1.5.0/plugin/i3 86/ns7
ln: creating symbolic link `./ns7' to `/usr/java/jre1.5.0/plugin/i386/ns7': Perm ission denied
kudu@ubuntu:/usr/lib/mozilla-firefox/plugins$ /libjavaplugin_oji.so .

How do I enable the java plugin?? I'm trying to get VASSAL up and running but it ain't easy!

regards,
grofaz[/QUOTE]

Here is how:

[https://wiki.ubuntu.com/Java](https://wiki.ubuntu.com/Java)

Why are you doing it the hard way...and not how the Ubuntu Guide says?

---

### Post by Ubunted on 2005-07-23
I'd hardly consider that way much easier.

All you gotta do is add this to sources.list:

```
deb http://ftp2.caliu.info/backports hoary-backports main universe multiverse restricted
deb http://ftp2.caliu.info/backports hoary-extras main universe multiverse restricted
```

Followed by:

```
sudo apt-get update
apt-get install sun-j2re1.5
```

Bam, done.

---

### Post by poofyhairguy on 2005-07-23
[QUOTE=Ubunted]I'd hardly consider that way much easier.

All you gotta do is add this to sources.list:
[/QUOTE]


To do that: 

> sudo gedit /etc/apt/sources.list

---

### Post by grofaz on 2005-07-24
I figured it out, got it installed properly now. Thanks! However, the new problem is putting vassal where I want it. Everytime I launch it it goes in a folder where I don't want it to go. I can't find a way to change the download directory to make it go into a "vassal" folder I created for it. Help??!

---

### Post by poofyhairguy on 2005-07-24
[QUOTE=grofaz]I figured it out, got it installed properly now. Thanks! However, the new problem is putting vassal where I want it. Everytime I launch it it goes in a folder where I don't want it to go. I can't find a way to change the download directory to make it go into a "vassal" folder I created for it. Help??![/QUOTE]

Hmm...its likes its my shared folder. I bended to it, instead of the other way around. I bet there is an easy way though.

Lazy wins again.

---

### Post by grofaz on 2005-07-24
Figured that one out too. All is well. It was a VASSAL preferences file telling it what to do. Remove that and you can start from scratch and put it where you like. Thanks all!

---


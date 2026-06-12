---
title: "Firefox+Java problem - different twist"
date: 2007-12-16
forum: Absolute Beginner Talk
---

### Post by apmjoshi on 2007-12-16
Greetings,

Like many people on this forum, I have been struggling to get Java working in Firefox. I am using 32 bit Gutsy on a Windows XP dual-boot laptop.

I have followed the instructions/suggestions in the forum and unistalled version 1.4 of Java sdk. I have installed JRE 1.6 and the plugin from the Sun site (through Synaptics). As far as I can tell, this is the only Java installation on my machine. As Firefox refuses to recognise this Java installation, I took a look at the plugins folder in Firefox. The output is as follows
```

andy@andy-laptop:~$ cd /usr/lib/firefox/plugins
andy@andy-laptop:/usr/lib/firefox/plugins$ ls
flashplugin-alternative.so  libtotem-gmp-plugin.xpt
libjavaplugin_oji.so        libtotem-mully-plugin.so
libjavaplugin.so            libtotem-mully-plugin.xpt
libtotem-basic-plugin.so    libtotem-narrowspace-plugin.so
libtotem-basic-plugin.xpt   libtotem-narrowspace-plugin.xpt
libtotem-gmp-plugin.so      libunixprintplugin.so
andy@andy-laptop:/usr/lib/firefox/plugins$ 

```
The files** libjavaplugin_oji.so **and **  libjavaplugin.so ** are highlighted in red (indicating they are broken). When I look at the same folder graphically the icon clearly has a cross on it. I tried to link these files to the ones in the java directory using 
```

sudo ln -f -s /usr/bin/jvm/java-6-sun/jre/plugin/i386/ns7/libjavaplugin_oji.so ./libjavaplugin_oji.so

```
The command does not give any error messages but the link remains broken. Am I doing something wrong? I am hoping that this final step will make Java work on my machine.

Thanks in advance for your replies.

Regards
Aniruddha

---

### Post by jfank on 2007-12-16
I'm also having the same problem.  There is certain websites that FF will recognise the java installation and some websites won't recognise the installation and tell me that I have to install the newest version of it.  So I'm needing help on this as well.

---

### Post by apmjoshi on 2008-02-04
:guitar:I think I have finally managed to get Firefox and Java working on Ubuntu! I followed the steps below:
0. Installed Sun Java 6 following instructions in the forum
1. Downloaded Firefox 3 beta 2 from [www.mozilla.org](www.mozilla.org)
2. Extracted the entire archive to a new folder - there is no installation. For me the program is installed in $HOME/Downloaded Stuff/firefox
3. Using Terminal, I executed the command
```
andy@andy-laptop:~/Downloaded Stuff/firefox/plugins$ sudo ln -s /usr/lib/jvm/java-6-sun-1.6.0.03/jre/plugin/i386/ns7/libjavaplugin_oji.so libjavaplugin_oji.so
```
4. When I execute ```
/home/andy/"Downloaded Stuff"/firefox/firefox
``` Firefox comes up and Java applets get loaded without a murmur.

Now that I have got this working after months, I forgot what I wanted Java for :)

Aniruddha

---

### Post by jan quark on 2008-02-04
I always use this

```
sudo apt-get install sun-java6-jre sun-java6-bin sun-java6-plugin
```

---


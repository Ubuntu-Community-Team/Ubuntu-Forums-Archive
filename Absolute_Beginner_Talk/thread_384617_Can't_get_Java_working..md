---
title: "Can't get Java working."
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by Fidelio on 2007-03-14
I installed java from synaptic, but when I visited the java site to test my installation, it siad I did not have the lastest version of java. I downloaded the bin file. I'm not exactly sure what a bin file is, but when I clicked on it on the desktop it gave me the option to 'run' or 'run in terminal'
I tried run first and nothing happened, so I tried 'run in terminal' which gave me the license agreement, and appeared to run the installer. I still don't have java. I've tried website with java and running frostwire and neither work.
Do I need to try anything else?

---

### Post by Kobalt on 2007-03-14
Here is an easy method on how to install the latest version of Java for Ubuntu 6.10 : [http://www.ubuntuforums.org/showthread.php?t=262603](http://www.ubuntuforums.org/showthread.php?t=262603)

---

### Post by moffa on 2007-03-14
You need to install the java plugin for the browser.

The package name is sun-java5-plugin (or sun-java6-plugin)

---

### Post by Fidelio on 2007-03-14
Thanks. Not sure what to try first. Kobalt, when I pasted the command from that link into my terminal got an error message.

Moffa, how do I do that?
And doesn't the fact that frostwire won't run suggest that it's not just the fire-fox plugin?
Thanks

---

### Post by Fidelio on 2007-03-14
I already have sun-java5-plugin installed. BTW.
The error I got when I tried 'the easy way' is this; I copied 

```
deb http://download.tuxfamily.org/3v1deb/ 3v1n0
```

into my terminal, but got:

```
bash: deb: command not found
```

---

### Post by oneofth3m on 2007-03-14
Make sure that you copy the plugin to the firefox/plugin folder. I also had a similar problem and after a lot of searching finally learnt that we have to do this manually.

---

### Post by Fidelio on 2007-03-14
> **oneofth3m said:**
> Make sure that you copy the plugin to the firefox/plugin folder. I also had a similar problem and after a lot of searching finally learnt that we have to do this manually.

Oh, Ok. How do I do that? I have no idea where my firefox plugin folder, or my plugin are, and to be honest, havn't really got my head round ubuntu file management and structure.

---

### Post by Fidelio on 2007-03-15
Anyone help here?
I'm guessing this is a simple thing I've done wrong.

---

### Post by qpwoeiruty on 2007-03-15
Find out first where Java is installed (search for jre). For me this is /usr/lib/jre1.6.0
Then all you have to do is:
cp /usr/lib/jre1.6.0/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib/firefox/plugins/

Replace /usr/lib/jre1.6.0 with your java install path

Ed: Go to Places/Search for files.../Look in folder: Filesystem and type in jre. You could just search for libjavaplugin_oji as well.

---


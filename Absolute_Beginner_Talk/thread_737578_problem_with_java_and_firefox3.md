---
title: "problem with java and firefox3"
date: 2008-03-25
forum: Absolute Beginner Talk
---

### Post by jdlf on 2008-03-25
hello. I have **firefox 3**.0b3 and java 1.6.0_03-b05 **(java 6**). Can you help **link java to firefox **cause it hasn't done it automatically?

Thanks for all

jdlf

---

### Post by LowSky on 2008-03-25
mine is working fine, how did you install firefox 3/java

---

### Post by jdlf on 2008-03-25
can't remember, tried loads of ways... remember how you did it? I think the problem might be that i haven't been able to properly uninstall firefox 2, so there is still an entry that is read during java installation, so maybe java is linked to firefox 2...

---

### Post by jdlf on 2008-03-27
hello

look at this:   
Instructions to install java on firefox: 

**  1. Install Java Runtime Environment. (done already)**
   

2.** Make a symbolic link to libjavaplugin_oji.so in your Mozilla Plugins director**y. Use the copy located in the plugin/i386/ns7 directory of JRE 5.0 or later, or plugin/i386/ns610-gcc32 if you are using JRE 1.4.2. (don't know how to do this)

the installation procedure hasn't linked java to firefox 3 and it doesn't work, so i think y have to do step 2. [B]Can you explain me how??? What's a symbolic link??

[/B]

---

### Post by Achtung on 2008-03-27
**If you've just installed JRE 5.0 or later ...**
The gui way:
Open nautilus with root priviledges 
```
sudo nautilus
```
Go to the ../plugin/i386/ns7/ directory of JRE 5.0 (something like /usr/lib/jvm/java-version/jre/plugin ...)
Copy the libjavaplugin_oji.so 
Go to /usr/lib/mozilla/plugins/
Paste the libjavaplugin_oji.so 


**If you've just installed JRE 1.4.2**
The gui way:
Open nautilus with root priviledges 
```
sudo nautilus
```
Go to the ../plugin/i386/ns610-gcc32/ directory of JRE 1.4.2 (something like /usr/lib/jvm/java-version/jre/plugin ...)
Copy the libjavaplugin_oji.so 
Go to /usr/lib/mozilla/plugins/
Paste the libjavaplugin_oji.so 

In both cases, you can also use the cli way with the following command:
```
ln -s /path/to/real/file /path/to/non-existant/file
```
... where you need to modify the paths to the correct ones of course ;)

---

### Post by jdlf on 2008-03-27
thank you! problem solved.

---

### Post by jdlf on 2008-03-27
problem been solved

---

### Post by Joeb454 on 2008-03-27
Please don't make duplicate threads, it's against the forum CoC

---

### Post by Joeb454 on 2008-03-27
Duplicate thread found [here]("http://ubuntuforums.org/showthread.php?t=737578")

---

### Post by p_quarles on 2008-03-27
Threads merged. 

Joeb454 speaks the truth: duplicate threads are against the rules.

---


---
title: "Java making me insane"
date: 2006-05-23
forum: Absolute Beginner Talk
---

### Post by Ben Sprinkle on 2006-05-23
iv gotten java installed, works fine in konqueror but not firefox wtf!?! someone help

---

### Post by lukew on 2006-05-23
[QUOTE=Goat Spirit]iv gotten java installed, works fine in konqueror but not firefox wtf!?! someone help[/QUOTE]
Hi, You need to ensure that you have registered your java runtime environment against your firefox installation. I asumed if you do "java -version" or "which java" you get information detailing that you do have a jre installed?!?

Below is how to, but ensure that you subsitute your versions in....

Open a terminal 
Change to your Mozilla (or Mozilla Firefox) plugins directory 
Issue the following command: ln -s /usr/java/jre1.5.0_06/plugin/i386/ns7/libjavaplugin_oji.so ./libjavaplugin_oji.so

---

### Post by hotbrainz on 2006-05-23
hey dude,

Try to follow the instructions in this page. If there is further problems please ask:

[https://wiki.ubuntu.com/RestrictedFormats?highlight=%28formats%29%7C%28restricted%29]("https://wiki.ubuntu.com/RestrictedFormats?highlight=%28formats%29%7C%28restricted%29")

Hope this helps..

---

### Post by Ben Sprinkle on 2006-05-23
ok ill try this when i get home cuz im at school cheers:mrgreen:

---


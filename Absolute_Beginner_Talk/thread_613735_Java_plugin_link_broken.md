---
title: "Java plugin link broken"
date: 2007-11-15
forum: Absolute Beginner Talk
---

### Post by chaos.- on 2007-11-15
My link to my firefox plugin is broken and as soon as i right click on it it dissapears 

> java version "1.6.0_03"
Java(TM) SE Runtime Environment (build 1.6.0_03-b05)
Java HotSpot(TM) 64-Bit Server VM (build 1.6.0_03-b05, mixed mode)
chani@chani-desktop:~$ 


i have the current version of java installed it is in

/usr/lib/jvm/ia32-java-6-sun-1.6.0.03/jre/plugin/i386/ns7 ( the libjavaplugin_oji.so is installed here)

and my firefox java plugin is installed here

/usr/lib/firefox/plugins

my java plugin in my firefox folder has a broken link how do i set the link to where my libjavaplugin_oji.so is placed


any help would be great :)

---

### Post by chaos.- on 2007-11-15
anyone?

---

### Post by justsomedude on 2007-11-15
If the paths you posted are correct, you can try this:

```
sudo ln -sf /usr/lib/jvm/ia32-java-6-sun-1.6.0.03/jre/plugin/i386/ns7/libjavaplugin_oji.so /usr/lib/firefox/plugins/
```

This should create a new working link. :)

---

### Post by chaos.- on 2007-11-15
> /usr/lib/firefox/plugins/

souldnt this be pointed towards the acutal plugin itself?

---

### Post by justsomedude on 2007-11-15
No, the second path defines where the link is placed. We want to link the libjavaplugin_oji.so from your java folder to the firefox plugin folder.

---


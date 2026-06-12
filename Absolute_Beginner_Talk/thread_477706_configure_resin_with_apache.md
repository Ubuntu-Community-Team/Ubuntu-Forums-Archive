---
title: "configure resin with apache"
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by 77stan on 2007-06-18
Hello All,

I have a problem to confige resin with apache.
I just installed ubuntu the first time a few days ago.
I installed apache with: ```
sudo apt-get install apache2
```. That works fine.
I have also installed mysql and php with the apt-get command, everthing works.

So I get the resin 3.0 version and installed it. Now I don't know how to configure apache for the caucho module. I dont't find the mod.so module in the apache mods-available. How can I configure apache for that? 

I'm using ubuntu 7.0.4 and the jdk 1.6.0. On a further suse system I installed the apache manually and use the --enable-module=so option. Could I use the command with apt-get as
```
sudo apt-get install apache2 --enable-module=so
``` too?

Thanks for help....

---


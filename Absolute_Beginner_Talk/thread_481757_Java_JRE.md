---
title: "Java JRE"
date: 2007-06-22
forum: Absolute Beginner Talk
---

### Post by magnethead on 2007-06-22
ok, firefox couldn't download the java plugin and said to do so manually. I have jre-6u1-linux-i586.bin sitting on my desktop, but what do i do with it?

---

### Post by yabbadabbadont on 2007-06-22
You delete it and install the plugin using apt-get, aptitude, synaptic, ....  ;)

```
sudo apt-get install sun-java6-plugin
```

Edit: You will need to have the multiverse repository enabled.  In synaptic, Settings->Repositories, then enable universe and multiverse.  Ok the change and then hit the Reload button.  After that it should be available for installation.

---

### Post by NeoLithium on 2007-06-22
```

sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-fonts

```

You need to make sure you have the repositories enabled, if you don't, see here:
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_extra_repositories)

Hope this helps :)

---


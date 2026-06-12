---
title: "Java probs in XUbuntu"
date: 2008-02-21
forum: Absolute Beginner Talk
---

### Post by rockerphil on 2008-02-21
ok, i have just downloaded and installed the java runtime environment and it is now located in my home directory but i can't figure out how to get it to run in Firefox, my Firefox is located in my etc/firefox directory. i know that i need to make a link to the java runtime environment from my Firefox but can't seem to figure out exactly how to do so. plz bear in mind that i'm still pretty new at using Linux. any help would be greatly appreciated

---

### Post by FrozenFox on 2008-02-21
Assuming you installed java6,

sudo apt-get install sun-java6-plugin


You shouldn't have to do anything but install the plugin via synaptic or cmd line to install java in firefox.. assuming you didn't install firefox in some weird way.

---

### Post by jan quark on 2008-02-21
you mean you want to install a java plugin for firefox?

then run this
```

sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
```

---

### Post by rockerphil on 2008-02-21
much thanx Jan, got it fully installed and functional

---


---
title: "what is the wrong with me?"
date: 2006-05-27
forum: Absolute Beginner Talk
---

### Post by u04f061 on 2006-05-27
sudo apt-get install <package>
installs the package.but where to find package name. when i need something to install ,i come to this forum and post description of what i want to install.some nice people post the command which installs that thing. this solves my problem temporarily.but this requires me to post every time i need something.can't i become self dependent to search for my package in ubuntu.com?

i think where from these people come to know the package name?why can't i?what is the wrong with me?

---

### Post by ed_agamemnon on 2006-05-27
why don't you use synaptic?

---

### Post by Lord Illidan on 2006-05-27
[quote=u04f061]sudo apt-get install <package>
installs the package.but where to find package name. when i need something to install ,i come to this forum and post description of what i want to install.some nice people post the command which installs that thing. this solves my problem temporarily.but this requires me to post every time i need something.can't i become self dependent to search for my package in ubuntu.com?

i think where from these people come to know the package name?why can't i?what is the wrong with me?[/quote]

Use synaptic to search for the package. Search for its name and description, and generally you will get the right package. We know the names because either they are very frequently asked questions, or we look them up too.

---

### Post by 5-HT on 2006-05-27
If you don't want to use synaptic or browse packages.ubuntu.com, you can always use apt to search for packages:

```
 apt-cache search <string> 
``` 

See: 'man apt-get' (type in terminal) to read the manual for apt-get that will also link to other relevant apt manual pages (such as apt-cache).

HTH

---

### Post by mostwanted on 2006-05-27
This will set you up without the hassles:

[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by Nachtengel on 2006-05-27
If you'd like to use the command line for this, the command

```
sudo apt-cache search <partial_or_full_package_name_here>
```

The exercise of finding the name of the software you need is up to you :)

---

### Post by Minyaliel on 2006-05-27
Dear, there's nothing wrong with you, you just didn't know. You're not alone - I couldn't compile source code if I got a billion dollars for it :P Thanks goodness for the dapper package installer...

---


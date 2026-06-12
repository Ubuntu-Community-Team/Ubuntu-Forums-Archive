---
title: "How do you guys find out package names?"
date: 2007-06-22
forum: Absolute Beginner Talk
---

### Post by vegetable on 2007-06-22
I'll use Adobe Flash as an example. Someone who has never downloaded flash before would never guess that they need to type in **flashplugin-nonfree**. Is there a way in apt-get to make a quess, e.g. flash player. and then it will show package names that most resemble what you typed? I ask because i want to improve my shell skills, rather than always use synaptic.

thanks for looking!

---

### Post by wormser on 2007-06-22
To find a package name.

```
apt-cache search keywords
```

To find details about a package.

```
apt-cache show package_name
```

---

### Post by NeoLithium on 2007-06-22
Well, depending on if you know the partial names, you can use ```
sudo apt-cache search <name>
``` Common ones are always generally easier when compared to the long codec package names.

---

### Post by vegetable on 2007-06-22
Great, thanks! the apt-get man page didn't show the search keyword.. i wonder why! i never knew this command existed.

---

### Post by mengfei on 2007-06-22
What I also use is

[http://packages.ubuntu.com](http://packages.ubuntu.com)

If you felt like browsing around...

Hope that helps!

---

### Post by Najand on 2007-06-22
```

aptitude search <PACKAGENAME>

```
also gives you the current state of the package on yur computer too.

---

### Post by Songwind on 2007-06-22
I realize I won't be one of the cool kids by suggesting a GUI tool, but you can do this easily in both Synaptic and Adept.  They have pretty good search functions.

---

### Post by vegetable on 2007-06-22
awesome, thanks for all the suggestions! i'm going to use all these i'm sure.

---


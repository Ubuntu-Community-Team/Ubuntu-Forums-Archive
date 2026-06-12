---
title: "Proper Way of installing software (i.e. Opera) not found in Add/Remove"
date: 2007-05-18
forum: Absolute Beginner Talk
---

### Post by hanzj on 2007-05-18
Hello,
I would like to add a program to my system, but it isn't in Add/Remove. I know that I can install stuff via command line, but I don't want to have artificacts remain if I deceide to remove/uninstall the program later on. W
What's the proper way to install software? (if you suggest apt-get OR aptitude, please tell me why you didn't suggest the other).
Specifically, what's the proper way to install Opera browser?

---

### Post by Najand on 2007-05-18
Opera is not in the official repositories. So unless you add it to your apt source (/etc/apt/sources.list) you cannot install it using apt-get/aptitute/synaptic package managers. Well,if you have added it to your sources.list then you can add it using synaptic package manager with a nice GUI and you don't need to use commands in the terminal.

---

### Post by bobplano on 2007-05-18
have you checked synaptic? i find that there is more software available in synaptic. there are .deb packages at their site if you can't find it in the repos. if it is and you want to use the terminal aptitude cleans up dependencies better, and i don't know any disadvantages so far.

---

### Post by hanzj on 2007-05-18
I have checked "add/remove". If that's the same thing as synaptic, then yes, I have checked synaptic, and have not found opera. If "add/remove" is not synaptic, then, wow. I think people should know that. Both programs look so much alike.

---

### Post by hanzj on 2007-05-18
Yes, I know of the debs, I just didn't want to have a messy install/uninstall.

---

### Post by hanzj on 2007-05-18
I just don't want my uninstall to not COMPLETELY remove  EVERY change/ addition that install has done.

---

### Post by aysiu on 2007-05-18
Download the .deb from the Opera website and then double-click it.

More details here:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by Atomic Dog on 2007-05-18
Automatix will make installing Opera a snap.  You can get it here:  [http://www.getautomatix.com/](http://www.getautomatix.com/)

Many people here use Automatic.

---

### Post by hanzj on 2007-05-18
Najand,
Is adding to .list not more difficult than just getting the deb? If I add to the .list, will that mean that when opera comes out with a new version, I can get latest one in apt-get/aptitude/synaptic repos?

---

### Post by aysiu on 2007-05-18
> **Atomic Dog said:**
> Automatix will make installing Opera a snap.  You can get it here:  [http://www.getautomatix.com/](http://www.getautomatix.com/)

Many people here use Automatic.
Why would you install Automatix to install Opera?

**Automatix**:
1. Go to the Automatix website
2. Find the download page
3. Download the Automatix .deb
4. Double-click the .deb to install Automatix
5. Find Automatix in the menu
6. Find Opera in the list of programs to install via Automatix
7. Wait for Automatix to apply changes

**no Automatix**
1. Go to the Opera website
2. Follow the *Download Opera for Linux* link
3. Download the Ubuntu .deb
4. Double-click the .deb to install Opera

Seven steps. Four steps. I know which method I'd pick.

---

### Post by aysiu on 2007-05-18
> **hanzj said:**
> Najand,
Is adding to .list not more difficult than just getting the deb? If I add to the .list, will that mean that when opera comes out with a new version, I can get latest one in apt-get/aptitude/synaptic repos?
Yes. 

The .deb will just install the current version of Opera.

Adding the Opera repository to the /etc/apt/sources.list will keep you up to date when a new version of Opera comes out.

---

### Post by Najand on 2007-05-18
To use opera repository, you should do the following:
1. Open a terminal.
2. Open a terminal
3. Type:
```

gksu gedit /etc/apt/sources.list

```
4. Add:
> deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main
to the end of sources.list and save it.
5. Try Synaptic to find Opera and install it.

---

### Post by Atomic Dog on 2007-05-18
> **aysiu said:**
> Why would you install Automatix to install Opera?

**Automatix**:
1. Go to the Automatix website
2. Find the download page
3. Download the Automatix .deb
4. Double-click the .deb to install Automatix
5. Find Automatix in the menu
6. Find Opera in the list of programs to install via Automatix
7. Wait for Automatix to apply changes

**no Automatix**
1. Go to the Opera website
2. Follow the *Download Opera for Linux* link
3. Download the Ubuntu .deb
4. Double-click the .deb to install Opera

Seven steps. Four steps. I know which method I'd pick.

Well I'm just thinking of all the other cool stuff Automatix makes easy to install.  Don't hate on me!

---

### Post by hanzj on 2007-05-18
You (plural) are so helpful. So what exactly do i add to the sources.list, and how do I add? 
TY. TY. TY 8-)

---

### Post by hanzj on 2007-05-18
> **Najand said:**
> 
3. Type:
```

gksu gedit /etc/apt/sources.list

```4. Add: to the end of sources.list and save it.
5. Try Synaptic to find Opera and install it.

Great, clear instructions. Thank you.
I've done as you said but,
Question 1) For real newbies, is there no graphical way of adding to sources list?

Q2) I went to add/remove and searched for opera, but couldn't find it. I also went to synaptic and couldn't find it. Am I doing something wrong?

Q3) Is add/remove different from Synaptic? If so, how are they different?

---

### Post by Najand on 2007-05-18
Well, seems they have removed it from canonical repositroies:
Download it from:
[http://www.opera.com/download/](http://www.opera.com/download/)
And double click on it. It is a "deb" package, so it can be easily removed from any package manager in Ubuntu.

---

### Post by hanzj on 2007-05-18
Does this mean that there is no way to just click "Update" to get the latest version of opera? Does this mean I have to get the latest deb everytime there is a newer version of opera?

Thanks.

---

### Post by Smu on 2007-05-18
I would go with automatix. It's easy and efficient and adds quite a few new repositories to your source list. With Automatix you'll be able to install codecs, flashplayer, opera, DVD shrink, gnome tweaks etc. with one click! And all the installed software will update with the rest of the system...

---

### Post by zvacet on 2007-05-18
Once when you download and install Opera you will see that Opera have **chek for updates **option.If you click on that option and it say to you that new version is available you will just download it.So,download and install it and enjoy.

---


---
title: "Fresh Install; No Updates"
date: 2008-01-02
forum: Absolute Beginner Talk
---

### Post by Kymac on 2008-01-02
I just installed Ubuntu 7.10 on an old DELL Desktop, as well as my lenovo notebook (after messing up the partitions).

When I installed on the DELL, there were no updates after the install, also, flash doesn't seem to work, even after installing/trying both the gnash and adobe plugins.

With the notebook, I put in the live cd, and they screen would go blank after trying to run it.  I had to go on the live cd in safe graphics mode in order to get to it, and I installed it.  I was not connect to the internet during installation, and it told me it couldn't get ubuntu.security or something like that.  Anyway, I rebooted, and everything seems to be fine, but, again, there were no updates, even after I connected to the internet.  Also, I tried to install the flash plugin, and it told me it couldn't find mozilla_plugin_flash, or whatever that is (aka: it isn't in the synaptic package manager).

I'm not an expert in computers, and was curious if anyone heard of a similar problem, or could tell me how I could go about fixing this.  Thank You.

---

### Post by snickers295 on 2008-01-02
try typing sudo apt-get update and then check for updates.

---

### Post by sumguy231 on 2008-01-02
For updates, go to a terminal and type:
```
sudo apt-get update
```
and see if any updates appear. 

The flash plugin is called flashplugin-nonfree, and you'll need to make sure you have the multiverse repository enabled, which you can do from Synaptic. I would give you more details but I use KDE rather than Gnome so I don't know where everything is located. 

Another way to get that done is to run 'gksu gedit /etc/apt/sources.list' and remove the # from the front of the lines that looks like this;
```
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
```

Hope that helps.

Edit: Beaten on question #1.

---

### Post by g2g591 on 2008-01-02
if your sources.list file is mostly empty, like if theres only a line about the install cd, you should take the attatched sources.list.txt and replace the installed version with it (be sure to take off the .txt, had to add that in order to attach it)

---

### Post by Kymac on 2008-01-03
I'm sorry, but how do I check/replace my sources.list file?

Also, is there a reason behind the fact it won't let me use ubuntu off the live CD?

---


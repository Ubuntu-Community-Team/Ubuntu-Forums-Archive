---
title: "Update and Uninstall"
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by Madmoose on 2007-03-11
Evening, 

 I have three questions today:


> I have the Nvidia driver working perfectly, but I was wondering how I know theres it has the latest driver, and how do I go about getting it? Does it automatically update with they system updates, or do I have to do it manually? 

I followed this to install the driver on this computer about 2 months ago:
[http://albertomilone.com/latest_nvidia_udsf_edgy.html#METHOD_1](http://albertomilone.com/latest_nvidia_udsf_edgy.html#METHOD_1)

> How do you unintall something you installed with wine? 


> I followed this tatorial, but I think I might have messed up. 

[http://www.ubuntuforums.org/showthread.php?t=278206&highlight=Sunbird](http://www.ubuntuforums.org/showthread.php?t=278206&highlight=Sunbird)

Now I want to uninstall it, so that I can try it again. Yet, I didn't' install it through the synaptic or the add/remove. Can you tell me how to install it? Is there a simple command, or am I going to have to go into it by hand?   

---

### Post by Kateikyoushi on 2007-03-11
If you installed the driver as the method 1 instructions say it will be updated if new upgrades are avaible.

You can use "wine uninstaller" enter this to the terminal to uninstall what you installed with wine.

You could remove the directories, files you created but it is unnecessary because if you repeat the steps those get overwritten.

There is no simple command to remove programs you install by hand.

---

### Post by Madmoose on 2007-03-12
> If you installed the driver as the method 1 instructions say it will be updated if new upgrades are avaible.

Ah. Good to know!

> You can use "wine uninstaller" enter this to the terminal to uninstall what you installed with wine.

Worked! Thanks. I'll have to remember this.

> 
You could remove the directories, files you created but it is unnecessary because if you repeat the steps those get overwritten.


Hmmm. I repeated the steps, and I even get the Sunbird logo in the "Office" part of applications. Yet, when I click on it to start it a window pops up that says sunbird on it, but then it closes. I've posted this in that thread,  but I've yet  to have an answer. 

> 
There is no simple command to remove programs you install by hand.

When is anything simple? :guitar:

---

### Post by Kateikyoushi on 2007-03-12
Well if you install something with synaptic or aptitude removing them is just this:
```
sudo aptitude remove package
```

that is as simple as can get without letting my pc read my mind.

---

### Post by Madmoose on 2007-03-13
> **Kateikyoushi said:**
> Well if you install something with synaptic or aptitude removing them is just this:
```
sudo aptitude remove package
```

that is as simple as can get without letting my pc read my mind.

Hey, Thanks!


moose

---


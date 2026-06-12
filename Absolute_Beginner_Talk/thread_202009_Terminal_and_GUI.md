---
title: "Terminal and GUI"
date: 2006-06-22
forum: Absolute Beginner Talk
---

### Post by gdog05 on 2006-06-22
Hey everyone,

I'm looking for a way to set terminal to open automatically inside the Update windows specifically. If they open across the board for many menus, that's fine too. My problem is, the machine I have Ubuntu loaded on is really slow. When the window opens, and I click on the Terminal drop down arrow, it takes forever to open the Terminal. Usually so long that it never shows what is going on within Terminal. I think this would be a great way to learn terminal commands, but never being able to see them doesn't really help me. I think if it was set to automatically expand the Terminal when a window is opened, it might be enough to allow me to see what is going on. I thank you guys for all the stuff I've learned in here, and I will thank anyone that can help me on this in advance.

GDog

---

### Post by aysiu on 2006-06-22
How about just forgetting about the update windows altogether? Just open a terminal and type ```
sudo aptitude update
sudo aptitude dist-upgrade
```

---

### Post by Zikes on 2006-06-22
I'm not sure how to do that, but an alternative might be to use Synaptic to find the package names, then use "sudo apt-get install package_name" to install the package.  That should automatically grab dependencies and install them the same as Synaptic does, but you'll be able to see all the terminal output right from the start.

Edit: aysiu beat me to it, but while we're on the subject there's one thing I'm not really clear on.  What's the difference between aptitude and apt-get?  At first I thought they were basically the same command, and I've seen them used interchangeably at times, but occasionally I'll see a howto that says it's crucial to use one or the other when installing certain packages.

---

### Post by gdog05 on 2006-06-22
I've actually been using sudo apt-get update then "upgrade to get my updates, but there are a couple that the automatic updater says to install, but crashes (because of resources I'm sure). When I do apt-get update, it says nothing new is needed. Will dist-upgrade get me more options aysui?

Thanks Zikes, I think that is the route I will go. I was more curious if this was possible than anything. If it was, I wanted to see if it would help. Thanks for the suggestions, both of you. I didn't realize this forum was THAT quick.

GDog

---

### Post by aysiu on 2006-06-22
*aptitude* remembers dependencies and will remove them along with the package (as long as no other package is using those dependencies.

*apt-get* will forget the dependencies and uninstall only what you explicitly ask it to uninstall.

---

### Post by gdog05 on 2006-06-22
Ok, that makes sense. Thank you very much.  *------> Leaps ahead another notch.*

---

### Post by aysiu on 2006-06-22
To do a little test to see how it works, try these commands in this order: ```
sudo aptitude update
sudo aptitude install kword
sudo aptitude remove kword
sudo apt-get update
sudo apt-get install kword
sudo apt-get remove kword
```

---


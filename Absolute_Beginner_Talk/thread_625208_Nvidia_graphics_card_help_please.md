---
title: "Nvidia graphics card help please"
date: 2007-11-27
forum: Absolute Beginner Talk
---

### Post by pankirk on 2007-11-27
hello, I recently installed ubuntu linux 7.10 (first time ever using linux at all) and i like it, but the only thing I can not install is my drivers for my graphics card (nvidia 8800 GTS) and i tried Envy, envy just gives me this error 'error dependency is not satisfiable xserver-xorg-dev" and then when I try to do it the other way with terminal it says it can not open it. so basically I was hoping that some nice person can please tell me all of the steps to getting my drivers working. Like everything to download before I download envy and everything to do after. Basically a short tutorial with everything in it. Please I really would like to be able to set my resolution to 1680 x 1050 and use all of the neat linux features!

---

### Post by Inxsible on 2007-11-27
This link is for Feisty, but it might work for Gutsy.

[http://www.ubuntugeek.com/how-to-fix-nvidia-acceleration-in-feisty-nvidia-8800-and-legacy-users.html](http://www.ubuntugeek.com/how-to-fix-nvidia-acceleration-in-feisty-nvidia-8800-and-legacy-users.html)

---

### Post by stoodleysnow on 2007-11-27
So you've tried the restricted drivers manager?

---

### Post by Grey Box on 2007-11-27
For a start you could try [http://www.ubuntuguide.org]("http://www.ubuntuguide.org") which has useful guides for all sorts of stuff. 

But for the nvidia card issue, you need 'restricted' drivers to enable its full potential. System -> Administration - Restricted Drivers Manager, if you're using the standard Ubuntu. You'll need to enter your password to get in there, but it should report if you need any extra drivers or not.

Ubuntu doesn't always install them straight off, because the drivers are not opensource and don't have an open license (eg: GPL), but that's a long story.

---

### Post by pankirk on 2007-11-27
I dont know what I have tried, because I dont really know what anything is. Linux is a completely new OS for me. I did "system>administration>restricted drivers" and in there there was something about nvidia drivers and I clicked "use" or maybe it was "install" and then it said that "nvidia-glx-new" is not found or whatever. So then I tried to use Envy and I got an error that "xserver-xorg-dev" is missing or something.

---

### Post by Inxsible on 2007-11-27
> **pankirk said:**
> I dont know what I have tried, because I dont really know what anything is. Linux is a completely new OS for me. I did "system>administration>restricted drivers" and in there there was something about nvidia drivers and I clicked "use" or maybe it was "install" and then it said that "nvidia-glx-new" is not found or whatever. So then I tried to use Envy and I got an error that "xserver-xorg-dev" is missing or something.If you will tell us the correct error messages that you get, we might be able to better help you.

---

### Post by pankirk on 2007-11-27
Ah yes, I bet it would be a better help if i show the actual messages instead of my gibberish.

Ok 

this is what it says when I try to enable "restricted drivers"
[img]http://img406.imageshack.us/img406/6271/screenshotho0.png[/img]

And here is what it says when I try to install envy
[img]http://img405.imageshack.us/img405/8923/screenshot1ti5.png[/img]

---

### Post by Inxsible on 2007-11-27
I don't use Envy.. So I am going to help you out with the Restricted Driver Manager thing.

Go to System>>Administration>>Software Sources. Enable the Universe and Multiverse repositories. 

Then go back to the Restricted Driver Manager and try to enable it agian.

---

### Post by pankirk on 2007-11-27
I did that and When I went to restricted drivers is told me the same problem.

---

### Post by Inxsible on 2007-11-27
> **pankirk said:**
> I did that and When I went to restricted drivers is told me the same problem.you gotta reboot once you enable. Also, did you reload the sources after enabling the universe and multiverse ?
open a terminal and type in ```
sudo aptitude update && sudo aptitude upgrade
```

---

### Post by pankirk on 2007-11-27
Yes I reloaded the sources, and some stuff downloaded, I guess it was updating. I havent rebooted yet, so I will do that now and report back once I have rebooted.

Oh I didnt see I needed to use terminal for that. Ok I entered the code you said to do and it says this.

> W: The "upgrade" command is deprecated; use "safe-upgrade" instead.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done 

Im not sure if anything happened? I will try to do restricted drivers now.

---

### Post by Grey Box on 2007-11-27
If you want to install extra things, you can go to System -> Administration -> Synaptic Package Manager, which also requires your password to get in.

There you can search for things and you might well find the missing packages that you mentioned. Best thing to do is when you come accross stuff like that, write it down, then you can search for it exactly and install it.

---

### Post by pankirk on 2007-11-27
> **Grey Box said:**
> If you want to install extra things, you can go to System -> Administration -> Synaptic Package Manager, which also requires your password to get in.

There you can search for things and you might well find the missing packages that you mentioned. Best thing to do is when you come accross stuff like that, write it down, then you can search for it exactly and install it.

I did that and I searched for "xserver-xorg-dev" and I could not find it, I also searched for "nvidia-glx-new" and I could not find that "package" either.

---

### Post by pankirk on 2007-11-27
Ok, now I rebooted and Did everything. And still no luck. Im lost. It says that the nvidia-glx-new package thins is not enabled, so aparently I have it, but its not enabled. So where can I go to enable it?

---


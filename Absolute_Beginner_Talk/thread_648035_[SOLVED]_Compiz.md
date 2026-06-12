---
title: "[SOLVED] Compiz"
date: 2007-12-23
forum: Absolute Beginner Talk
---

### Post by thenailedone on 2007-12-23
Hello...

I installed the latest nvidia drivers on Gutsy (no internet via Linux so I couldn't use Synaptic)...

I know the drivers are working ok as I get the nvidia splash screen and the nvidia x-server app works ok (can even OC my gfx now)...

My problem is I cannot enable the desktop effects.  They still want to enable the restricted drivers and when I try it says the nvidia-glx-new (or something like that) is missing.  

I then tried to run compiz in a terminal and now my desktop effects are on normal (which looks much better) but I stil can't enable enhanced!?

When running compiz it gives the message that XGL wasn't found...?  Any assistance would be greatly appreciated...

(Please note I have a similar thread in another section and after a couple of days no repsonse... so I decided to try here as I am a n00b still)...


Cheers

---

### Post by santaslittlehelper on 2007-12-23
Hi, first of, if you do get a working connection at some time, remove the current drivers you installed from the nvidia site before using the Restricted Driver Manager or Visual Effects.

As for now you can start compiz the following way -
[http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty](http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty)
- basically.

From a terminal:
```
sudo nvidia-xconfig --add-argb-glx-visuals -d 24
```
Adds Option "AddARGBGLXVisuals" "True" to you're xorg.conf.

```
gedit compiz-start
```
Paste the following:
> #!/bin/bash
compiz --replace &
Save it in you're home folder.

```
chmod +x start-compiz
```
To make the script executable.

```
sudo aptitude install compizconfig-settings-manager
```
Should give you - System > Preferences > Advanced Desktop Effects Settings 

Add start-compiz to System > Preferences > Sessions > Startup Programs 

Hope that helps.

---

### Post by thenailedone on 2007-12-25
Hello santaslittlehelper...

I was so hopeful this was going to work but I get the following output when I run: 

```
thenailedone@eclipse:~$ sudo aptitude install compizconfig-settings-manager 
Reading package lists... Done 
Building dependency tree        
Reading state information... Done 
Reading extended state information       
Initializing package states... Done 
Building tag database... Done       
[B]Couldn't find any package whose name or description matched "compizconfig-settings-manager" 
No packages will be installed, upgraded, or removed. [/B]
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded. 
Need to get 0B of archives. After unpacking 0B will be used. 
Reading package lists... Done 
Building dependency tree        
Reading state information... Done 
Reading extended state information       
Initializing package states... Done 
Building tag database... Done       
thenailedone@eclipse:~$  
```

What now... :(

---

### Post by John.Michael.Kane on 2007-12-25
First off you are going to have a hard time installing anything on that machine without a working internet connection. So you may want to post a thread for getting that working.

For the question at hand.
You have to make sure all the repo's are uncommented in your sources.list file. Which is explained how to  go about doing here [http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)
After which you can try this
```
gksudo aptitude install compizconfig-settings-manager
```

However. you will not be able to install this file without a working net connection on the machine you want to use compizconfig-settings-manager.

---

### Post by thenailedone on 2007-12-25
> **John.Michael.Kane said:**
> First off you are going to have a hard time installing anything on that machine without a working internet connection. So you may want to post a thread for getting that working.

For the question at hand.
You have to make sure all the repo's are uncommented in your sources.list file. Which is explained how to  go about doing here [http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)
After which you can try this
```
gksudo aptitude install compizconfig-settings-manager
```

However. you will not be able to install this file without a working net connection on the machine you want to use compizconfig-settings-manager.

Hi...

Thanks for the advice and I have a link to my woes on getting a working net connection in my signature... I do have a internet when I boot XP... any info on downloading the packages that way like I did to get the nvidia drivers?



Cheers
Neil

---

### Post by John.Michael.Kane on 2007-12-25
> **thenailedone said:**
> Hi...

Thanks for the advice and I have a link to my woes on getting a working net connection in my signature... I do have a internet when I boot XP... any info on downloading the packages that way like I did to get the nvidia drivers?



Cheers
Neil
Since you don't have internet working under Linux your basically stuck downloading the package from below, As well as all dependencies it calls for. 
[compizconfig-settings-manager]("http://packages.ubuntu.com/gutsy/x11/compizconfig-settings-manager")

You really should try to get internet working under Ubuntu, As it would ease your transition, and testing of the OS.

---

### Post by thenailedone on 2007-12-27
> **John.Michael.Kane said:**
> Since you don't have internet working under Linux your basically stuck downloading the package from below, As well as all dependencies it calls for. 
[compizconfig-settings-manager]("http://packages.ubuntu.com/gutsy/x11/compizconfig-settings-manager")

You really should try to get internet working under Ubuntu, As it would ease your transition, and testing of the OS.

I finally got some Compiz goodness going today... just needed compizconfig-settings-manager_0.5.2+git20070912-0ubuntu1_all.deb and python-compizconfig_0.5.2+git20070912-0ubuntu1_amd64.deb and bob was my uncle... I got the groovy cube going and some wobbly windows... LOL (some of the custom settings I enabled didn't seem to do much though... maybe their is another problem... Water effects and fire on the desktop didn't seem to do much...)

Oh well... I am still chuffed :)  Thanks to all assistance... it was greatly appreciated! :KS

---


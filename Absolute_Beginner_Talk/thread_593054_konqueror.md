---
title: "konqueror"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by limac on 2007-10-26
Hi,

I am using knoqueror and am in the trial process of installing the adobe flashplayer and to install it they are saying to:

In terminal, navigate to this directory and type ./flashplayer-installer to run the installer. Click Enter. The installer will instruct you to shut down your browser(s).

What do they mean by saying to 
navigate to this directory and type ./flashplayer-installer to run.
Please explain.


thnx

---

### Post by philinux on 2007-10-26
Your post is hard to understand

---

### Post by llamakc on 2007-10-26
They mean to change directory to it. In the terminal you do this with the "cd" command. 

How knowledgeable are you on basic commands in the console or terminal? Perhaps a tutorial would help you get some of that basic knowledge digested?

---

### Post by kerry_s on 2007-10-26
> **limac said:**
> Hi,

I am using knoqueror and am in the trial process of installing the adobe flashplayer and to install it they are saying to:

In terminal, navigate to this directory and type ./flashplayer-installer to run the installer. Click Enter. The installer will instruct you to shut down your browser(s).

What do they mean by saying to 
navigate to this directory and type ./flashplayer-installer to run.
Please explain.


thnx


why are you trying to manually install?
just> sudo apt-get install flashplugin-nonfree < in a terminal
or you can use synaptic to install it if you prefer the gui way.

---

### Post by limac on 2007-10-26
> **llamakc said:**
> They mean to change directory to it. In the terminal you do this with the "cd" command. 

How knowledgeable are you on basic commands in the console or terminal? Perhaps a tutorial would help you get some of that basic knowledge digested?

Yeah i guess a tutorial on commands would really help me. But where in the world can I gather more experience about commands?

So i basically need to type in this command, "cd ./flashplayer-installer" in the terminal?

After i gather a basic knowledge about commands I problably wont have to be on the forum questioning all the times. So what would actually be a good source of learning commands?

---

### Post by llamakc on 2007-10-26
You should learn to use Google or other search engines.

[http://www.linuxcommand.org/](http://www.linuxcommand.org/)

---

### Post by Maestro23 on 2007-10-26
> **llamakc said:**
> You should learn to use Google or other search engines.

[http://www.linuxcommand.org/](http://www.linuxcommand.org/)

Add one more:

[http://www.tuxfiles.org/](http://www.tuxfiles.org/)

---

### Post by Frak on 2007-10-26
I'm guessing you are using Kubuntu, so click the link below to automatically install flash for konqueror.

[apt:flashplugin-nonfree]("apt:flashplugin-nonfree")

---

### Post by limac on 2007-10-26
so about the directory one,

What command should i put in?

After doing this i'll check out the websites for basic command knowledge.

---

### Post by limac on 2007-10-26
> **Frak said:**
> I'm guessing you are using Kubuntu, so click the link below to automatically install flash for konqueror.

[apt:flashplugin-nonfree]("apt:flashplugin-nonfree")

No I am using ubuntu

---

### Post by Maestro23 on 2007-10-26
> **limac said:**
> so about the directory one,

What command should i put in?

After doing this i'll check out the websites for basic command knowledge.

Did Frak's link not work for you?

*cd = change directory

---

### Post by Frak on 2007-10-26
> **limac said:**
> No I am using ubuntu
Should work anyway, it really doesn't matter what you use.

---

### Post by limac on 2007-10-26
so what should the entire command be?

only "cd" or something in addition to that?

Thnx

---

### Post by limac on 2007-10-26
> **Frak said:**
> I'm guessing you are using Kubuntu, so click the link below to automatically install flash for konqueror.

[apt:flashplugin-nonfree]("apt:flashplugin-nonfree")

says protocol not supported.

---

### Post by Frak on 2007-10-26
> **limac said:**
> says protocol not supported.
sorry, forgot you're using Konqueror, run in the terminal

```
sudo aptitude install flashplugin-nonfree
```

---

### Post by Maestro23 on 2007-10-26
> **limac said:**
> says protocol not supported.

Have you tried getting it from the repositories as suggested earlier?  In a terminal, type the following commands, and post back what happens.

> sudo apt-get install flashplugin-nonfree

---

### Post by Frak on 2007-10-26
It's recommended you use the repositories so you always get the latest version instead of having to manually check and reinstall repetitively.

---

### Post by limac on 2007-10-26
here's the reply

ron@Apple-Macintosh:~$ sudo apt-get install flashplugin-nonfree
[sudo] password for ron:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
flashplugin-nonfree is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
ron@Apple-Macintosh:~$ 

i remember installing those plugins for firefox. and i just started konqueror.

---

### Post by Frak on 2007-10-26
try
```
sudo dpkg-reconfigure flashplugin-nonfree
```

---

### Post by kerry_s on 2007-10-26
i think i know what you did, you installed konqueror, but you didn't install the plugin for plugins.

sudo apt-get install konqueror-nsplugins

you should use synaptic the gui package manager, it gives you a better view of what's going on.

---

### Post by limac on 2007-10-26
it says it's installed but if i try to run any videos they are still showing the message that i have to download the flashplayer in order to play the clip.

??

---

### Post by limac on 2007-10-26
> **kerry_s said:**
> i think i know what you did, you installed konqueror, but you didn't install the plugin for plugins.

sudo apt-get install konqueror-nsplugins

you should use synaptic the gui package manager, it gives you a better view of what's going on.

this is what it says:

ron@Apple-Macintosh:~$ sudo apt-get install konqueror-nsplugins
[sudo] password for ron:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
konqueror-nsplugins is already the newest version.
konqueror-nsplugins set to manual installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
ron@Apple-Macintosh:~$

---

### Post by kerry_s on 2007-10-26
so then go into konqueror settings> plugins> search to activate any plugins you have installed.

---

### Post by limac on 2007-10-26
where is konqueror settings?

---

### Post by Frak on 2007-10-26
> **kerry_s said:**
> i think i know what you did, you installed konqueror, but you didn't install the plugin for plugins.

sudo apt-get install konqueror-nsplugins

you should use synaptic the gui package manager, it gives you a better view of what's going on.
Don't mind me asking kerry_s, but are you using Ubuntu-lite?

---

### Post by Frak on 2007-10-26
> **limac said:**
> where is konqueror settings?
Tools->Configure Konqueror

Also, if you follow the dialogue, it should install Flash for you.

---

### Post by kerry_s on 2007-10-26
> **Frak said:**
> Don't mind me asking kerry_s, but are you using Ubuntu-lite?

no, i use jwm. i do a base debian install and build up from there. my setup is built to be fast and low resource. i only have 450mhz 256ram.

---

### Post by Frak on 2007-10-26
> **kerry_s said:**
> no, i use jwm. i do a base debian install and build up from there. my setup is built to be fast and low resource. i only have 450mhz 256ram.
You have to be my hero on resource management :D

---

### Post by Maestro23 on 2007-10-26
> **kerry_s said:**
> no, i use jwm. i do a base debian install and build up from there. my setup is built to be fast and low resource. i only have 450mhz 256ram.

Lean and mean. Not too much overhead.:)

---

### Post by kerry_s on 2007-10-26
thanks guy's, i only just installed yesterday so it's work in progress.

---


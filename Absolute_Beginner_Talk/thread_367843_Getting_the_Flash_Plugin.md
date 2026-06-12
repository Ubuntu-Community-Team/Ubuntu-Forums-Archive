---
title: "Getting the Flash Plugin"
date: 2007-02-22
forum: Absolute Beginner Talk
---

### Post by jtrimble on 2007-02-22
Greetings, 

I am trying to install the flash plugin so that I can watch videos on YouTube. 

I have gone to this website, and followed the instructions:

[URL="https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/web-browsing.html"]
https://help.ubuntu.com/6.10/ubuntu/desktopguide/C/web-browsing.html[/URL]

and have turned on both the 'Universe' and 'Multiverse' options under SYSTEM - Admin - Software Properties

however, when I run the command sudo update-flashplugin in my terminal, I get this:

josh@josh-laptop:~$ sudo update-flashplugin
Password:
sudo: update-flashplugin: command not found
josh@josh-laptop:~$

Any help would be great! Thanks!

---

### Post by Maestro23 on 2007-02-22
Make it easy on yourself.  Get it via synaptic.

Open Synaptic and search for: flashplugin-nonfree

or

Open terminal:

sudo apt-get install flashplugin-nonfree

---

### Post by jtrimble on 2007-02-22
This is what I got:

josh@josh-laptop:~$
josh@josh-laptop:~$ sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package flashplugin-nonfree
josh@josh-laptop:~$

---

### Post by AtrejuT on 2007-02-22
if you enabled the repositories you probably have to do
```

sudo apt-get update
sudo apt-get install flashplugin-nonfree

```

atreju

---

### Post by jordanmthomas on 2007-02-22
Have you forgotten to do 
```
sudo apt-get update
```
after enabling multiverse?

Personally, I'd go with flash 9 instead of 7
[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

**edit**  woopsy, beaten!

---

### Post by jtrimble on 2007-02-22
Also, when I go to the Add/Remove option under Applications, and try to install the plugin that way, I get this message:

The application may not be supported by your system architecture.

---

### Post by jtrimble on 2007-02-22
> **AtrejuT said:**
> if you enabled the repositories you probably have to do
```

sudo apt-get update
sudo apt-get install flashplugin-nonfree

```

atreju

I still get this error message in the end: E: Couldn't find package flashplugin-nonfree


could it be that i am running a 64 bit verson of Ubuntu? I thought I remember reading on the flash website that it doesnt support it.

---

### Post by jordanmthomas on 2007-02-22
here's a thread that might help since you're on 64 bit
[http://www.ubuntuforums.org/showthread.php?p=1174435](http://www.ubuntuforums.org/showthread.php?p=1174435)

You have to install 32 bit firefox and run flash in it.

---

### Post by arkangel on 2007-02-22
first install firefox  in 32 bits  then go here   
[[URL="http://www.adobe.com/shockwave/download/index.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux&P3_Browser_Version=Netscape4"]http://www.adobe.com/shockwave/download/index.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux&P3_Browser_Version=Netscape4]([URL="http://www.adobe.com/shockwave/download/index.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux&P3_Browser_Version=Netscape4"]http://www.adobe.com/shockwave/download/index.cgi?P1_Prod_Version=ShockwaveFlash&P2_Platform=Linux&P3_Browser_Version=Netscape4)[/url

donwload it an  untar  it  then run ,  (the tgz version) 
#sudo ./flashplayer-installer 

it will ask where is firefox or mozilla 

normally is in /usr/lib/firefox

and  that was

follow the link given in the previous post

---

### Post by smiffo on 2007-02-26
Possibly a very stupid question but how do I know if I'm running 32bit or 64? I'm having trouble sorting out flash but don't know what I'm running! Any help appreciated. Thanks.

---


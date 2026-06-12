---
title: "Firefox Flash Player 9 install issues"
date: 2007-12-11
forum: Absolute Beginner Talk
---

### Post by unknown user on 2007-12-11
The other night I tried to access a website which needed me to have flash player 9 installed.  I followed the links and downloaded a tar.gz file on my desktop.  I then followed the instructions from the download site below:

[COLOR="Red"][b]1.	Download Flash Player 9.0. 
2.	Decompress it, then copy libflashplayer.so to your Mozilla plugins directory and flashplayer.xpt to your Mozilla components directory. [/COLOR][/b]

However, when I tried to place the libflashplayer.so into the Mozilla plugins directory (via copy and past & drag and drop), it told me that I didn’t have the right permissions to do this.  Strange as I thought my account was the admin one for the laptop.  I didn’t even get round to doing the second part of the instructions.

Can anyone advise me how to get around this or if there is an easier way to install Flash Player on my Firefox so that I can access the site that I want to.

Cheers,

---

### Post by flamelab on 2007-12-11
You are not permitted to change the folders content as normal user in dirs higher than /home/your-name .
There are two ways :

1)Through console :

```
sudo -s -H
```

then

```
cp /usr/share/firefox/plugins
```
 (I don't really remember the directory , you enter the proper one from the instructions )

2)Through GUI :

sudo nautilus .

But in the second case you have to be carefull because you may change and delete EVERYTHING , EVERYWHERE . Be carefull.

And report please after you try that .

---

### Post by ajgreeny on 2007-12-11
>  2)Through GUI :

sudo nautilus .Actually, it's gksudo nautilus. 

But before that, have you tried installing with apt-get or synaptic?  Add the universe and multiverse repos and use that method for **flashplugin-nonfree**.  It is so much simpler than downloading it yourself.

---

### Post by unknown user on 2007-12-11
I have been able to place the .so file in the location by using this line gksudo nautilus, but no have no idea where to get this file from -  flashplayer.xpt

Why the hell is this not a simple task, all I want to do is install a program......

---

### Post by unknown user on 2007-12-11
Where am I going wrong?
I followed the instructions of this site ([http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)) and got the following message:
With the download on my desktop:

unknown@unknown-laptop:~$ sudo apt-get install flashplayer-installer
[sudo] password for unknown:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package flashplayer-installer
unknown@unknown-laptop:~$ sudo apt-get install flashplayer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package flashplayer
unknown@unknown-laptop:~$

---

### Post by RomeReactor on 2007-12-11
Hi. As ajgreeny stated, the package you need to install is **flashplugin-nonfree**:
```
sudo apt-get install flashplugin-nonfree
```

Make sure you have the Multiverse repository enabled. Note that apt-get will not look for the compressed package you downloaded from Adobe's website.

---

### Post by mcduck on 2007-12-11
> **unknown user said:**
> Where am I going wrong?
I followed the instructions of this site ([http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)) and got the following message:
With the download on my desktop:

unknown@unknown-laptop:~$ sudo apt-get install flashplayer-installer
[sudo] password for unknown:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package flashplayer-installer
unknown@unknown-laptop:~$ sudo apt-get install flashplayer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package flashplayer
unknown@unknown-laptop:~$
That page is slightly outdated.

Try "sudo apt-get install flashplugin-nonfree" instead.

---

### Post by unknown user on 2007-12-11
This is what I get when I do that:

unknown@unknown-laptop:~$ sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package flashplugin-nonfree

---

### Post by mcduck on 2007-12-12
> **unknown user said:**
> This is what I get when I do that:

unknown@unknown-laptop:~$ sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package flashplugin-nonfree

Go to System/Administration/Software Sources and on the Ubuntu Software-tab make sure everything but the source code and Ubuntu CD are enabled (most likely you don't need those two).  Then try again.

If that still fails to work post the output of /cat /etc/apt/sources.list' here.

---

### Post by CJ56 on 2007-12-12
I had this problem yesterday when I installed Ubuntu Gutsy on my old Inspiron 1200. So I went to a Flash site - YouTube, in fact - followed the link to the Flash Player 9 download page, downloaded the tar.gz to my desktop.

Then I right-clicked on the packing-case icon and clicked 'Extract Here'. This put a file 'install_flash_player_9_linux' on the desktop. I right-clicked Open, got two more files - one of which was 'flashplayer-installer'. I right-clicked Open on this, then clicked on 'Run in Terminal'. A Terminal window opened up and I just followed the y/n instructions.

This seems to work fine at the moment - works on Firefox and on Epiphany (which I kind of like as a browser...). Haven't installed Opera yet...

---

### Post by oldcity on 2007-12-12
Solution from CJ56 worked just fine for me.
Thanks
oldcity

---

### Post by Afkpuz on 2007-12-12
Here is the solution for anyone else still having trouble

[http://ubuntuforums.org/showthread.php?t=639029](http://ubuntuforums.org/showthread.php?t=639029)

---

### Post by aonegodman on 2007-12-12
Sounds good but just don't work on my desktop for some reason. These quirky little problems trying to get everything to work together is what is slooooowing the process of winning people over to Linux from Windows. Believe me I want switch so bad I can taste it, but you have to wade through so much of this kind of reprogramming and coding stuff to get things to run. I have been trying several different Linux packages over this past week and I'm getting exhausted trying to make things work. Someday they will come out with a REAL self executing, user friendly destro that just "works". Sorry I'm getting a little frustrated spending hour upon hour on forums and guides and asking and trying and .................... oh phoooyey!

---

### Post by aonegodman on 2007-12-12
YES! Afkpuz has given the correct info and link to solve this issue with exception that some, like myself, may be running off of Live CD testing the waters. Every thing went well and the commands worked perfectly in Terminal, but the Adobe Installer could not find the correct PATH and said:

"WARNING: Please enter a valid installation path.

Please enter the installation path of the Mozilla, Netscape,
or Opera browser (i.e., /usr/lib/mozilla): "

Now I'm guessing that it wants to go to the Live CD and write some code there. So this would probably work on regular install, but in the mean time no way to test it out running the CD I guess.

Thanks!

---

### Post by arhamlinux on 2007-12-12
>  This seems to work fine at the moment - works on Firefox and on Epiphany (which I kind of like as a browser...). Haven't installed Opera yet...

It works on Epiphany, too? But, it does not in my laptop.....(Firefox seems to be frozen frequently)

---

### Post by unknown user on 2007-12-13
CJ56, cracking reply I done what you said and it worked great, I can see the sites that I want to.  This is the kind of reply that I was looking for one that is easy to do for a new Ubuntu user like me as I am not really got to grips with the codes yet.  Hopefully, in time I will though.
Guys, thanks for all your help on this one.

---

### Post by fivesmellydragons on 2007-12-13
> **CJ56 said:**
> I had this problem yesterday when I installed Ubuntu Gutsy on my old Inspiron 1200. So I went to a Flash site - YouTube, in fact - followed the link to the Flash Player 9 download page, downloaded the tar.gz to my desktop.

Then I right-clicked on the packing-case icon and clicked 'Extract Here'. This put a file 'install_flash_player_9_linux' on the desktop. I right-clicked Open, got two more files - one of which was 'flashplayer-installer'. I right-clicked Open on this, then clicked on 'Run in Terminal'. A Terminal window opened up and I just followed the y/n instructions.

This seems to work fine at the moment - works on Firefox and on Epiphany (which I kind of like as a browser...). Haven't installed Opera yet...


Hey thanks man! I tried your method and it worked perfectly. I'm not sure if it didn't work because I was already in Firefox when I tried the install, but I followed your instructions and it works now. Thanks again!! 

Here's the launchpad thread that is going around with it. [https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/173890](https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/173890)

---


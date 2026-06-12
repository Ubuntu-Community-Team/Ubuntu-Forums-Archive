---
title: "Getting Beryl to run in Dapper AiGLX"
date: 2006-12-12
forum: Absolute Beginner Talk
---

### Post by evanvlane on 2006-12-12
Hey,
I'm going through the Install/Ubuntu/Dapper/AiGLX tutorial at [http://wiki.beryl-project.org/index.php/Install/Ubuntu/Dapper/AiGLX](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Dapper/AiGLX) . But whenever I try to launch beryl from a terminal my menu bars disappear, as do the top and bottom bars.

I have AiGLX successfully installed, and have 3d acceleration working on my Radeon 9100IGP.

Whenever I try and run Beryl it gives me this:

```
XGL Absent, checking for NVIDIA
Nvidia Absent, assuming AIGLX
beryl: GLX_EXT_texture_from_pixmap is missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :0.0
```

and all the bars disappear, as do all of my hotkeys that I've established.


The only hang-up on the tutorial thus far has been the line:
```
sudo apt-get install xserver-xorg-air-core linux-dri-modules-common linux-dri-modules-`uname -r`
```

So I went through it step by step and the air-core and modules-common worked just fine, but when I tried ```
sudo apt-get install linux-dri-modules-`uname -r`
``` the terminal returned:
```
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package linux-dri-modules-2.6.15-27-386
```

I tried Googling for the package, but I can't find it. Is there a way to get it installed? And if not, what am I doing wrong?

Also, if I try to run beryl-manager from a terminal it quits the GUI entirely and I have to startx from the terminal to restore it.

Hope this is enough info to help.


Thanks,

Evan.

---

### Post by Zelut on 2006-12-12
I swear I posted an answer to this a minute ago & I guess it didn't go through..

the command looks wrong to me.  Try:

sudo apt-get install linux-dri-modules-$(uname -r)

---

### Post by evanvlane on 2006-12-12
Heh. You did.

For some reason UbuntuForums wouldn't show me my old post, so I reposted, and then I couldn't delete the old topic.

But in anycase, it still displays:

```
elane@elane-laptop:~$ sudo apt-get install linux-dri-modules-$(uname -r)
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package linux-dri-modules-2.6.15-27-386
elane@elane-laptop:~$

```

Do you think I'm missing a repository somewhere? Which repository would this be in?


Evan.

---

### Post by Zelut on 2006-12-12
I just checked and I don't see any linux-dri packages in any of my repos.  Do the instructions you're using suggest adding an additional repository for these additional packages?  Might want to check that again..

---

### Post by evanvlane on 2006-12-12
Yeah, it requires the addition of:
deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) dapper main aiglx

Which I did, and added the public key (the walkthrough lists two; the first one didn't work, but the second one did).

Unfortunately, I can't seem to get that last one to work, no matter what I do.

I looked at uname --help, and it looks like the syntax for the package is linux-dri-modules-(kernel-release). Is it possible that they simply don't have a package for my kernel? Although considering that the walkthrough is entitled "Install/Ubuntu/Dapper/AiGLX", I'm pretty sure there has to be one...


Evan.

---

### Post by evanvlane on 2006-12-12
Aha!

Okay, I tried the 'update part of the instructions' ```
sudo apt-get update
``` again and it said:
```

W: GPG error: http://ubuntu.beryl-project.org dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3FF0DB166A7476EA
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.
```

So I guess the key didn't work, which means I don't have the updated version of the kernel, and therefore there wouldn't necessarily be a package available.

Is there some other way to get the key?

The output from ```
wget http://ubuntu.beryl-project.org/1609B551.gpg -O- | sudo apt-key add -
``` is:
```
--19:17:40--  http://ubuntu.beryl-project.org/1609B551.gpg
           => `-'
Resolving ubuntu.beryl-project.org... 82.140.42.54, 89.200.136.91
Connecting to ubuntu.beryl-project.org|82.140.42.54|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1,730 (1.7K) [text/plain]

100%[=======================================================>] 1,730         --.--K/s

19:17:40 (97.05 MB/s) - `-' saved [1730/1730]

OK
```. 

Is there some other way to go about it?

Thanks!


Evan.

---

### Post by neemz on 2006-12-12
I'd just like to say that it is significantly easier to run beryl/compiz on edgy as it has a more recent version of xorg.

If you wish to run it on dapper I would suggest giving XGL a try.

---

### Post by evanvlane on 2006-12-12
I just recently switched form XP to Linux, and from what I've heard, the switch from 6.06 to 6.10 isn't the most user friendly of transitions, and I'd like to cut my teeth on 6.06 for a while before taking that on.

Although, I was able to find a solution:

I went to the repository site in Firefox, and it gave me a different key command. Tried that in the the terminal and it still didn't work, so I went into their archives and found linux-dri-modules-2.6.15-26-386

which was one off from my uname -r of 2.6.15-27-386

It works now, but some stuff is kind of weird. For instance:
```

libGL warning: 3D driver claims to not support visual 0x4b
beryl: No stencil buffer. Clipping of transformed windows is not going to be correct when screen is transformed.
```

Is there a way to correct that? Because it seems to orient the windows strangely (especially on maximize).

Other than that, it works splendidly. (Oh that and ATI not supporting the rain and water functions.. That kind of irks me... Friggen laptops with Mobility cards. GRRR)


Thanks for the help guys.

Evan.

---

### Post by evanvlane on 2006-12-12
Crud, one more question.

It seems that metacity and beryl both occupy the position of a window manager. So all my hotkeys (<Control><Alt>f for Firefox; <Control><Alt>p for Limewire [p2p]) disappeared. Is there a way to set those via Beryl?


Evan.

---

### Post by evanvlane on 2006-12-12
Nevermind, solved that one:

Beryl Settings Manager->General Options->Commands & Keyboard

---

### Post by bb002 on 2006-12-14
> **kuyaedz said:**
> I swear I posted an answer to this a minute ago & I guess it didn't go through..

the command looks wrong to me.  Try:

sudo apt-get install linux-dri-modules-$(uname -r)

You did. I thought I was reading the same thread a second time....lol [http://www.ubuntuforums.org/showthread.php?t=317671](http://www.ubuntuforums.org/showthread.php?t=317671)

I didn't install the dri modules for the moment...I got this missing debs too.

This part of my post is a bit off topic but does anyone know what thread it was that explains aiglx's missing modules in "/usr/lib/xorg-ailgx"?

---

### Post by DirtDawg on 2007-01-08
> **evanvlane said:**
> I just recently switched form XP to Linux, and from what I've heard, the switch from 6.06 to 6.10 isn't the most user friendly of transitions, and I'd like to cut my teeth on 6.06 for a while before taking that on.

Although, I was able to find a solution:

I went to the repository site in Firefox, and it gave me a different key command. Tried that in the the terminal and it still didn't work, so I went into their archives and found linux-dri-modules-2.6.15-26-386

which was one off from my uname -r of 2.6.15-27-386



Thank you. I was stuck there as well. 
:KS

---

### Post by vineetphillips on 2007-01-31
Hey, 
i m facing the same problem .. i have an internal graphics card (82845G/GL[Brookdale-G]/GE Chipset) . i followed [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Dapper_with_AIGLX](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Dapper_with_AIGLX)
to install beryl on my Ubuntu LTS 6.06 .. the problem is that everyhting is installed except the linux-dri-modules-2.6.15-27-386.. the site says that this package is broken and needs to fixed  and so when i try to install this package it gives me an error saying 

sudo apt-get install xserver-xorg-air-core linux-dri-modules-common linux-dri-modules-2.6.15-27-386
Reading package lists... Done
Building dependency tree... Done
xserver-xorg-air-core is already the newest version.
E: Couldn't find package linux-dri-modules-2.6.15-27-386

I also tried installing the linux-dri-modules-2.6.15-26-386 but then it gives me an error saying 
Reading package lists... Done
Building dependency tree... Done
xserver-xorg-air-core is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  linux-dri-modules-2.6.15-26-386: Depends: linux-image-2.6.15-26-386 but it is not installable
E: Broken packages
 i guess it is because i had cancelled while it was installing before (because i wa not sure)

has anyone got a way around it!!

---


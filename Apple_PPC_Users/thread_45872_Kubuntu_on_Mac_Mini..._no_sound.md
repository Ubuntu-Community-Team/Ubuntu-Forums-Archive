---
title: "Kubuntu on Mac Mini... no sound"
date: 2005-07-02
forum: Apple PPC Users
---

### Post by zenrick on 2005-07-02
Hey everybody,

I'm very new to Linux in general and this forum as well... this is actually my first post. I tried to find something before I posted, but no dice.

I just installed Kubuntu on a Mac Mini, and I have no sound. If I open the mixer in KDE, I get no options and I can't change anything. I am a complete newbie when it comes to Linux, so I don't know how to use the command line either, so please bear with me...  ;-) 

When I boot up or start a new session I get this message:

*****
Sound server informational message:
Error while initializing the sound driver:
device /dev/dsp can't be opened (No such file or directory)
The sound server will continue, using the null output device.
*****

After I hit OK (the only option), the computer boots up fine, but I have no sound and the volume control on the mixer is grayed out. Everything else works perfectly. If I put in an audio CD, it's recognized and I can "play" it, but there is no sound.

Any suggestions??? If anything needs to be configured using the CLI, I have no problem with doing that, but please be very specific, for example, if I need to configure "x file", please tell me exactly what steps to take to modify "x file", and also the new values. 

Is anybody here running Ubuntu on a Mac Mini, *with* sound? Could this be a KDE/Kubuntu issue? I've read that Kubuntu is not as stable as Ubuntu, not sure if there's any truth to that.

Thanks to all for your help!!!

Rick     :grin:

---

### Post by zenrick on 2005-07-04
31 views so far, and no replies??? I refuse to believe I'm the only one having this problem. 

Can anybody help me, please?

---

### Post by pvz on 2005-07-04
There is this big fat **search this forum**  option on the right top side, why don't you try that first? Just search for "mini sound" and you will get plenty of answers to your question..

---

### Post by zenrick on 2005-07-04
[QUOTE=pvz]There is this big fat **search this forum**  option on the right top side, why don't you try that first? Just search for "mini sound" and you will get plenty of answers to your question..[/QUOTE]
 Yeah, if you read my original post at all, you'll notice in the first sentence I mentioned that I had looked (searched) before posting. I get a lot of OLD posts where the problem is exposed, but no solution is given, or someone says to edit "this file" (but not how to do it), or someone suggests "recompiling" the kernel... of course, again no clear instructions. I'm a complete newbie when it comes to Linux. I have no idea how to recompile and half the time I don't even know where to look for a file, much less how to edit it. I used to run DOS and I am NOT afraid to work with the command line, but I need help on how to do it. 

I went [here](http://www.pvv.org/~perchrh/macmini/) and it mentions a kernel image. Am I supposed to "download" this? When I click on it, I get a text file in a separate window that takes forever to display, with loads of gibberish. If I right-click on it and download it, I get a 14 MB text file. Is this normal? Maybe it is, but I have no idea!!! Of course, my copy of Ubuntu is on another machine that is no connected to the Net. Do I need anything else? Please someone help me!

Sorry if I seem PO'd, but I'm just confused and everything seems so complicated, although I'm sure it's not. About 6 or 7 years ago, I tried to get involved with Linux and I even joined a user group, but I eventually got so frustrated and tired of feeling stupid whenever I tried to get something to work in Linux when I considered (and still do) myself to be pretty savvy when it comes to technology. I eventually gave up on Linux back then and would hate to do it again now, especially with the advances Linux has made in the user-friendliness area. 

So, please anybody? I just need some temporary hand-holding, that's all. 

Thanks!!!!!    :grin:

---

### Post by dasaivet on 2005-07-04
sudo apt-get install alsa-base
sudp apt-get install alsa-utils

---

### Post by pvz on 2005-07-05
You should install the kernel file [http://www.pvv.org/~perchrh/macmini/kernel-image-2.6.11.7_1.2_powerpc.deb](http://www.pvv.org/~perchrh/macmini/kernel-image-2.6.11.7_1.2_powerpc.deb)
from that site on your Mac Mini. Save it with right-clicking somewhere on your computer. It is indeed around 14mb, this is normal. Now you should transport this file to your Mac Mini, maybe you can burn it on a cd if the machine is not networked? Once you have the file "kernel-image-2.6.11.7_1.2_powerpc.deb" on your Mini, say in your home directory, you have to issue the command
"sudo dpkg -i kernel-image-2.6.11.7_1.2_powerpc.deb" to install your new sound-enabled kernel. You will be asked for your password, fill it in and pres enter. Your new kernel will be installed. the last important step is
"sudo ybin" to set your bootloader to the new kernel.
Now reboot, and if all goes well, you should have sound working on your Mini.
(you have to open a console/shell to enter these commands btw.  Select Terminal Program (Konsole) from KDE menu -> system to get a console :-)

---


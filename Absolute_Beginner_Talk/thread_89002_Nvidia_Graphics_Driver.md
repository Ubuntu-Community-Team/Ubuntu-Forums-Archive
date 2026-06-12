---
title: "Nvidia Graphics Driver"
date: 2005-11-11
forum: Absolute Beginner Talk
---

### Post by el__sid on 2005-11-11
Hey all

I just transferred to Ubuntu after getting sick of the lack of sound in FC4 :P. And somehow you guys achieved the impossible and made a creative driver for Linux, when creative can't.

But anyway, I have version 5.10 and I'm having some trouble installing the drivers. I'm trying through the "Ctrl-Alt-F3" Konsole mode, and am getting the message that X-server is still running. Now in FC4, the command "init 3" usually gets you around this, but not in Ubuntu. So I ran Ubuntu in recovery mode, which did disable X-server, only to be told that my version of GCC is version 4.0, and the Kernel is compiled in 3.3.

So I try to change the GCC version "GCC -V 3.3" only to be told that it doesn't exist (syntax error?). So I run the installation again telling it to carry on regardless of my GCC version.

The Kernel gets made and all seems well, and then it tells me that "Nvidia.ko is unable to load because the kernel was built using the wrong kernel source"

I've looked through the guide on this forum, but I don't have an "Nvidia-setting" option in my Synaptic P.M. and other instances of this error in google refer only to old graphics cards, and I have a 6600.

Any idea's appreciated guys,

-El__Sid

---

### Post by 23meg on 2005-11-11
Try this before starting the nvidia installer:

```
CC=gcc-3.3
export CC
```

Also make sure you have gcc 3.3 installed.

---

### Post by spizkapa on 2005-11-11
[QUOTE=el__sid]
I just transferred to Ubuntu after getting sick of the lack of sound in FC4 :P. And somehow you guys achieved the impossible and made a creative driver for Linux, when creative can't.
[/QUOTE]

Welcome and enjoy! Small correction, Ubuntu didn't write the creative drivers, Creative did... why it doesn't work on Fedora, I can't say.

> 
But anyway, I have version 5.10 and I'm having some trouble installing the drivers. I'm trying through the "Ctrl-Alt-F3" Konsole mode, and am getting the message that X-server is still running. Now in FC4, the command "init 3" usually gets you around this, but not in Ubuntu. So I ran Ubuntu in recovery mode, which did disable X-server, only to be told that my version of GCC is version 4.0, and the Kernel is compiled in 3.3.


There is no reason why you should do all this. The NVidia driver should just be installable from Synaptic. It will do all the compilation magic for you and, this time, you can thank Ubuntu for this!

If, for any reason, you can't install the nvidia kernel module from Synaptic (have you made sure you have ALL the repositories?) then you can just turn gdm off with: sudo /etc/init.d/gdm stop

This will stop the X server as it's being managed by gdm. Then, do what compilation you want and start it again with:
sudo /etc/init.d/gdm start

That should be it. Good luck!

---

### Post by el__sid on 2005-11-11
I got the 7667 drivers working through synaptic, but it still won't install 7676.

I tried the cc=gcc-3.3 but it didn't make a difference, the installer still whined and failed.

any other suggestions, or should I just stick with 7667?

Oh and how do I increase my refresh rate? 60Hz Hz my eyes :P and that's all I get to choose (or 56Hz in 800x600, but we won't be doing that :)

Thanks for the help so far,

- el__Sid

p.s. On the creative drivers front. If you go to the creative site, and ask for Linux drivers, they say none exist, which is why I was curious about the Ubuntu ones.

Edit: the GCC compiler version was actually 3.4, but I tried "cc=gcc-3.4; export cc" and got nothing still

---

### Post by spizkapa on 2005-11-11
If you haven't got a specific problem with 7667, I'd stick with them for now.

You can increase your refresh rate and resolution from System -> Preferences > Screen resolution. If, as I suspect, it doesn't give you the option of a higher refresh rate, you may need to:

sudo dpkg-reconfigure xorg-common

which I think will run the configuration of the xserver. You should then be able to set the refresh rate higher. Your card/monitor may be unable to run at higher refresh rate unless properly configured in which case, you'll have to dig out the monitor's book and put in the right values for hsync and vsync. Don't experiment with this if you're not sure, you will fry the monitor!

---

### Post by 23meg on 2005-11-11
Are you sure you have gcc 3.4 installed? Make sure you have the packages "gcc-3.4", "gcc-3.4-base" and "gcc" installed.

---

### Post by el__sid on 2005-11-11
You're right I don't have the packages installed, and they're not in the list. where can I get them?

---

### Post by 23meg on 2005-11-11
```
sudo apt-get install gcc gcc-3.4 gcc-3.4-base
```

---

### Post by spizkapa on 2005-11-11
Are you sure it's a good idea to go installing an older version of gcc (and associated libraries) which are not compatible with gcc 4 (and g++/libstd) that vreezy came with? Perhaps it's better to leave it alone... You probably won't find too many problems if you're not a c++ developer. But, unless you REALLY have to, I wouldn't install a pre-4 version of gcc.

BTW, this is another reason why you shouldn't have skype installed until skype produce a gcc 4 compatible package. Having libstdc++-5 and libstdc++-6 on the same system will inevitably lead to problems.

---

### Post by 23meg on 2005-11-11
There are no problems associated with having both versions of gcc installed for a casual user. If any problems do arise it's safe to uninstall one of the versions once its function is complete. You can't compile the Nvidia kernel module without gcc 3.4 in Breezy since the Breezy kernel is compiled with gcc 3.4.

---

### Post by spizkapa on 2005-11-11
[QUOTE=23meg]There are no problems associated with having both versions of gcc installed for a casual user. If any problems do arise it's safe to uninstall one of the versions once its function is complete. You can't compile the Nvidia kernel module without gcc 3.4 in Breezy since the Breezy kernel is compiled with gcc 3.4.[/QUOTE]

Absolutely, the **casual** i.e. non-developer user should be fine. And, just to be clear, when you say that it's safe to uninstall one of the versions, you actually mean to uninstall the 3.x version since uninstalling the 4.x version will remove the whole of ubuntu, except the kernerl. To test that out, try uninstalling either libstdc++6.x or gcc4-base.

For only the nvidia driver (and only a minor version increase there), installing gcc may not be worth it overall, unless of course the earlier driver version causes you problems.

---

### Post by nrwilk on 2005-11-11
This is an excellent guide covering exactly what you need.

In fact, I'm surprised no one has posted it here yet.

> 
[http://ubuntuforums.org/showthread.php?t=75074&highlight=install+nvidia+drivers](http://ubuntuforums.org/showthread.php?t=75074&highlight=install+nvidia+drivers)


BTW, I write C++ and have not yet had a single problem with both versions of gcc installed.  I don't think it'll cause any problems.

spizkapa:
make sure you write the
```
CC=gcc-3.4
export CC
```
exactly like that.  I had to try this process about 5 times before I figured out that I was typing it wrong.

---

### Post by el__sid on 2005-11-11
[QUOTE=Fealos]This is an excellent guide covering exactly what you need.

In fact, I'm surprised no one has posted it here yet.



BTW, I write C++ and have not yet had a single problem with both versions of gcc installed.  I don't think it'll cause any problems.

spizkapa:
make sure you write the
```
CC=gcc-3.4
export CC
```
exactly like that.  I had to try this process about 5 times before I figured out that I was typing it wrong.[/QUOTE]

Yeah I tried the guide, but without gcc 3.4 i'm screwed.

I tried the refresh rate thing, but all it did was display two results of something in the konsole and nothing else.

---


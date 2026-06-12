---
title: "Just installed ubuntu and need help on a few things"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by nanolight on 2007-05-06
All right, I've just installed the 64bit 7.04 ubuntu and was wondering whether you could help me out with a few things.

The first thing is that I let ubuntu automatically partition my 120gb hdd and it decided to create a 107GB main partition and a 4.5GB swap.

Would I off been better of like creating a 100mb boot partition, 2GB swap partition (I like to be on the safe side, i also have 2gb of ram), a 20GB ubuntu partition and use the rest for my home? Or is it best to wait till i understand it more then I can set it up properly then.

Next thing is i have an  intellamouse V3 and as wondering how I can configure the middle button so when I press It down in like programs like firefox is scrolls down? Also how can I get the backwards and forwards button to do exactly that in firefox and other folders?

Also I've managed to Install be Beryl and when I use it the top part of the windows where the minimize, maximize and close buttons are disappear. How can I fix this?

Another thing do you know of any repository where I can get flash and other multimedia codecs? Ive followed several posts on this forums but it keeps sayings its unavailable.

Last thing, anything you would suggest to do, or install on a fresh system?

Any help would be great :grin:

---

### Post by Happy_Man on 2007-05-06
You don't need a /boot, /var, /tmp partition, but I would suggest getting yourself a /home partition before you do too much. That way, if you need to reinstall, all your settings and files will be intact. You need to install emerald-themes for Beryl to work right. Get Automatix2 for help with codecs: [http://www.getautomatix.com](http://www.getautomatix.com). Hope this helps!

---

### Post by Cypher on 2007-05-06
First, welcome to Ubuntu..:)

Regarding the partitioning. The default scheme might work for now, but as you've already surmised it could be done better and the one you've come up with would be better. It is usually good to isolate "/home" on a seperate partition so that you can re-install Ubuntu without having to disturb any of your personal files.

The middle scroll-wheel should already be functioning in FIrefox to scroll through the pages, you shouldn't have to do anything special to make this happen as long as the right mouse was detected. I'm uncertain about the back/forward buttons.

After you activate Beryl if you lose the top bar, known as Window Decoration, you'll have to modify the X11 configuration for this. Open up a terminal with Applications->Accesories->Terminal, then type
```

gksudo gedit /etc/X11/xorg.conf

```
Scroll down until you find the 'Section "Device"' section..before the "EndSection" add
```

Option   "AddRGBGLXVisuals" "True"

```
For example, in my configuration the entire section looks like:
```

Section "Device"
    Identifier     "NVIDIA Corporation NVIDIA Default Card"
    Driver         "nvidia"
    Option         "AddARGBGLXVisuals" "True"   # This adds the window decoratio
n
EndSection

```
Now, you can either reboot the machine. Or logout, and hit CTRL-ALT-BACKSPACE to cause a X11 Restart, now with Beryl you should have the minimize/maximize/close buttons..

---

### Post by nanolight on 2007-05-06
> **Happy_Man said:**
> You don't need a /boot, /var, /tmp partition, but I would suggest getting yourself a /home partition before you do too much. That way, if you need to reinstall, all your settings and files will be intact. You need to install emerald-themes for Beryl to work right. Get Automatix2 for help with codecs: [http://www.getautomatix.com](http://www.getautomatix.com). Hope this helps!
Ill get around to creating my home partition later on in the day. Do I have to do anything to get all the settings to go into the new partition or is that done automatically?

I'm not quite sure how to install those themes there like in the menu but I'm not sure how to install them.

Automatix fixed up my codec problems as far as installing them go. Ill test them out later.

Thanks alot for that.


> **Cypher said:**
> First, welcome to Ubuntu..:)

/snip

The middle scroll-wheel should already be functioning in FIrefox to scroll through the pages, you shouldn't have to do anything special to make this happen as long as the right mouse was detected. I'm uncertain about the back/forward buttons.

After you activate Beryl if you lose the top bar, known as Window Decoration, you'll have to modify the X11 configuration for this. 

/snip

Now, you can either reboot the machine. Or logout, and hit CTRL-ALT-BACKSPACE to cause a X11 Restart, now with Beryl you should have the minimize/maximize/close buttons..
Thanks.

In the device manager it is picked up correctly. I guess ill have to do more reading about that.

I modified the x11 conf files rebooted and now when I use beryl the terminal window is completely whited out.

---

### Post by Happy_Man on 2007-05-06
Well, if you already installed to one partition, yes, you will have to jump some hoops to get a /home, but it's not that bad, just follow this guide:
[http://psychocats.net/ubuntu/separatehome](http://psychocats.net/ubuntu/separatehome)

It's easy to install themes from Emerald Theme Manager, just click them! :razz:

---

### Post by azdragon on 2007-06-11
First thing, I made the same mistakes as you last week when I installed my OS. 

 I figured I have a 64 bit CPU so why not install the 64 bit version.  Well first off the web site says that the 64 bit version is only 2-5% faster.   Plus it simply is VERY VERY hard to get JAVA, or FLASH to work, along with thousands of other things.  After 2 days of trying I downloaded the 32 bit live CD, reformatted and started all over.   This will also fix your home directory problem.   

I only gave Ubuntu 50GB of space, 8GB for swap then I made the other 500GB into three Fat32 Partitions.   I did this to make one a home, one for media and one for other stuff.  I find that it works very good and if I ever need to install windows some day in the future I have access to all my stuff.


On the missing buttons I had that problem also, and I tried the solution the other guy gave and my file was already like that, it was of no help, I still had the problem.   What I did to fix it is  go into Application >System tools > Beryl Settings Manager 
Then click on Visual Effects, then click on Windows Decorations.   Make sure in the "Command Line" area it says emerald.       If the emerald software is not running it does not work.  Who knows why this is not on by default in the new release....but this fixed it for me.

---


---
title: "At the end of my rope... can't load video AT ALL"
date: 2007-03-10
forum: Absolute Beginner Talk
---

### Post by dragonchilde on 2007-03-10
Alright, in my attempt to get a resolution over 1024 X 860 (or whatever it is), I managed to completely mess up my drivers, to the point I can no longer see anything once Ubuntu loads. I get the load splash, but when it gets to the drums part, the monitor SHUTS OFF COMPLETELY. 

I can hear it... I can even log in, but I can't see anything.  At ALL. 

If I can't see it, how the HECK can I fix this? 

I can boot into recovery mode, but that takes me to root command line... which might as well be greek to me, for all I know what to do. 

Please help! I've got a nVidia geforce 4 Ti 4400.  

I'm not asking for the world here, just a working monitor and a resolution ABOVE "Hi I'm blind". 

I was running something from the ubuntu site that involved some command line resets (three lines, sudo command), some guide that said something about "fix it" and "resolution"... now I can't find it. It was bookmarked on my ubuntu partition, but now I'm in windows and of course can't access it.  I'll be happy to tell you what I did to it if you can get me my video working. 

PLEASE help, I'm getting frustrated. The more I try to learn, the more I figure out that I don't know, and the more I wind up messing up. I'm about *this* close to a clean install of something else. I knew there would be a steep learning curve, but this is getting ridiculous. 

I'm going to bed now, but I'll be up in the morning to read any responses and fix this mess.

---

### Post by Dr. Nick on 2007-03-11
try this from the revovery mode

dpkg-reconfigure xserver-xorg

since you have a nvidia when you reach the video driver section choose "nv" then when you reach the monitor selection part pick the middle of the 3 levels, not simple. Once their choose the desired resolution and finish the wizard.

look in my signature for some more info

Good Luck

---

### Post by 3rdalbum on 2007-03-11
Apart from going to the recovery mode, you could try pressing "control-alt-F2" when your monitor turns off. That should turn your monitor back on and bring you to a command prompt where you can type:

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by dragonchilde on 2007-03-11
okay, we're back up and running. Thanks so much. Now, I've got to try your suggestions for getting my resolution turned up, Dr Nick. That's a great site, by the way.

Edit:  No dice. I'm obviously missing something, since my nvidia card isn't displaying the resolutions. xorg.conf has all the resolutions listed, they're just not showing up when I go to change my screen resolution.

---

### Post by dragonchilde on 2007-03-11
ARGH.  I'm back to spitting nails, although at least I have video.

I've been trying, and trying, and trying to get this $%^&%@$# nvidia drivers to install!  I've tried several different things, all of which fail when it's time to install nvidia GLX, and the last attempt was made following this guide: 

[http://knowledge76.com/index.php/XGL/Compiz_Nvidia_32bit](http://knowledge76.com/index.php/XGL/Compiz_Nvidia_32bit)

When I reach this point: Installing nVIDIA driver I get the following error:

dragonchilde@dragonslair:~$ sudo apt-get install nvidia-glx
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  nvidia-glx: Depends: xserver-common (>= 4.0.3) but it is not going to be installed
E: Broken packages
dragonchilde@dragonslair:~$ sudo nvidia-xconfig sudo: nvidia-xconfig: command not found 

Anyone have any ideas?

---

### Post by dragonchilde on 2007-03-11
Whoops... in the process of trying different things to fix this problem, I managed to completely corrupt and remove about half of ubuntu, so I figured now would be a good time to do a complete, clean install. 

I'll do some work and see if I can get the new install working better, and if/when I have problems, I'll be back here to get help.

---

### Post by Dr. Nick on 2007-03-11
I went into my xorg.conf and removed some resolutions, also when doing the dpkg-reconfigure part just choose the monitor that has the desired resolution listed and that may help.

Post back with any progress

---

### Post by dragonchilde on 2007-03-11
Yahoo!  

After completely messing up my dapper install, I had to do a clean install, and it just so happened that the disk I was sent for free using Sendit (supposed to be dapper) turned out to be Edgy (how's that for awesome!) 

Anyway, after updating, running easyubuntu, and then following Dr Nick's instructions on Fixing Low Resolutions from the link in his signature, it works! I'm currently running on 1280x1200, and the nvidia logo flashed when Ubuntu was loading, so I'm assuming that the sucker actually worked! 

Thank you SO much. I think I was making things a LOT harder than they had to be. 

Some of that may be the upgrade to edgy, but honestly, I think the problem was between the keyboard and the chair. 

Thanks guys!

---

### Post by Dr. Nick on 2007-03-11
Glad you got it, It took me a bit to get it the first few times, but after that it went smoothly.

When feisty comes out next month it should be even easier to get them working :)

---


---
title: "How to stop x server"
date: 2007-09-08
forum: Absolute Beginner Talk
---

### Post by _mOrgoth_ on 2007-09-08
I am trying to stop x server so I could install nvidia drivers. Till now I tried tips from this forum but it don't work. I tried ctrl-alt-F1 and then after login in sudo /etc/init.d/gdm stop. Then I tried to run script to install drivers but it say that my x server is still running. What is the problem??:confused:

---

### Post by Happy_Man on 2007-09-08
Reboot into recovery mode and do your driver installing from there. The option is available from the GRUB menu at startup.

---

### Post by Linux_Man on 2007-09-08
I read about this problem in a Linux magazine, their solution was to type
sudo rm /temp/.X0-lock

(either after X it is a 0 or an O I am not sure and I have never installed the drivers myself

---

### Post by _mOrgoth_ on 2007-09-08
So I reboted and login into recovery mod. Now it say that I am runlevel1 and that I should be runlevel3(telnit 3)????

---

### Post by _mOrgoth_ on 2007-09-08
> **Linux_Man said:**
> I read about this problem in a Linux magazine, their solution was to type
sudo rm /temp/.X0-lock

(either after X it is a 0 or an O I am not sure and I have never installed the drivers myself
 my system does not recognized that command

---

### Post by Linux_Man on 2007-09-08
Hmmm, well it was just the solution a Linux magazine gave, I have not tested it myself but I decided to post it in hopes that it was useful/correct.

---

### Post by _mOrgoth_ on 2007-09-08
> **Linux_Man said:**
> Hmmm, well it was just the solution a Linux magazine gave, I have not tested it myself but I decided to post it in hopes that it was useful/correct.


Thx in any case :-) Any help is welcome. Any ideas how to set to runlevel3 (telnit 3)??

---

### Post by Beggar on 2007-09-08
I believe in ubuntu FF the lock file is at /tmp/.X0-lock (it is a zero, it signifies the display that X is running on.


```

sudo /etc/init.d/gdm stop 
sudo rm /tmp/.X0-lock

```
install away...

Out of curiosity what video drivers do you need to jump through so many loops for?

---

### Post by ravenwere on 2007-09-08
You shouldn't need to stop the xserver to install the nvidia drivers only a reboot at the end is required.

Also if you are unfamiliar with command line installation many people use Alberto Milone's Envy program to automate the process.
```
sudo apt-get install envy
```

Before you do this also be familiar with your /etc/X11/xorg.conf file as you may need to tweak this file after installing new drivers.

cheers,

---

### Post by screamkitty on 2008-01-06
I am having this exact same problem.

I'm completely new to Linux- I really wanted to try it, and finally got an opportunity with my girlfriend's mother's computer - since they cannot afford to buy a computer - let alone an OS.

I recently built a computer for my girlfriend's mother and loaded Ubuntu on it.  It's actually a DELL Dimension 4600 tower that was given to my friend who works for a company who just got new machines and gave him their old ones (after they stripped them of RAM).  So basically, I just added RAM, a hard drive and Ubuntu - so not truly a build - but I digress.

The card that came with the tower is an nVidia GeForce 4 MX.  

My initial problem is that the computer does not have an internet connection (they can't afford it).  So I'm forced to my (this) computer to find support, software, etc. then use my external hard drive to transport needed software, drivers, etc. back to the Ubuntu machine.  So, downloading the drivers from the repositories is out.

I went to nVidia's website and they have a Linux x86 driver for the GeForce4 MX with instructions (exactly the one's the initial poster described.

I also did the same thing by rebooting in recovery and got the same message (in runlevel1 need runlevel3 - or whatnot).

I will try this:
 	
```
sudo /etc/init.d/gdm stop 
sudo rm /tmp/.X0-lock
```

-and post my results.

Just curious - Is installing ATI drivers any easier than nVidia drivers?

---

### Post by ryanVickers on 2008-01-06
nVidia is always easier than ATI because they are way more friendly to Linux...

either way, *_if possible_*, I would **highly** recommend using the Restricted Drivers Manager to do this...

---

### Post by screamkitty on 2008-01-06
Well, that was the first thing I tried - it shows the driver for my card but it's not enabled.  When I try to enable it says something like the software source is not enabled  - so I went to software sources and enabled all of them before realizing it makes no difference because that computer isn't connected to the internet, so I can't do it that way.

So, if this doesn't work, I give up.

---

### Post by Thunar on 2008-01-06
@screamkitty: Unfortunately, without Internet there is no way to install new drivers, or any software for that matter, unless you download it from a computer that has an Internet connection and install it manually. Harder, but not nearly impossible.

@_mOrgoth: Of the many times I've installed Nvidia drivers on Linux, not one time have I ever had to stop X server. Quite the contrary, it's much easier to install when you have a nice gui to work with, and a working web browser to reference with, than on a black screen full of white dos-like text. You shouldn't have to do more than restart the computer after installing the drivers.

For reference, these pages have helped me in the past, as well as others I've lost along the way. Even though one is meant for Dapper, and the other for Feisty the information remains relevant. I recommend printing this documentation out, as well as any other hints and tips you receive from people in this forum, just in case you end up having a problem with X and need to work command line only. (which is very likely when you play with video drivers)

[http://www.albertomilone.com/latest_nvidia_udsf_feisty.html](http://www.albertomilone.com/latest_nvidia_udsf_feisty.html)



[https://help.ubuntu.com/community/Latest_Nvidia_Dapper](https://help.ubuntu.com/community/Latest_Nvidia_Dapper)

Good luck! :)

---

### Post by Thunar on 2008-01-06
By the way, I would be remiss if I didn't mention that unless you plan on doing intense 3D gaming, the free Linux drivers that come with the installation will get you by just fine, and you won't need to pull your hair out trying to figure out how to install the proprietary drivers. You should have at least two, if not three, choices of drivers in Synaptic (System/Administration/Synaptic Package Manager) or you could just do it in your Restricted Drivers Manager. Or you could just leave it alone! ;)

Restricted Drivers Manager and Synaptic both require Internet, however.

cheers

:)

---

### Post by screamkitty on 2008-01-07
Hmm... last night I edited my post - guess it didn't work.  Anyway, I was going to bump the question about setting runlevel1 to runlevel3 (telinit) when booting in recovery mode.

Also, I tried this:

```
sudo /etc/init.d/gdm stop 
sudo rm /tmp/.X0-lock
```

But after the first line, it appeared I was no longer logged in and no commands did anything it seemed.

I did try installing in runlevel one after typing:

```
sh /home/jeremy/Desktop/NVIDIA-Linux-x86-96.43.01-pkg1.run
```

after booting in recovery mode - it then said something about it didn't have something like a profile for my kernel or the like (probably should have wrote it down) - after I continued and it failed to download one, it said something like I didn't have the installed "libc headers" 

Just doesn't make sense that I have the driver from NVIDIA's website sitting on my Desktop (in Ubuntu) and I can't install it.  Sure, having open source software available for download is nice, but I don't see the advantage of relying solely on the internet to make a computer usable.  

Sadly, the only thing I wanted the card to be able to do was turn on GNOME's visual effects.

---

### Post by Thunar on 2008-01-07
ahem...

ALL computers are less useful and more difficult to update and install software on when they don't have the Internet, not just ones running Ubuntu. Be fair. The days of the Sneakernet are LONG over.

However, your right. You should be able to install the Nvidia drivers from your desktop, and you can.

If you like, use this page as reference, it's a little out-dated (intended for Feisty), but still relevant:

[http://www.albertomilone.com/latest_nvidia_udsf_feisty.html](http://www.albertomilone.com/latest_nvidia_udsf_feisty.html)

and scroll down to the "OFFLINE INSTALLATION"

for the Nvidia installer you'll need to use "Method 2"

You might also look for a readme file in the package you downloaded, as well as any references that may be available on the Nvidia site itself. PRINT THEM OUT if you can. Very important.

best of luck! :)

---

### Post by Victormd on 2008-01-07
I tried to do the same thing to update my nvidia driver. The Nvidia site tells you to download and run the installation that is supposed to be "user friendly"... well, a screen pops up and says that you CANNOT be in x server to install, and the installation will end. As for the runlevel3, once in the terminal, as root, type telinit 3 and you should be set to runlevel3. As for the internet access, it will make your life much easier, but not mandatory. I gave up on using the Nvidia drivers and am using the generic NVIDIA driver available under System>Adminstration>Restricted Drivers Manager. Note that if Ubuntu did not automatically tell you that you can use the restricted drivers, chances are you'll have to install the drivers from NVIDIA site. The link that Thunar posted is a good place to start.
Good luck!

---

### Post by screamkitty on 2008-01-08
> **Thunar said:**
> ahem...

ALL computers are less useful and more difficult to update and install software on when they don't have the Internet, not just ones running Ubuntu. Be fair. The days of the Sneakernet are LONG over.

However, your right. You should be able to install the Nvidia drivers from your desktop, and you can.

If you like, use this page as reference, it's a little out-dated (intended for Feisty), but still relevant:

[http://www.albertomilone.com/latest_nvidia_udsf_feisty.html](http://www.albertomilone.com/latest_nvidia_udsf_feisty.html)

and scroll down to the "OFFLINE INSTALLATION"

for the Nvidia installer you'll need to use "Method 2"

You might also look for a readme file in the package you downloaded, as well as any references that may be available on the Nvidia site itself. PRINT THEM OUT if you can. Very important.

best of luck! :)

I apologize if I seemed to single out Ubuntu - that was unintentional.  I'm just not used to relying on the Internet THAT much.  I do appreciate your help and I'll continue posting my progress in an effort to help others trying to do the same thing.

Thanks

---


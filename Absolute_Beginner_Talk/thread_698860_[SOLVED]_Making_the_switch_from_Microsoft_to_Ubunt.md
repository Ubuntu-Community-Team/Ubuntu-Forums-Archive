---
title: "[SOLVED] Making the switch from Microsoft to Ubuntu"
date: 2008-02-16
forum: Absolute Beginner Talk
---

### Post by nsimeone2000 on 2008-02-16
Hello everyone,

Today I had my computer returned to me from Best Buy's customer support apparently now my activation code for Windows Vista is defunct, and won't allow me to go to a desktop because it isn't a genuine product key.  Needless to say, HP, Best Buy and Microsoft aren't at fault.  So I took the liberty of freeing myself from Microsoft's grasp and decided it is time to make the switch.

I am putting Ubuntu onto my Laptop, it is an HP Pavillion 9000.  I have downloaded Ubuntu 7.10 and I also have 7.04, after reading some issues with the latest release, I decided I would go with 7.04.

I am having some major install issues though, I get a black screen during install that lists error upon error upon error.  Should I just delete all the partitions on my Hard Drive and try a fresh install?

I have searched the forums, but I must admit I am a day one newbie to Linux as well as Ubuntu, I have been contemplating the Linux switch for over a year, so if you have some good reading material for me to look at or any advice to help me out I would appreciate it greatly.

Thanks,

Nick

---

### Post by oilchangeguy on 2008-02-16
> **nsimeone2000 said:**
> Hello everyone,

Today I had my computer returned to me from Best Buy's customer support apparently now my activation code for Windows Vista is defunct, and won't allow me to go to a desktop because it isn't a genuine product key.  Needless to say, HP, Best Buy and Microsoft aren't at fault.  So I took the liberty of freeing myself from Microsoft's grasp and decided it is time to make the switch.

I am putting Ubuntu onto my Laptop, it is an HP Pavillion 9000.  I have downloaded Ubuntu 7.10 and I also have 7.04, after reading some issues with the latest release, I decided I would go with 7.04.

I am having some major install issues though, I get a black screen during install that lists error upon error upon error.  Should I just delete all the partitions on my Hard Drive and try a fresh install?

I have searched the forums, but I must admit I am a day one newbie to Linux as well as Ubuntu, I have been contemplating the Linux switch for over a year, so if you have some good reading material for me to look at or any advice to help me out I would appreciate it greatly.

Thanks,

Nick

can you define error upon error? and where did these partitions come from? something you did during the windows period?

---

### Post by JoshuaRL on 2008-02-16
If you don't have anything on your partitions you need, then go ahead and wipe the whole drive.  It will be much easier.

As far as any problems with Gutsy, I believe that most have either been fixed or have good workarounds widely known.  I would suggest you just use the newest version, and if you have any problems, post them here.

A couple links to get you started:

[https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)
[https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows](https://help.ubuntu.com/community/SwitchingToUbuntu/FromWindows)
[https://help.ubuntu.com/community/WindowsApplicationsEquivalents](https://help.ubuntu.com/community/WindowsApplicationsEquivalents)

---

### Post by nsimeone2000 on 2008-02-16
I cannot define error upon error just yet, I am in the process of formatting the computer and doing everything fresh.  When I tried to install 7.04 I received an error that was something like boxcode B731m could not load, and it said that 3 times and then simply froze.

I get scrolling errors when I attempt to install 7.10.  What does a typical install look like with Ubuntu, did you experience any errors when you installed?

The partitions in questions are whatever was on my hard drive from Vista.

---

### Post by nsimeone2000 on 2008-02-16
This is what scared me away from Gutsy,  I haven't finished it all the way through though 

[http://ubuntuforums.org/showthread.php?t=528618](http://ubuntuforums.org/showthread.php?t=528618)

---

### Post by MasterJS on 2008-02-16
If these errors come from the Live CD, it might mean that it just can't load all of your hard ware. It might mean that it does not contain the drivers in the LiveCD.

---

### Post by JoshuaRL on 2008-02-16
What do you mean by scrolling errors?

As far as the "boxcode B731m", I'm not really sure.  I'm thinking it's either an onboard wireless card or HD issues.  Sorry I can't be more specific.

And that actually looks like a pretty decent collection of HOWTOs.  I wish they had something like that for my laptop.  Well, one user had something like it.

---

### Post by nsimeone2000 on 2008-02-16
I might film the errors and put them up on you tube if my fresh install doesn't work.   I will post you a link if I am still having issues.

Half of my headache is gone though, I am so irritated with Microsoft, I am looking ahead now.  Unfortunately though, it takes like 2 hours to get rid of all the Vistaness of my computer, and I have to pick up my girlfriend from work.

I will keep you guys posted

Thanks again

---

### Post by dstew on 2008-02-16
If the Live CD is not running well, try the Alternate Install CD. It installs the same Ubuntu using a text-based interface.

---

### Post by kenono on 2008-02-16
I also have a HP pavillion although it is not the same model as yours.
When I first installed Gutsy, I had to do it on the safe graphics mode. Otherwise I'd be hit with alot of error messages on a black screen too. 
Maybe if you try install on safe mode it'll be ok. It was with my laptop.

---

### Post by nsimeone2000 on 2008-02-16
OK, figured out the error, you were right, it was the drivers, there were 3 in particular that had an issue, I will post the errors, is there a way to pinpoint which drivers are failing?

firmware helper [6403] main: error loading '/lib/firmware/bcm43xx_microcode5.fw'
117.594902 bcm43xx: error: Microcode "bcm43xx_microcode 5.fw not available or load failed.

firmware helper [6430] main: error loading '/lib/firmware/bcm43xx_microcode5.fw'
117.6355911 bcm43xx: error: Microcode "bcm43xx_microcode 5.fw not available or load failed.

firmware helper [6433] main: error loading '/lib/firmware/bcm43xx_microcode5.fw'
117.645687 bcm43xx: error: Microcode "bcm43xx_microcode 5.fw not available or load failed.

After these errors, it looks like it goes to network interface  configuration, says OK to the right of it and then at the bottom of the screen there is a cursor, I figured I would leave the computer alone for awhile and see what happens.

I tried the live CD to see if I would like it first, but to no avail I couldn't get it to work, I basically loaded it up as a boot disk so to speak and just ran the install, if that doesn't work I will try to load it under the graphics safe mode.

---

### Post by JoshuaRL on 2008-02-16
Yeah, it looks like your Broadcom micro wifi chipset isn't supported.  There's a ton of info on that, you'll need to load the Windows driver through ndiswrapper.

---

### Post by Dark-Penguin on 2008-02-16
> **JoshuaRL said:**
> Yeah, it looks like your Broadcom micro wifi chipset isn't supported.  There's a ton of info on that, you'll need to load the Windows driver through ndiswrapper.


I recently purchased a belkin wireless card from Best Buy and I got it to work using ndiswrapper. It's not very hard to do and I'm a newbie (sorta) as well. Here are the instructions that worked well for me. I had to uses the Window$ driver (.inf, .sys) drives as well. I'm actually using my wireless right now. Works great.....thanks to the Ubuntu gods here at Ubuntu Forum.

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by nsimeone2000 on 2008-02-16
Ok, I had to download the Feisty alternate CD to load it onto my computer because I have the AMD chipset.

I went through the text installation and everything went just fine.  However after reboot of the installation, the Ubuntu screen comes up, the little orange bar moves up 3 blocks and then stops.  I went into the grub menu and added the following lines
noapic
noirqdebug
nolapic
irqpoll

Still to no avail I cannot get it to get past 3 bars, anyone have any ideas on what to do now?

---

### Post by MasterJS on 2008-02-16
This is basically fixed on Ubuntu Gutsy Gibbon (7.10). The broadcom wireless drivers are added to the Restricted Drivers Manager. On the Live CD it usually doesn't work because those drivers are needed.

---

### Post by nsimeone2000 on 2008-02-16
I am sorry, I meant like three bars on the program itself, I can't even get the program to load.

---

### Post by nsimeone2000 on 2008-02-16
OK, I finally figured out how to get it to load, but then when I enter my username and password it states the following: 

GDM could not write to your authorization file.  This could mean that you are out of disk space (which is highly unlikely) or that your home directory could not be opened for writing.  In any case, it is not possible to log in.  Please contact your system administrator.

The highly unlikely part I threw in myself, I have given Ubuntu 100 Gigs, that should be plenty

---

### Post by Dark-Penguin on 2008-02-18
> **nsimeone2000 said:**
> OK, I finally figured out how to get it to load, but then when I enter my username and password it states the following: 

GDM could not write to your authorization file.  This could mean that you are out of disk space (which is highly unlikely) or that your home directory could not be opened for writing.  In any case, it is not possible to log in.  Please contact your system administrator.

The highly unlikely part I threw in myself, I have given Ubuntu 100 Gigs, that should be plenty

Well I'm not sure if this helps but I got that one time so I had to type;

sudo dpkg-reconfigure -phigh xserver-xorg

I find starting from a completely fresh install and backing up my xorg file helps

---


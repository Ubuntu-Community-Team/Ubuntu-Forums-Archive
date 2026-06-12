---
title: "Powermac G5, Ready for takeoff!  Runway 6!  Roger Roger!"
date: 2006-07-18
forum: Apple PPC Users
---

### Post by mgregory on 2006-07-18
Yo!  I got a dual G5 2.0Ghz machine and have been trying to install Ubuntu with no go.  I can install it, but the fans rev uncontrollably.  It's hard to sit next to the machine in fear it will start to taxi down the desk.

I thought I would just put a post on here about the fan revving for the help of the community.  Maybe they have a solution I am not aware of.  My g% is up to date on all the firmware, etc.  Not sure what to try.

I just tried Yellow Dog too, but it freezes during install.  

Anyhoo - thought it would be cool to try our linux on a mac.

Thanks!

---

### Post by 3rdalbum on 2006-07-18
Sorry to disappoint you. Ubuntu doesn't have fan control on the G5s for some inexplicable reason. I've also heard that the other PPC distros have the same problem. Have you maybe tried the Mandriva One (live CD)?

---

### Post by j2lunt on 2006-07-18
EXACTLY my situation as well.  January 2006 G5 iMac with OS 10.4.7.  Freezes when installing Yellow Dog; fan roars when installing Ubuntu.  Is there likely to be any further development of 6.06 so it will run on these G5 machines?

---

### Post by joshuapurcell on 2006-07-18
> **3rdalbum said:**
> Sorry to disappoint you. Ubuntu doesn't have fan control on the G5s for some inexplicable reason. I've also heard that the other PPC distros have the same problem. Have you maybe tried the Mandriva One (live CD)?This answer makes me cringe. If the fans work for another distribution then it can work for Ubuntu. I'm trying to decide whether or not to buy one of these monster machines for my next desktop so I don't have any way to test out a fix for this yet, but I'll look around and see what is out there.

EDIT: Does loading this module help with the problem?:

therm_adt7467

Here are some links I found that talk about this problem and offer some possible solutions:

[http://seb.france.free.fr/linux/ibookG4/iBookG4-howto-4.html#ss4.1](http://seb.france.free.fr/linux/ibookG4/iBookG4-howto-4.html#ss4.1)
[http://geekounet.org/powerbook/ibookg4.html](http://geekounet.org/powerbook/ibookg4.html)
[http://ozlabs.org/pipermail/linuxppc64-dev/2005-August/004870.html](http://ozlabs.org/pipermail/linuxppc64-dev/2005-August/004870.html)

---

### Post by mgregory on 2006-07-18
I'll try that Mandriva One tonight!

As far as the therm_adt7467 module...  how does one load it and where do I get it??

Thanks!

---

### Post by pindar on 2006-07-18
Things may be different for  the dual processor machines, but I have tried gentoo and SuSE linux on my G5 1.8, and I can confirm that the fans behave(d) normally in both distributions (I'm still running gentoo on it). So it's either Ubuntu specific or G5 dual specific...

Thomas

---

### Post by mgregory on 2006-07-18
Well - I tried Yellow Dog, it repeatedly froze while starting up, even in safe mode.  I tried Gentoo, but it seems too complex and I don't want to screw up my main Mac OS X.

Ubuntu seems to be the most user friendly and easiest to install.  I guess they can't support every single computer made.

I reinstalled Ubuntu and ran all the updates thinking it would fix something.  I'll just let it be until I can figure something out.  I'm scared it will burn out my computer or blow up the fans.

I also noticed the display wasn't working properly.  I have a 20" Studio Display and I couldn't bump up the resolution beyond the minumim setting.

Oh well - I'm a devout Mac fan anyways.  I just wanted to see what the other side was like.  Now I'm a more devout Mac fan.  lol

Thanks for all your help!  The Ubunutu Community is by far the most helpful and friendly group!  Way to go people!  Thanks!](*,)

---

### Post by bogoliubov on 2006-07-19
> **mgregory said:**
> Well - I tried Yellow Dog, it repeatedly froze while starting up, even in safe mode.  I tried Gentoo, but it seems too complex and I don't want to screw up my main Mac OS X.

Ubuntu seems to be the most user friendly and easiest to install.  I guess they can't support every single computer made.

I reinstalled Ubuntu and ran all the updates thinking it would fix something.  I'll just let it be until I can figure something out.  I'm scared it will burn out my computer or blow up the fans.

I also noticed the display wasn't working properly.  I have a 20" Studio Display and I couldn't bump up the resolution beyond the minumim setting.

Oh well - I'm a devout Mac fan anyways.  I just wanted to see what the other side was like.  Now I'm a more devout Mac fan.  lol

Thanks for all your help!  The Ubunutu Community is by far the most helpful and friendly group!  Way to go people!  Thanks!](*,)


I guess that the Studio display dont have the "standard" resolutions, since it's a wide screen thingy.
Find the appropriate resolutions for your monitor and then we'll edit the configuration file.
First we make a backup of the original file:
sudo cp /etc/X11/xorg.conf /etc/x11/xorg.conf.BACKUP
It will as for you password.

Then we can edit the file:
sudo gedit /etc/X11/xorg.conf
This will open a text-editor

Now look for the screen section, should look something like this:
Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA Corporation NV40? [Unknown nVidia Card]"
        Monitor         "L1715S"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
EndSection

Here we can add resolutions, but be sure that your monitor can display them!

When your finished, save the file and restart the computer.
If things don't work for you, just change to the original configuration file:
sudo cp /etc/X11/xorg.conf.BACKUP /etc/X11/xorg.conf

As for the fan issue I don't know; but you might be missing some module. Or the kernel needs to be patched.

---

### Post by eby on 2006-07-20
i know this won't help with your g5 problem. if you have a G4 & panther, you can run ubuntu under Mac-on-Mac on OS X (no need for partitioning). Why G4 ?. because Mac-on-Mac won't run on G5 nor on tiger :mad:

---

### Post by mgregory on 2006-07-21
Well, I got Ubuntu working.  Not the most typical way.  But the fans aren't roaring and the display is working properly.

I am running it from within Mac OS X in Virtual PC 7.  It works, but not very snappy.  Oh well, at least I can try it out and I don't have to get grief from the wife about yaboot!

Here is a screenshot:

[http://www.fyre-fraust.ca/linux/ubuntu.jpg](http://www.fyre-fraust.ca/linux/ubuntu.jpg)

---

### Post by stmiller on 2006-08-04
I can confirm that powermac G5 fan support is excellent in current Gentoo PPC. Though you have to use the previous install CD to boot (then just point it to the latest snapshots). See gentoo forums for more details.

It's as silent as in OS X. Even when running high cpu % in Gentoo, it never gets loud.

Sound works excellent in Gentoo also on the powermac G5.

I love ubuntu (have it install on my iBook) but it will take some work before it has thermal and sound working properly for the G5.

---

### Post by kellogs on 2006-08-04
sorry to be abit on the opposite side here, but I've got a powermac G5 Dual 2.3ghz with the fans working perfectly... and I dont think its a matter of luck. did you try installing ubuntu with install-powerpc64-smp?

that's what I did, the fans only go full work if you do intensive tasks, and for moments not totally full blowing. most of the day they are quite. 

I use ubuntu dapper updated until the day of today.

---

### Post by stmiller on 2006-08-08
Hi Kellogs:

Is your powermac the dual CPU kind, or the dual core kind? What video card, everything? What is your output of 
$ cat /proc/cpuinfo

?

Thank you. I would love to switch to ubuntu on my powermac.

---

### Post by mgregory on 2006-12-05
Hey-o!  I finally got a chance to download the latest Ubuntu.  I have it installed and the fans ARE behaving properly!  Right on!

Now I can fiddle around to get my Studio Display at the right resolution!

Thanks!
:-D

---

### Post by mgregory on 2006-12-05
Sweet man!  It worked great!  Rebooted at my proper resolution!  Now I got a Dual G5 with fans that are behaving, proper resolution, sound, internet everything so far!  This is the first Linux distro I have properly installed and it is blazing fast!

Thanks everyone!
:D 

> **bogoliubov said:**
> I guess that the Studio display dont have the "standard" resolutions, since it's a wide screen thingy.
Find the appropriate resolutions for your monitor and then we'll edit the configuration file.
First we make a backup of the original file:
sudo cp /etc/X11/xorg.conf /etc/x11/xorg.conf.BACKUP
It will as for you password.

Then we can edit the file:
sudo gedit /etc/X11/xorg.conf
This will open a text-editor

Now look for the screen section, should look something like this:
Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA Corporation NV40? [Unknown nVidia Card]"
        Monitor         "L1715S"
        DefaultDepth    24
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
EndSection

Here we can add resolutions, but be sure that your monitor can display them!

When your finished, save the file and restart the computer.
If things don't work for you, just change to the original configuration file:
sudo cp /etc/X11/xorg.conf.BACKUP /etc/X11/xorg.conf

As for the fan issue I don't know; but you might be missing some module. Or the kernel needs to be patched.

---


---
title: "g3 imac - no network"
date: 2008-04-09
forum: Apple PPC Users
---

### Post by Ecclesia on 2008-04-09
I have an interesting issue with an old imac that I acquired  recently.  I started the process to install linux and then realized that there was no network connection.  It's an old 350 ghz imac and currently has OS 9 installed on it.  Oddly my router doesn't see the imac when connected (i.e. the port light doesn't come on, dhcp won't pick it up and I can't ping it).

I don't have much mac experience.  Anyone have an idea of how to get the network card working?  Is this just a dead card (it doesn't seem to work with OS 9)? Could a dead PRAM have anything to do with this?

Thanks.

---

### Post by stream303 on 2008-04-10
From a terminal, does:

```
sudo /etc/init.d/networking restart
```

bring it back to life?  You may have to play with your network settings prefs once this is started and possibly add

```
auto eth0
```

to **/etc/network/interfaces**

Did you install without the network connected?  The most un-elegant way to resolve it would be to reinstall with the network connected, but don't say I said that.... :)

---

### Post by Ecclesia on 2008-04-10
The network will not connect during installation, nor does it connect when using OS 9.  I actually haven't installed yet, because I can't get the network running - given that I'm going to use it to stream music, I figured that it's pointless to do an install if I can't get the network running.

My router doesn't show a cable connected when the computer is plugged in and on.  I'm thinking at this point that it's probably a dead network card.

Anyone know a good forum for old mac hardware?

---

### Post by slacka-vt on 2008-04-10
Just to check all your bases, does the router work with other computers ?
Just to rule out that it's not a problem with your router. 
Also, did you try other Ethernet cables and other ports on the router ?
Just got to ask these questions.
Have you tried bypassing the router all together ?

~s

---

### Post by linear on 2008-04-10
> **Ecclesia said:**
> Anyone know a good forum for old mac hardware?

This is a good place to start: [http://lowendmac.com/](http://lowendmac.com/)

---

### Post by stream303 on 2008-04-10
Aside from physical problems, ie bad cable, bent or smashed jack pins, corroded pins, , dust bunnies shorting things out, here is some info on zapping the pram, and doing pmu reset:

[http://docs.info.apple.com/article.html?artnum=2238](http://docs.info.apple.com/article.html?artnum=2238)

at the bottom here's some info about the pmu button reset.  Not sure if it is the same on your model:

[http://forums.appleinsider.com/showthread.php?t=61257](http://forums.appleinsider.com/showthread.php?t=61257)

---

### Post by Ecclesia on 2008-04-11
stream303 - thanks for the info.

Just for clarification here - I'd obviously want to replace the battery for the PRAM if I were going to use this machine (that is how this works, right?), but would this be the likely cause of the network issues?  If not, I'd rather not go through with trying to fix the pram.

Also, yes, the router is fine.  I am using this router with other machines.  I have also switched cables to one that is known to work, and switched jacks on the router.  The issue is somewhere on the imac.

---

### Post by stream303 on 2008-04-11
> **Ecclesia said:**
> Just for clarification here - I'd obviously want to replace the battery for the PRAM if I were going to use this machine (that is how this works, right?), but would this be the likely cause of the network issues?  If not, I'd rather not go through with trying to fix the pram.

I'm not sure myself that doing this would bring the network back to life either - unfortunately I don't own a G3 iMac.  I do know of some friends that do a "clean slate" on their machines before installing Linux by zapping the pram and doing a pmu/smu reset.

You can find the battery online, or if you are in the states Radio Shack has them.  I believe they are this model, but doublecheck it:

[http://www.radioshack.com/sm-tadiran-3-6v-2-100ah-aa-lithium-battery--pi-2104708.html](http://www.radioshack.com/sm-tadiran-3-6v-2-100ah-aa-lithium-battery--pi-2104708.html)

Worst-case, maybe you can go wireless.

Keep in mind that early model G3 iMacs have an 8Gb partitioning limitation - so if you choose a very simple install, keep everything at about 7.5 Gb max if you have upgraded the hard drive.  Or you can do extensive partitioning but keep the boot and root partition at 7.5 gb.

With OS/9 installed, you may be interested in a firmware update that you can perform (only available to OS8/9 on a hard disk) if you can get the firmware file on the machine:
[http://docs.info.apple.com/article.html?artnum=86117](http://docs.info.apple.com/article.html?artnum=86117)

This will allow you to install large amounts of ram, etc should you want to.

Warning!  I probably wouldn't mistakenly try using any OSX system-checker utilites on that machine - reports are that the utilities warn you that you have to upgrade the firmware first, and then when you back out, your machine is hosed and you have to go to extensive lengths to get it back to where you can boot it.  I haven't confirmed this yet with any ubuntu installs though.

Wish I had a guaranteed solution, but if it were me, I'd zap the pram, reset the pmu and cross my fingers. :)

---

### Post by ristosu on 2008-04-14
I don't think the battery would make any difference.

Check that you have the right driver module loaded:
```
risto@indigo:~$ lsmod | grep sungem
sungem                 38948  0 
sungem_phy             10432  1 sungem
risto@indigo:~$ 
```
This is from my iMac G3/350 with Ubuntu 6.06.1.

---

### Post by Midwest-Linux on 2008-04-14
I have two Imacs, one is a older version (tray loader) which had OS9 with it I too was unable to get on the internet. Since my plan at the time was to wipe OS9 off anyway, I went ahead and just installed Feisty 7.04 using the alternate CD install. I installed it and then I had internet with the Ubuntu despite the OS9 not being able to connect.

 So the Linux was able to find the network card and drivers but OS9 was dead as a door nail. If you do decide to install Linux use the alternate install disc for 7.04 PPC and go with Xubuntu especially if you have 256 Ram or less.

 If you decide to upgrade the ram, the older tray loader uses SODIMM Ram PC100 144 pin much like the PC100 for PC notebooks. The RAM replacement on that machine is a bit difficult since you must disassemble the unit to get at the RAM.

 If you have the newer slot loader, replacing Ram is a piece of cake. its located on the bottom of the unit and a little door just swings out and uses the PC100 168 pin SDRAM.

 Now, the network card could very well be dead too, but in my experience with my Imac it could be that the OS9 is just refusing to work with the network card for some reason and the cure is to install Linux.


[http://cdimage.ubuntu.com/xubuntu/ports/releases/7.04/release/xubuntu-7.04-alternate-powerpc.iso](http://cdimage.ubuntu.com/xubuntu/ports/releases/7.04/release/xubuntu-7.04-alternate-powerpc.iso)



[http://cdimage.ubuntu.com/ports/releases/feisty/release/ubuntu-7.04-alternate-powerpc.iso](http://cdimage.ubuntu.com/ports/releases/feisty/release/ubuntu-7.04-alternate-powerpc.iso)

---

### Post by stream303 on 2008-04-14
> **ristosu said:**
> I don't think the battery would make any difference.

Check that you have the right driver module loaded:
```
risto@indigo:~$ lsmod | grep sungem
```

I had forgotten about that!  In one of my installs, I was given the choice to choose between the regular ethernet or the ethernet-over-firewire, and definitely did NOT want the firewire-ethernet.  Wonder if that might be the case here..

Thanks for the memory jog...

---

### Post by Ecclesia on 2008-04-16
Thanks.  Unfortunately, I'm trying to install Debian here, since the machine has only 64mb ram.  It won't recognize the network card, or at least won't connect with it (this is a bit odd).  I'm guessing that it's a problem with the card. (other people installing Debian on similar systems didn't report having this problem) I think that I'm going to give up here, since fixing it at this point would require dumping some money (not a ton, mind you) into it to at least upgrade the ram, fix the PRAM and probably upgrade the hard drive.

Rather than go this route I'll just find another free/cheap computer to accomplish the same task.  I kind of like the imac though.  Maybe I'll find another one that works.

---


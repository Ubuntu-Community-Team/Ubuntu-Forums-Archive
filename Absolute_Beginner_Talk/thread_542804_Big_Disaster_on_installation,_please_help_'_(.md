---
title: "Big Disaster on installation, please help :' ("
date: 2007-09-04
forum: Absolute Beginner Talk
---

### Post by fredscripts on 2007-09-04
Hi! I'm in a very huge trouble.

In a computer without any OS installed, I want to install Kubuntu 7.04 (I have the CD and I've already done the installation on a laptop without any problem). The fact is that I follow the live CD installing the system (I make a partition of 10Gb mounted on / and a 1G swap partition) and then proceed as the live cd says. All is going fine. The livecd says to me that the installation is complete so I can restart the computer (removing the cd) and enjoy kubuntu.

So I restart (I remove the live cd), I see the grup message, I see the blue Kubuntu bar that tells to me that the very soon the Desktop will appear, but....when the progress bar is almost complete, the computer gets turned off. Absolutely, without any warning, the computer turns off completely and I have to press the power button again (and the same happens).

I've done the installation a couple of times deleting all partitions and so on and there's no way.

Please I really need help :(

---

### Post by GMachine_24 on 2007-09-04
> **fredscripts said:**
> Hi! I'm in a very huge trouble.

In a computer without any OS installed, I want to install Kubuntu 7.04 (I have the CD and I've already done the installation on a laptop without any problem). The fact is that I follow the live CD installing the system (I make a partition of 10Gb mounted on / and a 1G swap partition) and then proceed as the live cd says. All is going fine. The livecd says to me that the installation is complete so I can restart the computer (removing the cd) and enjoy kubuntu.

So I restart (I remove the live cd), I see the grup message, I see the blue Kubuntu bar that tells to me that the very soon the Desktop will appear, but....when the progress bar is almost complete, the computer gets turned off. Absolutely, without any warning, the computer turns off completely and I have to press the power button again (and the same happens).

I've done the installation a couple of times deleting all partitions and so on and there's no way.

Please I really need help :(

Hey Fred - sorry to hear you are having such problems. I've had problems with Kubuntu 7 also. Others have, too.

Just to be clear, you let Kubuntu do its live install, then click the "install" desktop icon and do you allow the computer to set the partitions? This always seems to be the best idea, especially if you are new. If you're setting the partitions yourself, try a reinstall where you let Kubuntu set the partitions (select "entire drive" when you get to the partitions question).

Otherwise, you might check this thread:

[http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=2955446](http://ubuntuforums.org/newreply.php?do=newreply&noquote=1&p=2955446)

It contains the travails of a few installer (including me).

I think this post (from that thread) would be a good place to start:

>  Re: Kubuntu 7.04 hangs/stops at boot-up
When the grub boot menu comes up, move to the ubuntu entry and press 'e' to edit the commands. A list of about 3 line will come up. The longest line will probably have the text 'splash' in it. Remove the word 'splash'. I can't remember exactly what you have to press to do this, but there's a short help message at the bottom of the screen. Once, you've removed splash, boot by pressing 'b' (I think!) It will boot ubuntu without the ubuntu logo so you can see exactly whats going on. This isn't premenant so don't worry about changin it back later. There's probably another option next splash which says 'quiet'. I'm not certain, but I think if you remove this too it will show more info. It certainly won't harm your system so its worth a try.

Btw, you might have to press a key at startup to get the grub boot menu if you are only running one system on your pc.

--This post is from Aquavitae (a veritable genius)
	

The good news is, this can be fixed. The problem is usually some errant code or something missing from your video display config file - which might come up later. Best to start at the beginning.

---


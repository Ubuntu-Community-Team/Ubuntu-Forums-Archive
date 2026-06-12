---
title: "Ack, dead internet"
date: 2008-01-18
forum: Absolute Beginner Talk
---

### Post by XanderKaplan on 2008-01-18
Okay, first of all, so far I love Ubuntu; it's a thousand times faster than Vista [blech], which I was running before.

I'm running a fairly low-end [scratch that, abolute lowest end] laptop and so this seemed to be the best choice that wouldn't kill my system every five seconds. However, since I installed earlier today I can't get on the internet through either a network cable or using my wireless [built into the laptop]...

For the wireless, the LED's turned off and so I assume it's not compatible or something, but for the ethernet, I cant figure out why it wouldn't work as on my other laptop I can get on fine [thus the thread]... When I switch it seems to have trouble acquiring a network address [or at least thats the step it gives up on]

ANY help would be appreciacted, and if you think it'd be easier to talk me through this, I've got AIM and MSN (xanderkaplan and xander_kaplan(at)hotmail(dot)com)

Thanks in advance!

---

### Post by pytheas22 on 2008-01-18
First we need to know what your hardware is:

Post the output of the command

```
lspci
```

And if you know them, what are the specifications of your system (motherboard, cpu, gpu, et cetera).

And by the way, did you think about using Xubuntu, a minimalist version of Ubuntu that might run even better on your old machine?

---

### Post by XanderKaplan on 2008-01-18
Yikes, okay... I'd have to retype all of it [two laptops] I will if it's really needed but I think I can find what you need

I'm assuming you're looking for the network card?.... Not sure which one of these it is, but my bet's on the second one...

06:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)
08:08:0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139

---

### Post by XanderKaplan on 2008-01-18
Oh, and Xubuntu: no I hadn't really looked into it and I might if it starts slowing down but so far it's been so smooth I'm not worried.

It's a Presario C500

Hardware
Memory: 494.4 MB
Processor: Intel Celeron M CPU     520 @ 1.60 GHz

---

### Post by pytheas22 on 2008-01-18
Exactly, those two cards are your ethernet and wireless interfaces.  I don't know why the ethernet won't work; I've never heard of it not working out-of-the-box in Ubuntu.  But I will try to do some research and get back to you (or feel free to google around yourself for something like "realtek ethernet ubuntu driver."

Broadcom wireless I know well because I have it as well in a laptop.  It doesn't work out-of-the-box because it requires non-free drivers that Ubuntu doesn't ship.  This is really easy to fix by downloading one package, but the problem is that you don't have any Internet connection right now, so give me a few minutes to think about working around that and I think I'll be able to tell you how to get the wireless to work.

---

### Post by XanderKaplan on 2008-01-18
Well, I do have a rewritable CD and a second laptop so if transferring between computers is the problem I can do that

---

### Post by pytheas22 on 2008-01-18
ok, so this should work:

(I am assuming that you have a USB drive or something to transfer files from your working laptop to your Ubuntu one).

First, download these two files and put them on your USB drive:
1. the non-free firmware: [http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o](http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o)
2. the package to install fwcutter, a program to extract the firmware: [http://mirror.clarkson.edu/pub/ubuntu/pool/universe/b/bcm43xx-fwcutter/bcm43xx-fwcutter_006-3_i386.deb](http://mirror.clarkson.edu/pub/ubuntu/pool/universe/b/bcm43xx-fwcutter/bcm43xx-fwcutter_006-3_i386.deb)

Next, transfer those files to your Desktop on Ubuntu.  First install the fwcutter package: just click on it and it should launch an installer (you will have to enter your root password).  It will probably ask you if it should fetch the firmware automatically; click no since you don't have a connection.

Then open a terminal and type these lines:
```

sudo bcm43xx-fwcutter -w /lib/firmware ~/Desktop/wl_apsta-3.130.20.0.o
sudo bcm43xx-fwcutter -w /lib/firmware/`uname -r` ~/Desktop/wl_apsta-3.130.20.0.o
```

which will extract the firmware.

Then if everything has gone smoothly so far, reboot and your wireless card should be working.

There are some possible things that could go wrong with these steps, but try them and let me know.

---

### Post by pytheas22 on 2008-01-19
In the meantime, I've done some research on your ethernet problem, and it looks like there is indeed a bug with some Realtek cards on Ubuntu.

This post provides a possible answer: [http://ubuntuforums.org/showthread.php?t=538448](http://ubuntuforums.org/showthread.php?t=538448)

---

### Post by XanderKaplan on 2008-01-19
after typing the first line it says

[sudo] password for xxxx:

but doesn't actually allow me to type anything???

---

### Post by pytheas22 on 2008-01-19
just type your password and press enter--you don't see the characters for security reasons

---

### Post by XanderKaplan on 2008-01-19
heh, so i realized, sorry that was a pointless post

---

### Post by XanderKaplan on 2008-01-19
YES!... LEd's on and It's scanning correctly; not quite on yet but just wanted to say that

---

### Post by pytheas22 on 2008-01-19
that's good! hopefully you'll be able to connect too

---

### Post by XanderKaplan on 2008-01-19
hmmm... no success when I tried joining... I see 3 1/2 bars but it just sits there Attempting to Join the wireless network... for a minute or so before giving up

---

### Post by pytheas22 on 2008-01-19
that's strange; it should connect if you have a strong connection.  Try rebooting and trying to connect again.  If you can, get closer to your router.  And is your router using WEP or WPA?

---

### Post by XanderKaplan on 2008-01-19
ehm... well right now MY router's dead..... but my neighbor's router ;-).. is.. netgear

EDIT: Oh, and it works fine on my other laptop

---

### Post by pytheas22 on 2008-01-19
It could just be that you're too far away.  If you move around it could help--literally a few centimeters in either direction makes a huge difference at long ranges (I know from my days of stealing the neighbors' connection...).  It could work on your other laptop but not the Ubuntu one because the former has a stronger wireless card.  Either way, if you can see networks, then the card should definitely be working.

When you tell it to connect, what happens?  Does one green dot light up, and the swirls spin for a while, and then eventually it gives up?

---

### Post by XanderKaplan on 2008-01-19
well pre-ubuntu I got it in this same spot...

but when I last posted it'd show both dots, both off, and show the animation but then eventually give up, but now for some reason when I go to connect it just shows four grey bars.... and then at one point it showed three blue bars but I couldn't access the internet :-\... it doesn't even seem to try to access it...

---

### Post by pytheas22 on 2008-01-19
hmmmm, I don't know, that behavior is strange.  At least one dot should light up.  I will think about this and try to get back to you, or you can do some research for something like "BCM94311 Ubuntu can't connect."  Unfortunately I need to go soon so I may not be able to respond rapidly (or until tomorrow sometime).

You can also in the meantime try getting the ethernet to work using this link, as I posted before: [http://ubuntuforums.org/showthread.php?t=538448](http://ubuntuforums.org/showthread.php?t=538448)

---

### Post by XanderKaplan on 2008-01-19
this is so sketchy: update, I restarted again and one lit up but it eventually gave out. The weird thing, when it gave out, so did the LED for the wireless......and now it wont turn on, im sure restarting will fix that, but its seriously weird

---

### Post by pytheas22 on 2008-01-19
It could be that the version of the firmware that you used is not good (the firmware is basically the Windows driver and there are lots of different versions).  Here's a different firmware to try: [http://svit.epfl.ch/stuff/wl_apsta.o](http://svit.epfl.ch/stuff/wl_apsta.o) .

to use it, first move it to your Ubuntu desktop as you did with the first one

then delete the old firmware files:

```
sudo rm /lib/firmware/bcm*
```

then repeat the fwcutter step, but with the new version of the firmware:

sudo bcm43xx-fwcutter -w /lib/firmware/`uname -r` ~/Desktop/wl_apsta.o

and reboot, and hopefully it will work better.

If this doesn't work, there's another method of getting your wireless card going using a program called ndiswrapper.  It's very well known and there are lots of guides for it so you might be able to figure out how to use it yourself, but if you can't I can try to help you out tomorrow, if the second firmware attempt fails.

For now I'm out.

---

### Post by pytheas22 on 2008-01-19
Actually I got more time, so here is an alternate method to try using ndiswrapper instead of the native Linux driver for your card.  It's complicated but the directions should be straight-forward.  I adapted this from [http://invaleed.wordpress.com/2007/11/20/install-bcm94311mcg-wlan-mini-pci-ubuntu-710/](http://invaleed.wordpress.com/2007/11/20/install-bcm94311mcg-wlan-mini-pci-ubuntu-710/) to address your lack of an Internet connection.

1. clean stuff up:

```
sudo apt-get remove ndiswrapper-common ndiswrapper-utils-1.9
```

you probably don't have these installed so it will say it can't uninstall them; just ignore it and go to the next step

```
sudo apt-get remove bcm43xx-fwcutter
```

blacklist the bcm43xx driver: type

```
sudo gedit /etc/modprobe.d/blacklist
```

and in the text file that comes up, add the line

```
blacklist bcm43xx
```

to the end of the file and save the file.

2. Reboot.

3. while the Ubuntu laptop is rebooting, you can download the stuff you need and get ready to transfer it to the Ubuntu laptop.

First download the Windows driver for your card here: [http://rapidshare.com/files/70969505/WLANBroadcom.tar.gz.html](http://rapidshare.com/files/70969505/WLANBroadcom.tar.gz.html) (click through the steps till you get to the download).

Also get the ndiswrapper source from [http://downloads.sourceforge.net/ndiswrapper/ndiswrapper-1.49.tar.gz](http://downloads.sourceforge.net/ndiswrapper/ndiswrapper-1.49.tar.gz).

Transfer both of these files to the desktop of your Ubuntu laptop.

4. Prepare to compile ndiswrapper:
```

sudo apt-get install build-essential
sudo apt-get install linux-headers-`uname -r`
sudo ln -s /usr/src/linux-`uname -r` /lib/modules/`uname -r`/build
```

5. compile it:

Right-click on the icon for the ndiswrapper tarball that you have on your desktop and select "Extract Here."

Then open a terminal and type 

```
cd ~/Desktop/ndiswrapper*
```

type these lines to actually to the compile:
```

make distclean
make
sudo make install
```

it will probably take a few minutes for your system to build the binary

6. finally, "install" the Windows version of the driver into ndiswrapper:
```

cd ~/Desktop/WLANBroadcom/
sudo ndiswrapper -i bcmwl5.inf
ndiswrapper -l
```

hopefully it will say something like "driver installed, hardware present"

type

```
sudo gedit /etc/modules
```

and add this line to that file:

```
ndiswrapper
```

and do this to load the new module:

```
sudo modprobe ndiswrapper
sudo ndiswrapper -m
```

and then reboot, and hopefully it will work!

I know this guide is complicated, but it's written by someone with the same computer manufacturer and the exact same wireless card as you, so it has a high probability of working.  Let me know how it goes.

---

### Post by XanderKaplan on 2008-01-19
alright, well, the driver link is dead so I went ahead and found another.. idk if its the same thing but we'l find out in a bit.

---

### Post by pytheas22 on 2008-01-19
hmmm, you're right..that's strange, the link was definitely working last night.  In any case it shouldn't matter; all you need are the Windows drivers for your card which you can download from lots of places or maybe you even have on a CD that came with your computer.  If the name of the driver you get is different than the one in the tutorial, you will need to change the commands a little to reflect the different filename, but it shouldn't be too hard to figure out.

---

### Post by XanderKaplan on 2008-01-19
yeah thats what I did but it didnt work n(dled a different one and changed the paths) It installed but I restarted and nothing was different... (wel, actually, it was worse, the LED wouldn't light up)...... i dont think I got the right type of driver and I don't have the CDs...... any chance you could send me a link?

---

### Post by pytheas22 on 2008-01-19
I'll look, or hopefully that site will come back up...I wish I'd just downloaded it last night myself.

In the meantime it could just be that your card is installed but not "up;" post the output of

```
iwconfig
```

---

### Post by pytheas22 on 2008-01-19
here are some other drivers to try.  Repeat the process from the beginning so that you clean up all of the old stuff.  The driver links are at the bottom of this post.  If the first one doesn't work, try the second.

EDIT: I posted a third one to try as well if the two others fail.  I am getting this from [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff) .

---

### Post by ugm6hr on 2008-01-19
Don't want to interfere with this process, but this might be the problem with the wired ethernet:
[http://ubuntuforums.org/showpost.php?p=4077372&postcount=14](http://ubuntuforums.org/showpost.php?p=4077372&postcount=14)

It is an issue wirh power saving function in Windows.

---

### Post by pytheas22 on 2008-01-19
yeah, I was reading about that.  I think there's no Windows system on the laptop in question anymore so it can't be reset by accessing it in Windows as that post describes.  But I read somewhere that if you turn off the machine and disconnect the battery for a little while, it should reset the ethernet card to make it work.  But I imagine that getting wifi to work would be even nicer.

---

### Post by XanderKaplan on 2008-01-19
YES, im on, posting from my ubuntu laptop... Wireless is working fine, 

[for anyone who ended up on this page & has the same problem]
the key was making sure to remove all the old drivers because

sudo ndiswrapper -l

would show that the drivers were failing or broken or something, so 

sudo ndiswrapper -r xxxxxxx

and then

sudo ndiswrapper -i xxxxxxx

oh and make sure you leave the inf inside the folder or else it can't access the sys file too

---

### Post by pytheas22 on 2008-01-19
nice!  glad it finally worked, and hope you enjoy Ubuntu

---

### Post by pytheas22 on 2008-01-20
by the way, in case you don't know, you will probably need to recompile ndiswrapper the next time you update your kernel, as it won't be updated via the package manager.  So it would be a good idea to keep the ndiswrapper source on your machine so that you can just make, make install again when you need it.  I don't think that you need to reinstall (ndiswrapper -i) the Windows driver itself though.

And for the benefit of anyone else who might find this thread, which of those drivers did you end up using?

---


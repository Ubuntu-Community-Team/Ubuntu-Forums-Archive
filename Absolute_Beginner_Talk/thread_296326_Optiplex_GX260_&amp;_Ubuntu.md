---
title: "Optiplex GX260 &amp; Ubuntu"
date: 2006-11-09
forum: Absolute Beginner Talk
---

### Post by nholt on 2006-11-09
I am new to ubuntu and to linux. I have never loaded it or used it. I have just heard great things about it.

I have been looking for a version of linux that I could use in our hospital. I like what I see with ubuntu. However, I have been trying to install 6.10 on a Dell Optiplex GX260 but in the compatibility sheet I found where it is compatible with 4.10 Warty. I have tried to download 4.10 from [http://old-releases.ubuntu.com/releases/4.10/](http://old-releases.ubuntu.com/releases/4.10/) but it says: You don't have permission to access /releases/4.10/warty-release-install-i386.iso on this server.

So now what?:confused: 

The system hangs after you tell it to start using the live cd. The cursor will just blink in the upper left hand corner of the screen.

---

### Post by taurus on 2006-11-09
Are you trying to install Ubuntu on your Dell?  If you are, try using the alternate CD.  However, I recommend you use Dapper since it's nore stable and has three years support.

[http://ftp.ussg.iu.edu/linux/ubuntu-releases/6.06/](http://ftp.ussg.iu.edu/linux/ubuntu-releases/6.06/)

---

### Post by nholt on 2006-11-09
I have download 6.06 Dapper. When the live Cd menu comes up and after choosing start it goes through the startup process and the last thing I catch is "Starting HP Linux......" then the screen turns black and the cursor is in the upper left hand corner for while and then in a little bit I get two white rectangle boxes turned on end, one is on the left side of the screen middle and the other is in the middle of the screen. The system is doing nothing at that point.

---

### Post by taurus on 2006-11-09
There could be a problem with the onboard Intel graphic card controller!  May want to use the alternate CD to install it on the Dell machine then.

---

### Post by K.Mandla on 2006-11-09
I'm using a GX260 right now, and chances are that white-box thing has to do with the onboard graphics. 

If you decide to try and install Ubuntu 6.06.1 on the hard drive, you'll see the same thing for a short while, but when you reboot the computer for the first time everything will work fine. As far as I can tell, that white-box problem happens when Ubuntu tries to probe the onboard graphics, but can't switch back. It's a quirk, but kind of renders the live CD useless.

If you want to try out Ubuntu but don't want to install it, you could put that live CD in a different computer (probably not another GX260 ;) ) and see how it works for you. Good luck!

---

### Post by nholt on 2006-11-10
Okay. I have just ried to install 6.06.01 to the GX260 using the alternate CD. Yes I have the whit-box thingymabob again. You stated for a "short while" I'll just let it sit there then or should I go ahead and reboot.

I have tried Ubuntu and I am going to partition my laptop and load it on there also as a boot option. But I need to be able to load it on the GX260's as we have a dozen of these around the hospital and I need to get used to it and be able to load and test our other applications.

---

### Post by nholt on 2006-11-10
It's Loaded! The two white blocks will stay on your screen for 15-30 minutes and then the CD will kick open. At which time you can reboot the machine.  :-D 

Thanks for your help!

---

### Post by K.Mandla on 2006-11-11
No problem! Glad it worked! :D

---

### Post by ale8oneboy on 2007-02-12
I have noticed this trend as well on most Dells with onboard video. I've even had users report simular problems with Windows XP (forgive me for speaking of MS on my first post).

---

### Post by andrew.46 on 2007-04-27
Hi,

 My ears pricked up when I saw the GX260 mentioned:

> **ale8oneboy said:**
> I have noticed this trend as well on most Dells with onboard video. I've even had users report simular problems with Windows XP (forgive me for speaking of MS on my first post).

 Well I have a Dell GX270 that does not have this problem. Mind you I altered the shared video memory from 1 to 8 megs in the BIOS before I loaded the OS. Not sure if you can do this with the GX260 though.

                      Andrew

---

### Post by rrinker on 2007-06-28
> **andrew.46 said:**
> Hi,

 My ears pricked up when I saw the GX260 mentioned:



 Well I have a Dell GX270 that does not have this problem. Mind you I altered the shared video memory from 1 to 8 megs in the BIOS before I loaded the OS. Not sure if you can do this with the GX260 though.

                      Andrew


 Yes, you can. I just installed 7.04 on a GX260 and it worked fine. I set the video to 8MB before installing and I can get all supported resolutions. Certainly not my first Ubuntu install, but it went very smoothly. The only problem I had was that I started liking the way this little (it's on of the slimline desktop GX260's, not the mini-tower one) machine was working that I decided to repalce the 20GB drive with a larger one I had and I duplicated it with Ghost and it would no longer boot. Manually fixing up GRUB solved that and I'm happy once again. I've considered ading a slightly betttr video car,d but since it will only take low profile cards which aren't too easy to obtain, I've let it go for now. The GX260 make an excellent Ubuntu box, IMO. Mine is a 2GHz P4 with 512MB L2 cache, 1GB RAM, and an 80GB HDD.

                                                --Randy

---

### Post by bluepolo on 2007-07-05
I had this problem with my Dell SX260.

It seems the problem with some Dells with the builtin 810 chipset is that the OS cannot override the BIOS. The answer is to change the BIOS VRAM size to 8Mb.

If you are here because you got this problem _after_ installing Ubuntu, then you need to boot from the ALT CD and go into recover mode. Go through all the options, and eventually you get asked if you want a shell in the root.

Accept this option, and at the subsequent prompt re-configure X by running

# Xorg -configure

then restart.

Worked for me, hope it works for you as well.

Cheers

BP

---

### Post by preachergirl on 2007-09-19
Hi, I downloaded the ubuntu 7 dont remember the exact number, but i cant get it to boot my Dell gx260. It has nothing on it, we are refurbishers for a not for profit outreach. All I get is the menu when I tried to install the screen goes blank and stays that way for a while. Is that normal and should I wait longer. I'm kind a thinking my downloads are right. I downloaded directly from the ubuntu website. Help please.

---

### Post by CharlieHorse73 on 2007-09-27
I had the same problem with a GX260 with integrated video as well.  My fix was to change the BIOS from 1Mb to 8Mb, but that still did not work.

What did finally work for me was to downgrade the BIOS from A09 to A06.  Hope this helps.

---

### Post by mramsey on 2007-09-27
I have installed 6.10 and 7.04 successfully on Dell Optiplex GX110, GX250, GX260, GX270, and GX280 models with no problems. Also installed on Dell Lattitude laptops with no issues.:)

---


---
title: "Pre-flight check"
date: 2009-03-08
forum: Apple Hardware Users
---

### Post by hictio on 2009-03-08
Hi there,

I'm considering getting a 12" PowerBook, specifically the 1 GHz model, with 1.25 GB RAM.
The idea is test it with Intrepid, I have been Googling, but I have found nothing definitive that will list what to expect.

I know that you have to install from the "Alternate Install CD", ok, and from there, I guess that you issue a 'sudo aptitude install gnome-desktop'; and get a working Gnome environment; but, is there anything else to expect?

I mean, to be used as a workstation, what does not properly work on Intrepid PPC?

VLC?
Flash?
3D aceleration/ Desktop Effects? (yeah, right... :) )
Sound?
Wireless card?

Please, if someone has a link, or can post here what does work, that'll be wonderful.

As usual, TIA :D

---

### Post by zmatt on 2009-03-08
I'm actually about to attempt an install of 8.1 on my 1.33ghz 12inch power book. I will let you know how it turns out. I didn't know you had to use the alternate install though. I guess that's good to know. it will save me from a headache.

---

### Post by hictio on 2009-03-08
> **zmatt said:**
> I'm actually about to attempt an install of 8.1 on my 1.33ghz 12inch power book. I will let you know how it turns out. I didn't know you had to use the alternate install though. I guess that's good to know. it will save me from a headache.

Many thanks!
Here is the info regarding the Intrepid PPC install: 

[Re: PowerPC - How to upgrade from Ubuntu Hardy Heron (8.04) to Intrepid Ibex (8.10)](http://ubuntuforums.org/showpost.php?p=6071373&postcount=5)

Actually, I expressed myself bad, the Alternate CD its the only way, unless you chose to install the server version.

Thanks again.

---

### Post by mkvnmtr on 2009-03-08
The alt install disk will put the whole system on your machine. You should not have to use the command line unless you want to do a minimal install. I have done that on my G4 Ibook and it is not required. Infact the live disks will boot up and run with just a little effort.

---

### Post by hictio on 2009-03-08
Thanks a lot.
I'm really not worry about the install per se, but as what to expect once its done.
What will it work, and what doesn't.

I found this [Ubuntu PowerPC FAQ](https://wiki.ubuntu.com/PowerPCFAQ), which sheds a lot of light onto things, but perhaps another user might other tips regarding that particular model.

As usual, TIA :D

---

### Post by zmatt on 2009-03-09
Seems I have run into a wall. The installer cannot detect my cd drive, the irony of a cd based installer not being able to find the cd drive has already struck me. Does anyone know how to work around this? It wants me to load a different cd module but I don't know where to start.

---

### Post by tiresia on 2009-03-09
> **zmatt said:**
> Seems I have run into a wall. The installer cannot detect my cd drive, the irony of a cd based installer not being able to find the cd drive has already struck me. Does anyone know how to work around this? It wants me to load a different cd module but I don't know where to start.
[http://ubuntuforums.org/showthread.php?t=964904](http://ubuntuforums.org/showthread.php?t=964904)

---

### Post by zmatt on 2009-03-09
For some reason the ctrl+alt+F2 combo doesn't want to work. I am using a 12inch power book G4. Is there a default keyboard layout that I can choose instead of keyboard detection that will work? I already tried apple Macintosh and apple laptop neither worked with the ctrl+alt+F2 combo.

---

### Post by tiresia on 2009-03-09
I don't have a Power Book, but it looks like you have to use also the Fn-Key. 
Try something like Ctrl-Alt-F2-Fn

---

### Post by zmatt on 2009-03-09
ok I got it to work with fn+option+F2. I ran the modprobe command and followed the instructions. No dice, it says my disc couldn't be mounted. 


EDIT:
I tried again, things seem to be working. I'll report back how things go.

---

### Post by zmatt on 2009-03-10
ok, I got 8.04 up and running. fo rosme reaosn my 8.10 discs were giving me trouble, I think my iso was corrupted, and a friend had ppc 8.04 laying around. 

Anyways, out of the box sound, bluetooth, dvd, ethernet etc all work. Wifi of course will need work and I haven't tested hibernate and suspend yet. 

I noticed my laptop gets a lot hotter now. I know the chassis is supposed to act as a heatsink so it isn't a system issue as much as it is a comfort one. 

I will get back to you as soon as I get everything configured right. As things stand I need to;
Get Wifi working
Configure the KB for Mac
Configure the mouse for Mac
Install all audio and video codecs
And make sure that hibernate and suspend work fine.

---

### Post by hictio on 2009-03-10
Hey, thanks a lot for the posts!
I'm still trying to get my hands on the PowerBook, the deal went down, so I'm still searching for a nice deal on a used one.

---

### Post by tiresia on 2009-03-10
> **hictio said:**
> Hey, thanks a lot for the posts!
I'm still trying to get my hands on the PowerBook, the deal went down, so I'm still searching for a nice deal on a used one.
If you want just to see how Ubuntu can work on your Hardware, you can download the LiveCD of Hardy (8.04) You have enough Ram to run it.
As always, if you have video issues, try at boot up```
video=ofonly
```
To see the different options, hit TAB at the first yaboot prompt. 
Nosplash will help you to check what happens during booting

---

### Post by zmatt on 2009-03-11
This is an interesting problem. I don't think its powerbook related. After the installation i let the update manager do its thing. After the reboot I have lost all privileges. I try to start the network manager and it says the configuration cannot be loaded because I am not allowed to access it. I tried sudo commands in the terminal and got this:

could not find compatible GRE between version 1.9.0.1 and 1.9.0.*

As best I can tell, it seems the updates broke something in the privileges system.

EDIT:

I got firefox to work with this line:

sudo xulrunner-1.9 --register-global


However permissions are still jacked up. I enabled root and logged in. I'm still denied access in simple things like the network module.The updates seriously broke permissions. I find it odd this would happen to the LTS release, the one meant for servers and mission critical stuff.

Oh and clicking the Quit icon makes Gnome freeze. 

I'm considering a reinstall and just running without updates.

---

### Post by hictio on 2009-03-11
> **zmatt said:**
> 
~snip~
I'm considering a reinstall and just running without updates.


That's a total drag, man... Even a show stopper on my case, at least, for an OS that I plan use day to day... I mean its Ok if you can't install any update and use the box to test it a few days, but day in day out, I would be really worried w/o updates and patches.

---

### Post by zmatt on 2009-03-14
ok, I have gotten 8.10 installed. Much smooth process than 8.04. I dunno what they changed, but so far so good. I don't have a spare Ethernet cable laying around, so I will have to wait till tomorrow to run the updates and work on WiFi.

---

### Post by zmatt on 2009-03-31
Sorry fore the lack of updates. WiFi works....sort of. Encryption support is non-existent, but open APs work fine and my signal strength on average is better than in MacOS. Flash doesn't work. I installed swf-player but that crashes Firefox. Bluetooth seems to work, but I haven't actually tested it. Battery life is ok considering I still have the original battery. And  weird thing happens on bootup. When I boot with the laptop plugged into the wall it freezes on startup. The same thing happens when I boot with Ethernet plugged in.

---

### Post by stream303 on 2009-04-03
I had that model and one of the very first things you'll want to install to ensure that cpu-frequency scaling is taking place is cpudyn, otherwise your machine will be running a bit hot. :)

Also, only on that machine Network Manager was one process that chewed up 100% of my cpu time all the time.  I had to actually disable / uninstall Network Manager.  On my other ppc boxes, no problem, but on the 12" ibook - NM was a showstopper.

You can check by using the TOP command, or perhaps see it better by downloading HTOP, which I really like.

If you can tackle these two issues, I have a feeling that your ibook should settle down.

---

### Post by zmatt on 2009-04-03
> **stream303 said:**
> I had that model and one of the very first things you'll want to install to ensure that cpu-frequency scaling is taking place is cpudyn, otherwise your machine will be running a bit hot. :)

Also, only on that machine Network Manager was one process that chewed up 100% of my cpu time all the time.  I had to actually disable / uninstall Network Manager.  On my other ppc boxes, no problem, but on the 12" ibook - NM was a showstopper.

You can check by using the TOP command, or perhaps see it better by downloading HTOP, which I really like.

If you can tackle these two issues, I have a feeling that your ibook should settle down.

Well I'm on the powerbook now. It's running pretty cool and network manager isn't giving me nay trouble. I would really like to know bout flash. Gnash gives me animations and ads, but no youtube. So in effect my web browsing experience is now worse, since I have flash ads.

---

### Post by stream303 on 2009-04-04
Some can get gnash to work with PPC, but not always.

I'm not a big flash user, so I cure that problem by not relying on flash-driven sites. :)  But yes, flash and no 3D video really kind of forces one to use a ppc Linux box for other uses.  It is just the way it is ...

---


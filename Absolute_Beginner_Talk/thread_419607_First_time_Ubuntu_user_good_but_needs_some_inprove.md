---
title: "First time Ubuntu user good but needs some inprovements"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by Unetwork on 2007-04-23
[COLOR="Blue"]Hello to all. 
Am a first time user with 7.04 did some install some time ago of Linux this for a firewall between my other PC’s with 2 network cards. 
But to say that beside giving rights to my Dreambox  with the chmod I am absolutely fresh.
I would first of all like to thank every one who develeloped Ubuntu I can only imagine how much time went into this!
Great thank you all ;)

Here are my experiences with Ubuntu:
Install went very nice and smooth.
My professional sound card worked right away and that really surprised me! With Vista I did have to wait for months to get any sound on my PC. And that was the main reason I erased Vista that came with a official license on my new PC. 
I am in the business of audio and video editing/recording so need something that will work.
In fact I don’t think that Linux can do the same job yet as editing software made for Windows and Mac can do but it does look so much better!

Now when trying to install dual screen with Ubuntu that where I ran into problems!
All advise from other experienced Ubuntu users made my system fail and even when I used the recovery as option 2 on the boot screen the only way was for me to setup Ubuntu from the start  again.
I saw that with Nvidea cards will not have that problem but changing my video AGP card (radeon ATI 9250) for a operating system is going to far.
I am wondering why the basic functions will not work from ATI with Ubuntu such as dual screen.
Also Ubuntu is still far too difficult for beginners.
To download drivers lets say for ATI t comes with a “run” extension and this does not work.
Also Skype-VOIPBuster does not work and that might be also a reason for many not to use Ubuntu.

But in general I see this going on the right way as it sure looks and works fine.
I will keep this like a dual boot on one of my PC’s and will check in to see if the Ati problem will e solved as making  a search seeing that many are having just that problem too.
[/COLOR]

---

### Post by aberry5555 on 2007-04-23
ATI is a PAIN on linux, I have had too much experience trying to make it work, though I expect in the coming months ATI will do better and make working packages, as Dell, the biggest single computer manufacturer in the world, are going to be selling their PC's with Linux soon (maybe Ubuntu, maybe another distro, who knows but it can only be a good thing :) ) and, as they mostly use ATI, the company would be making a massively wrong move if they didn't get their drivers in order. As for your audio and video editing software it could well work in Ubuntu, as it has a Windows emulator program that you can download via synaptic but it might take a bit of fiddling to get it up and running. I think a good idea would be to post up your experiences with your software and see if anyone has managed to overcome any difficulties.

As for installing things go, you're right, Linux lacks and desperately needs a unified method of installation, that isn't depenendent on individual distros, maybe a .install file and an auto-sensing script for the distro. Saying that, though, I wouldn't know where to start even proposing something like this myself so I can see why it hasn't been set up yet.

Hopefully you can find a way around the problems you're having, I can guarantee the Ubuntu team and it's users will provide much more intelligent and helpful tech support than microsoft does!

---

### Post by Unetwork on 2007-04-23
> Hopefully you can find a way around the problems you're having, I can guarantee the Ubuntu team and it's users will provide much more intelligent and helpful tech support than microsoft does!
Well that's for sure ;)
I am very pleasant surprised with all the help users and mods are giving me.
I do hope there will be a universal install methods to make all much easy than going all the time in shell.

I heard that  lots did solve the problem with dual screen Ati 9XXXX cards. but this needs to be done with manual typing and there it goes wrong so many times.
I am for 3 days now busy trying to get my 9250 Radeon working but no success yet.
Instead I did have to do more than 4 times a setup again.

Also a pity that Skype is not working like MSN does in Ubuntu...

But I will use your ideas like synaptic and will keep you posted.
Again thanks for the reply and regards, Peter

---

### Post by Unetwork on 2007-04-23
Hello again problems, now I can't get into the system following the sticky about ATI Radeon card.
Is there a way to recover the last config edit? Or should I make a brand new install again?

---

### Post by aberry5555 on 2007-04-23
If you have a command-line try 

```
sudo dpkq-reconfigure xserver-xorg -phigh
```

and restart

---

### Post by Unetwork on 2007-04-23
Ok thanks aberry will try that the next time when I do something stupid ;)

---

### Post by stimpsonjcat on 2007-04-23
> **Unetwork said:**
> Also a pity that Skype is not working like MSN does in Ubuntu...
the reason why msn works so well is that the specifications of the msn protocol are freely available. skype uses a proprietary (and AFAIK even encrypted) protocol. there used to be a proprietary skype client for gnu/linux but it is no longer being maintained.

as for your audio editing needs, check out [ubuntu studio]("http://ubuntustudio.org/"), an ubuntu derivative designed for multimedia enthusiasts.

> I am wondering why the basic functions will not work from ATI with Ubuntu such as dual screen.
such functions have to be provided by the video driver. linux developers [have offered]("http://www.kroah.com/log/2007/01/29/#free_drivers") all hardware companies free linux driver development. all they need is proper documentation regarding hardware specifications, but nvidia and ati refuse to make any documentation about their newer cards available. that's basically why 3d acceleration sucks on linux unless you have an intel card (free drivers available directly from intel) or put up with proprietary drivers which are not includable in ubuntu by default because of incompatible software licenses.

if your card is supported by the 'radeon' driver you could try to get dual head to work using ['mergedfb']("http://www.thinkwiki.org/wiki/Additional_options_for_the_radeon_driver"). that's how I managed to hook up my external TFT screen to my laptop.

---

### Post by Unetwork on 2007-04-23
Okidoki  stimpsonjcat  thanks for the detailed reply.
Its very strange that in lets say Automatix Skype is there for download but it is not working.
Also on the Skype website there are drivers for Skype only they do not work for Ubuntu.....

But with more and more users coming to Ubuntu I guess those hard heads will be forced to work on this.
I wrote several times to Ati why the drivers don't work and guess what? Did not even get a single reply..
Well the next time I know which card to purchase and which not...
Strange is also that with a friend of mine Nvidia is working much better than Radeon but that might have something to do with the chipset as we have the same motherboard Asus K8N-E de luxe with, guess what, nvidia chipset like the AGP controller.

I do appreciate all the work of the Ubuntu team I hope that installing will be a lot easier in the future.
Cheers :guitar:

---

### Post by Unetwork on 2007-04-23
Hi again, well the link you gave me is too difficult for me.
I really won't know what to edit and how to do so...
Also the extra links on that page are not working (dead links)
But any way thanks again for your help, I guess Ubuntu is too complicated for me as a beginner, I know Windows sucks but at least I know what to do when I need to install something ;)
Cheers, Peter

---

### Post by stimpsonjcat on 2007-04-24
Automatix is a third party project and not recommended by the ubuntu developers (they even [criticsed]("https://wiki.ubuntu.com/CommonCustomizations") it for [breaking]("https://lists.ubuntu.com/archives/ubuntu-devel/2006-November/022185.html") release upgrades). with feisty, it has become a lot easier to install most audio/video codecs and proprietary software without using automatix. for help with that, consult the wiki: [https://wiki.ubuntu.com/RestrictedFormats]("https://wiki.ubuntu.com/RestrictedFormats")

I don't know why skype doesn't work. I use ekiga for internet telephony which is based on a free Voip standard (SIP). ekiga is installed by default in ubuntu (Applications >> Internet >> Ekiga).

your friend's nvidia card probably works better because Nvidia's linux driver supports it while Ati doesn't support your radeon card. the free radeon drivers included in ubuntu were created using a technique called reverse engineering. this is very difficult, especially with complicated video hardware, hence the reduced functionality.

I remember there used to be a problem with some nForce chipsets related to a reverse engineered network interface driver (again, lack of documentation). I don't think this has anything to do with your problem though.

---

### Post by stimpsonjcat on 2007-04-24
> **Unetwork said:**
> the link you gave me is too difficult for me.
I really won't know what to edit and how to do so...


OK I'll try to walk you through. I'll suppose both monitors use identical resolutions (1024x768) and you want a side-by-side configuration.

First, you should create a backup of your current configuration so you don't get into too much trouble if things go wrong :)
tip: you can copy/paste the following commands using the middle mouse button (this works everywhere in ubuntu!). mark text to be copied and insert using the middle button (very handy isn't it?! :guitar: )

to make a backup, open a terminal (Applications >> Accessories >> Terminal) and type
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.orig
```
then open the X configuration file for editing:
```
sudo gedit /etc/X11/xorg.conf
```
you'll get prompted for your password.
under the Device section, add this line:
```
Section "Device"
[...]
Option "MergedFB" "True"
```
To specify the physical position of the second monitor (RightOf, LeftOf, Above, Below, Clone is the default)
```
Option "CRT2Position" "RightOf"
```
--------------------
EDIT: just checked the manpage. the following step is optional if your monitors use equal resolutions.
then you need to create the 'virtual desktop'. the virtual desktop is the total size of the desktop. if you have two monitors with 1024x768 resolution side by side, the virtual desktop will be 2048x768. (Note that the 3D engine is limited to 2048x2048). edit all "Display" subsections under the "Screen" section to look like this (Add the "Virtual" ... line):
```
Section "Screen"
[...]
SubSection "Display"
Depth 24
Modes "1024x768"
Virtual 2048 768
EndSubSection
```
---------------------

That's it. Save the file and reboot your computer with both monitors attached.

in case something goes wrong and the graphical user interface does not start, simply boot ubuntu in rescue mode and type
```
cp /etc/X11/xorg.conf.orig /etc/X11/xorg.conf
```
and then reboot:
```
shutdown -r now
```

If you want to use monitors with unequal resolutions, consult the manpage of the radeon driver (type 'man radeon' in a terminal) hint: read the sections about MergedFB, CRT2Position, and MetaModes.

This should get you started. If it doesn't work, let me know and post your xorg.conf file here.

---


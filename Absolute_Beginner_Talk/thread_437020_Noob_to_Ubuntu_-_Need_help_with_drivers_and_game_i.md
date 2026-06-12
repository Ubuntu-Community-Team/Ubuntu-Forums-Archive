---
title: "Noob to Ubuntu - Need help with drivers and game installs - Core 2 duo - 8800gtx PLZ"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by MR Spade on 2007-05-08
Ok well after microsoft annoyed me for the last time.

So now i have Ubuntu 7 (the fiesty  one :P) 

I have install wine and beryl but done nothing much else. I dont really know that much but i kinda like here already.

These are my following aims that i need guidence on.

Installing the drivers - (for Graphics card:8800gtx) and for (logitech stx communicate webcam)
Installing various win apps (like office and what not i know open office is there but still) also apps such as photoshop
I know there is a program for mounting gaming (gone out of my mind now) - I play counter strike so i guess ill follow the Install steam guide on the internet.

I would like to thank for any help given

---

### Post by Terl on 2007-05-08
It is sort of ironic that you say you've had it with M$ but then go on to say you need M$ Office.  :)   Anyway, humor aside...

For games.  Check the Wine site.  [Wine HQ]("http://www.winehq.org/")  They have all the info and a great database for what works, what doesn't, and what is so-so.  

Photoshop is an iffy thing.  I have seen some posts that say it works but is buggy and others that say 6 and below work but CS2 won't.  A good search here and at Wine will help.

Also check out VM Ware.  That will help you with some windows apps too.

The nVidia drivers are available via synaptic and there are many guides here, at the wiki, and in the docs on the main ubuntu site.  [Ubuntu Guide Wiki]("http://ubuntuguide.org/wiki/Ubuntu_Feisty") has a good deal of information on the drivers and other useful tips.

---

### Post by MR Spade on 2007-05-08
Can you help me with the 8800gtx Graphics driver plz ?

---

### Post by IainT on 2007-05-08
Have you looked amongst your menu's for the 'restricted drivers' option?

I can't remember what it is called, nor have I used it, presently running fluxbox. Terl also suggested looking on synaptic and the Ubuntu wiki, which are excellent places to start.

---

### Post by Nobel on 2007-05-08
Have you tried seeing if the video driver for your card is in the "Restricted Drivers" programm?

I'm not at my Ubuntu box, and i don't know if its supported since i use a Radeon. But i heard that widget works well for installing display drivers .

"Restricted Drivers" is somewhere in your Preferences or Administration menu (Feel free to correct me here :) )

---

### Post by MR Spade on 2007-05-08
I tried its like auto update for my graphics. That caused a blue screen graphical x or something error.

Done the same with a different tutorial and had the same prob

---

### Post by az_s_za on 2007-05-08
Instead of Ms Office, use Open Office.
Instead of Photoshop, use GIMP Image Editor

Yes, they are different to what you are used to, but then Ubuntu is different to Windows.  If you spend some time getting used to them, you'll probably find you like them better than (or at least as much as) the Windows equivalent.

It would be a shame to have to use wine when there are good Linux equivalent programs, but if you must, the supporting documentation for wine at wine hq will explain how to install programs, but basically you have to:
1. use a terminal to navigate to the location of the windows setup file on a cd ROM or elsewhere on your computer, e.g. cd /somewhere/somewhereelese/ ; then
2. type: wine setup.exe (or whatever else the setup file is called)

Personally though, I think that if you can't do without these basic windows programs, you are probably going to be stuck still using a lot of windows software, so you may as well dual-boot to windows.  Your apps will work as expected then.

As for games, I am not familiar with counter strike using wine, as Terl says, there will be info on how this works at wine hq, but in my experience, depending on your system, complex games (esp 3-D) can be difficult with wine.  Dual-booting is the only 100% sure way to play them.  But that's my experience, and my laptop's 3-D drivers don't work properly with wine.

---

### Post by Nobel on 2007-05-08
I saw a 'Steam in Ubuntu' guide somewhere once, might even be on these forums.

But i agree with az_s_za.

Getting used to using Windows alternatives takes some time, but you'll get there.

I use my Ubuntu laptop at school, and it's not a problem. As long as i remember saving as .doc when sharing documents with classmates, and as PDF when the documents contain formulas.

But i recommend Dual-Booting if you're having a hard time getting used to Ubuntu. There is no shame in not jumping right into the fray, and rome was not built in 1 day.

I personally started using Ubuntu for very limited stuff. Just messing around at start, amazing my friends who had never seen another OS. I now spend more and more time in ubuntu, getting things to work. And eventually proberly doing all my work in Ubuntu..

On that subject, Why the hell am i in windows right now? I'll be right back with you  :KS

---

### Post by gamer91 on 2007-05-08
> **az_s_za said:**
> Instead of Ms Office, use Open Office.
Instead of Photoshop, use GIMP Image Editor

not everybody is a hobbyist - some of use have jobs/schools which require compatibility and uniformity with the outside world.

---

### Post by Terl on 2007-05-08
> **MR Spade said:**
> Can you help me with the 8800gtx Graphics driver plz ?


The driver you want is on synaptic.  Open it up and search for nVidia.  Scroll until you see nvidia-glx-new.  You want the new one.  Mark it for installation and apply.  When it is done edit you xorg.conf (there are guides at the sites I named above) save it and then hit contrl-alt-backspace to restart your xserver.  You should see the nice nVidia splash.  I did this last night on a new Feisty install and it took a matter of minutes.  When you get back to your desktop you will get a notice about the restricted drivers manager.  Do what it says, read it and ok it.

---

### Post by MR Spade on 2007-05-08
> **gamer91 said:**
> not everybody is a hobbyist - some of use have jobs/schools which require compatibility and uniformity with the outside world.

That is the reason for needing such programs I want to start learning the alternates but i need to be able to access such things in the mean time.

---

### Post by MR Spade on 2007-05-08
Well i have gone into that program and downloaded those updates. 

as for the xorg.conf. Well i am a total noob remember I have searched the winehq and the other site and well how am i surpose to edit it.

I have done sudo gedit /etc/x11/xorg.conf

and if you want me to replace all the "nv" with "nvidia" it has already been done is that all that needs to be done here ?

Could you possibly add me on msn: [email]total_365@hotmail.co.uk[/email]

Thanks Dude.

---

### Post by Terl on 2007-05-08
EDIT:  Just saw you got the nvidia changed.  Hopefully you fixed the resolutions in the file too.  If not we can get that next.  You might have to reboot to make it work.  Sometimes you just have to restart the x server with Ctrol-alt-backspace.  If that works great.  If not reboot the puppy, you should see the nvidia logo.  If you do, you nailed this part :)

---

### Post by az_s_za on 2007-05-08
The wine user guide [[COLOR="Blue"]_here_[/COLOR]]("http://www.winehq.org/site/documentation") has all the info you need.

To configure, in terminal, type:
winecfg
 
the default settings are probably OK for starters.

Thanks gamer91 for your "constructive" contribution to this thread.  I was simply showing this guy the Linux equivalents while still trying to get him going with what he wants to do.  
I too work for a living which is why I use OpenOffice, because it can do so much more for me than MsOffice.  
As for photoshop, yes, I have seen experienced photographers work with this program and the speed at which they can accomplish complex tasks, after years of familiarity with the program is amazing, so I can understand professionals finding it very hard to make the switch.

Doh! sorry, I thought you were asking how to edit the wine config, and missed Terl's post while typing, so I'll leave it too him now.  He seems to be doing a sterling job getting you going.

---

### Post by Terl on 2007-05-08
> **MR Spade said:**
> That is the reason for needing such programs I want to start learning the alternates but i need to be able to access such things in the mean time.

For this, definitely look into VM ware.  There are some good posts here and on the wiki about how to set it up.  I don't use it so I cannot help you too well with it.  I have checked the vmware site and they do have great guides and documents that will help a lot.  There is even a method using the workstation version that will let you load your existing windows installation (if it is on a separate disk) from linux in a virtual machine.  The info is all at their site.

This is a fun tool also:  [VirtualBox]("http://www.virtualbox.org/")

Here is link to VMWare free products page:  [VMWare]("http://www.vmware.com/products/free_virtualization.html")

When you get time though, I think you will find the Gimp to be a very effective tool.  There is even a way to mod it to look like photoshop.  Checkout [Gimpshop]("Gimpshop")

---

### Post by Terl on 2007-05-08
> **az_s_za said:**
> The wine user guide [[COLOR="Blue"]_here_[/COLOR]]("http://www.winehq.org/site/documentation") has all the info you need.

Doh! sorry, I thought you were asking how to edit the wine config, and missed Terl's post while typing, so I'll leave it too him now.  He seems to be doing a sterling job getting you going.


I am no expert on Wine, so thanks!!  I still want to get his x server running right... :)

---

### Post by MR Spade on 2007-05-08
O well that didnt work, Got an error message. On restart. So i guess i failed lol.

What i am gonna do now i reinstall Ubuntu (again) and then we can have another crack at it ;)

Right so from a fresh instalation this is what i am gonna do (what i did last time).

I am gonna install wine and amsn (so i can talk while on it) - Do you have msn ? If i could talk to you through that then this may be easier.

Then i will wait for your instructions I guess you suggest i intall the nvidia driver again? - What do you reckon on downloading the xp driver and trying to install it on wine ?

---

### Post by Terl on 2007-05-08
> **MR Spade said:**
> O well that didnt work, Got an error message. On restart. So i guess i failed lol.

What i am gonna do now i reinstall Ubuntu (again) and then we can have another crack at it ;)

Right so from a fresh instalation this is what i am gonna do (what i did last time).

I am gonna install wine and amsn (so i can talk while on it) - Do you have msn ? If i could talk to you through that then this may be easier.

Then i will wait for your instructions I guess you suggest i intall the nvidia driver again? - What do you reckon on downloading the xp driver and trying to install it on wine ?

I am headed out from work right now.  I won't be back on for about 2 hours.  I will check this forum when I get back on.  You can always send a pm to me here.

---

### Post by an93l on 2007-05-08
just so you know nvidea have brought out drivers for the 8800gtx for Linux. there is a small program out there called envy that will download/install it and also configure your xorg.conf file after backing it up for you. i used this auto installer and had no problems with it. after installing it there was an nvidea settings app in the system tools menu that lets you tweak the settings. i don't know about everything else but i would recommend this for your 8800gtx to get all the features

---

### Post by MR Spade on 2007-05-08
If this works then you are a legend.
I have downloaded it and I will reinstall Ubuntu and try it shortly.

---

### Post by Sqwishy on 2007-05-08
@ Spade
You shouldn't need envy, but if you tried everything else your gonna wana give it a shot. 
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)
You can download it there. Also if you get the blue screen make sure that under your device, the driver is "nvidia" not "nv" (I think they already said this, just making sure)

---


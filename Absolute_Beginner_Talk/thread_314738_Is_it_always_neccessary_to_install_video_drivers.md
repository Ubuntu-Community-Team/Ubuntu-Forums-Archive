---
title: "Is it always neccessary to install video drivers?"
date: 2006-12-08
forum: Absolute Beginner Talk
---

### Post by chris_n00b on 2006-12-08
My install of dapper (6.06) has been working great so far using an Nvidia GeForce FX5200 vid card. Automatically in the screen resolution menu it lets me select 640x480, 800x600, and 1024x768. I'm able to watch DVD and other videos just fine. I was reading through some other threads about bumping up the resolution a bit to something like 1280x1024  I read the easiest way, and sometimes the only way for it to work is to edit the xorg.conf file. 

So today, I typed in the terminal ```
gksudo gedit /etc/X11/xorg.conf
``` and added "1280x1024" at the beginning of each line. Saved it and then rebooted. Well when it restarted i could get to teh login window and you could tell it was set to 1280x1024 but once I entered my username and password, it would just loop back to that login screen. After a few times it would ask me to login from the full screen command line. It just ran in a loop and I couldnt get the GUI to load... I remembered from my other post that nano is the command line editor command so I tried that.

I used ```
sudo nano /etc/X11/xorg.conf 
``` and was able to get into the file and delete those extra resolutions. Then did an educated guess on how to save it (Ctl+S) and then now I'm able to get it running again. Last time when I tried to install the Nvidia drivers, I could only get max of 800x600 resolution (for a while it was only 640x480). Should I just leave things as it? Should installing the drivers always work on letting you select the resolutions you need? Everytime I have tried to add resolutions to the xorg.conf file it messes everything up for me.

Suggestions?

---

### Post by Ecthelion on 2006-12-08
The easiest way is to do
```
sudo dpkg-reconfigure xserver-xorg
```
leave everything as default except where you have to enter the resolutions.

But it is possible that you can only have some resolutions with a video driver...

I would say, try this, and if it doesn't work then it only leaves the option to install a video driver

---

### Post by BarfBag on 2006-12-08
You definitely don't need to install a video driver for everyday things.  Screen savers (except for OpenGL), video, DVD's, etc. will all work fine without it.

That being said, it will probably clear up your resolution problems.  I have that exact same video card and it's a breeze with the drivers installed.  If you don't feel like doing too much command line, Automatix is the easiest way to install it.  [http://www.getautomatix.com/](http://www.getautomatix.com/)

---

### Post by PriceChild on 2006-12-08
I strongly reccomend you get it going yourself using [usdf]Latest_Nvidia_Edgy[/usdf] or [usdf]Latest_Nvidia_Dapper[/usdf] Instead of using automatix.

But no you don't need it?

It does make everything appear quicker thoguh.

---

### Post by civic_si on 2006-12-08
It possibly could be the refresh rate for the monitor at the higher resolution. I have had that happen. The best way to fix that is to search the internet for the Monitor manufacturer and get the specs for that and make sure the refresh rate is good in the xorg.conf file if you dont want to try using the video drivers.

---

### Post by chris_n00b on 2006-12-08
Its wierd, because under System > Prefernces > Screen Resolution, my refresh rate is always fixed at 0. but I can select some different resolutions in the drop down menu... Im just hearing that if I have the drivers installed then more 3D apps will work better or correctly than if none were installed. I was looking at some posts on 3D gaming using Wine, and some how to's. They told to do a test to see how the fps were... so you opened from the command line some gears animation. (I did it but forgot the code.. something like glxgears or something) it said if you get over 1000fps your good, if low fps, then have to install new drivers etc..

I don't really plan to game on this machine..(have another one for that) but I noticed that some things (like a few screen savers, and a game or two were laggy)

would the correct drivers help this? I used Automatix2 originally, but thats how I got all messed up in the first place. After those drivers were installed, I had the nVidia splash screen come up on boot up, but my res was then stuck at 800x600 (refresh 60) Any modifying to the xorg.conf file led to me not being able to boot up. Well let me say adding extra resolutions to it didn't do anything and switching from 'nvidia' drivers to nv made it not boot up.

Everything works good now, except where the vid card would have to do some actual work to make things look smooth, then its a little choppy.

> I strongly reccomend you get it going yourself using [usdf]Latest_Nvidia_Edgy[/usdf] or [usdf]Latest_Nvidia_Dapper[/usdf] Instead of using automatix.

How do I do that? from the command line? 

Took me 2 or so days to get the computer working how I like it as it is now...Can I save this setup and if it doens't work, revert to how it is now?

Thanks for all your help... its really making a difference.

:)

---

### Post by drphilngood on 2006-12-08
The following link will walk you through it; just click on it.
[Latest_Nvidia_Dapper]("http://doc.gwos.org/index.php/Latest_Nvidia_Dapper")

Good luck!

---

### Post by chris_n00b on 2006-12-13
Ok I followed that link and went through with method #1. The install worked but its actually worse with the driver installed. With it installed I get fixed at 800x600 refresh rate of 60Hz. Does that mean #1, that the install worked but the driver isn't teh correct one, OR that it is and the only driver avail only supports up to that resolution on linux?

I then reverted back to my backup xorg.conf file and now I get 640 x 480, 800x600 and 1024x768, but the refresh rate is 0. 

Could my card need a legacy driver? Meaning method 2?  I have a Geforce FX5200 (256 RAM)

to quote teh page:
> Below are the legacy GPUs that are no longer supported in the unified driver.

GeForce 256 0x0100



should I do method 2?

---

### Post by PriceChild on 2006-12-13
Nope... you're not legacy... yet ;)

---


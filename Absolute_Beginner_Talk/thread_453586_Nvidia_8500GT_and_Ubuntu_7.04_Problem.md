---
title: "Nvidia 8500GT and Ubuntu 7.04 Problem"
date: 2007-05-24
forum: Absolute Beginner Talk
---

### Post by De_JA_Vu on 2007-05-24
Here i am once again...i guess with silly problems...

so i have a Nvidia 8500GT PCI-E card.
I have tried it for the last one week, with various method, for a number of times. but i could not get to install nvdia driver on my pc. it always crashes after i restart the system. and every time i have to replace the new xorg.file with the backup one. unless it will not go the graphics mode ever.

I even tried with the system software called ENVY found in [www.albertomilone.com](www.albertomilone.com) . but no success.
I am attaching my /var/Xorg.0.log file
[http://www.sharebigfile.com/file/175502/Xorg-0-log-txt.html](http://www.sharebigfile.com/file/175502/Xorg-0-log-txt.html)


help me out people...

---

### Post by ryanVickers on 2007-05-24
Wow, nice card!  Anyway, I've had trouble with my 7600GT in previous versions of ubuntu.  When I tryed it for the first time (pre 6.06) it wouldn't even start from the cd - too new.  But since then, It's been imporving in leeps and bounds in basic functionality and ease of use.  For example, finally at version 6.06, it worked, but I could not get the 3D accelleration working.  Then in 6.10, it worked, but it was a real pain to set-up.  In 7.04, so far,everything's been great!  I just went into System -> Administration -> Restricted Drivers Manager. I checked it off, it installed it, and rebooted all perfectly and automaticly.  I would think that possibly there is no real great support for your card yet.  Don't worry, it was less than 1 month before I was up and running from my first problem.  Someone will figure it out.  In the mean time, just go on without the 3D if you can bear it.  Hey, it's better than windows, at least ubuntu runs right?  In windows, even moving a window is an extremely difficult task (like paints 3 frams per second) if you dion't have a driver!

---

### Post by De_JA_Vu on 2007-05-25
> **ryanVickers said:**
> I just went into System -> Administration -> Restricted Drivers Manager. I checked it off, it installed it, and rebooted all perfectly and automaticly. 

are you suggesting me to do this? what is that you mentioned about "Automatically" installed the driver for you?
have a look on this article. doesn't it say that the nvdia already has a driver for my card?
[http://www.phoronix.com/scan.php?page=article&item=690&num=1](http://www.phoronix.com/scan.php?page=article&item=690&num=1)


and the part where you mentioned that cd even failed to give you a graphical interface. it happens with me as well. when ever i try to run the live cd, 9/10 time it will fail to give me a graphical interface(as even i select the "Start Ubuntu in safe Graphics mode" option. 

as you said if i can live without 3 D acceleration or not. I really dying to try Beryl. i know some one will eventually figure it out, but as time will go on this thread will be lost in other thousand threads. ahh..who am i kidding? ya i can wait maybe. but it will be head ache for me till if figure it out.
Thanx for you reply mate.

---

### Post by ryanVickers on 2007-05-25
Hmm, maybe it does have one built it, but It looks to me like those are beta drivers, not quite perfected yet.  Yes, I would suggest clicking on the "use driver" or whatever box and letting it take it from there. Automatically means, you used to have to find a package, install it (it would work if you were lucky) and then run a few commands that would in most cases break the graphical window system.  Now, it auto-downloads, installs, and configures the driver.  It worked for me, but like I said, you have a very new card - it might not do it quite right.

About the live cd not working, if you got it to work once, there's no reason why it shouldn't work every time, and vise versa.  If it didn't work once, I wouldn't expect it to ever work without some change to your system.

Yes, you will be just fine without 3D acceleration, but any 3D programs will rather fail to start (for protection of you most likely) or be really slow (unless you have a super processor (mine's a AMD 3800+ duel-core and it worked decent untill I installed the drivers)
Now a few things about beryl.
Just to let you know, there are some effects already built in to ubuntu 7.04 System -> Preferences -> desktop effects.  Now these are simpler, but much faster effects.  Beryl is highly customizable, and much more impressive, but for now I'm staying with compiz (desktop effects) for now. why?

1. it removed the window boarder (top bar and sides) off all my windows (when it was turned on)
2. It was ok, but I found it sluggish, and I've got an impressive card.  Now, you may find neither of these problems to be true, but just a warning.  Oh, by the way, if the boarders to get that problem (only happens with beryl), then removing it is not enough to get them back.  I had to look around for quite a while before finding what to do to a file (but I don't remember what it was)

So, in conclusion, I would say try the Restricted drivers manager, and give the built in effects a run first, and consider my warnings.  Beryl is experimental, but of course, so are the built in ones.

---

### Post by derekr44 on 2007-05-25
This was my biggest beef too.  I run a 7600GT and I had nothing but frustration after frustration trying the hundreds of different methods offered here to get it working (meaning the 3d acceleration).  I was usually able to get xserver loaded, but OpenGL was not working fully and I couldn't run any games.  Finally after about 2-3 hours of trying, I got it working last night!

I am using the following:
19" widescreen (1440x900)
nVidia 7600GT
Cedega 6

I tried using ENVY and it failed miserably.  The Restricted Driver option didnt work.  This is what worked for me:

```
sudo /etc/init.d/gdm stop
wget http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/NVIDIA-Linux-x86-1.0-9755-pkg1.run
sh NVIDIA-Linux-x86-1.0-9755-pkg1.run
```

Then then I had to:
```
sudo nano /etc/X11/xorg.conf
```

Add my HorizSynch and VertRefresh rates for my monitor to the Monitor section...
Add "1440x900" as an available resolution to all the different resolution lists...

I then had to plug in a CRT in the 2nd open video jack on the card, open the nVIDIA Configuration program in the Menu and set my (currently inactive) widescreen as the primary display and adjust my resolution to 1440x900.

Viola!

I know my description is a little jumbled, but it worked right after that.  Hope it helped.

---

### Post by maxamillion on 2007-05-25
According to nVidia.com, the 8000 series isn't supported by the current stable linux drivers..... if none of this works you might need to file a bug report against their beta drivers.

---

### Post by De_JA_Vu on 2007-06-01
OK here i go... this might sound crazy..but it is true...
as above things were not working for me, my friend asked me to install nvidia-glx driver at first.
so i install nvdia-glx drivers.
I reboot ubuntu Recovery mode.
install "NVIDIA-Linux-x86-100.14.06-pkg1.run" and let it configure my xorg.conf file.
but this time instead of rebooting my pc. i just tried a "startx" command to get gdm. and voila....i got my nvidia driver installed.
i can even go to "Nvidia X Server" setting utility. i can do anything.
oh my problem solved.
just to make sure, i rebooted the pc. and it crashed. the same xorg.conf file error. same stupid thing.
so i stopped gdm again. installed the nvidia driver again. instead of rebooting , tried startx. i get my nvidia driver working fine again.
as soon as i reboot my pc. it goes back to that stupid error of by saying the kernel of nvidia driver does not match .
how crazy is this problem? i dont get it.
i am attaching the xorg.conf file after installing Nvidia driver utility. this file crashes if i reboot. but works fine if i dont reboot. have a look. save me from this turmoil.
Pls have a look at this xorg.conf file, why do i have TWO section for the SCREEN ?
i have attached the Xorg.log file as well.

---

### Post by Wynne G Oldman on 2007-06-01
> **ryanVickers said:**
> Wow, nice card!  Anyway, I've had trouble with my 7600GT in previous versions of ubuntu.  When I tryed it for the first time (pre 6.06) it wouldn't even start from the cd - too new.  But since then, It's been imporving in leeps and bounds in basic functionality and ease of use.  For example, finally at version 6.06, it worked, but I could not get the 3D accelleration working.  Then in 6.10, it worked, but it was a real pain to set-up.  In 7.04, so far,everything's been great!  I just went into System -> Administration -> Restricted Drivers Manager. I checked it off, it installed it, and rebooted all perfectly and automaticly.  I would think that possibly there is no real great support for your card yet.  Don't worry, it was less than 1 month before I was up and running from my first problem.  Someone will figure it out.  In the mean time, just go on without the 3D if you can bear it.  Hey, it's better than windows, at least ubuntu runs right?  In windows, even moving a window is an extremely difficult task (like paints 3 frams per second) if you dion't have a driver!

I'm sorry, but from what I've seen so far of any release of Linux, Windows works with a far, far greater range of hardware, and you don't have to be a programmer to get it working. It also works properly. I've tried loads of Linux releases over the past 3 years, and none of them work anywhere near as well as XP. I mean, compared to windows, Linux is totally primitive. I haven't found one release yet that will work with all of my fairly standard hardware. There's more W98 users on Desktops than Linux users. That says it all! I guess that you get what you pay for, and you can't really complain if you don't pay anything. Sorry if I've offended anyone, but until Linux becomes as user freindly, and as hardware compatible as Windows, it will never be any serious competition to Microsoft.

---

### Post by psyopper on 2007-06-01
I had this same problem with my 6200. I resolved it...

[http://ubuntuforums.org/showthread.php?t=443846]("http://ubuntuforums.org/showthread.php?t=443846")

This is my "blog-thread" of what I tried. Read through it all, the final solution is at the end. It's actually a pretty easy fix, requires editing one file after you boot into a gui.

Good luck!

---

### Post by De_JA_Vu on 2007-06-02
> **psyopper said:**
> I had this same problem with my 6200. I resolved it...

[http://ubuntuforums.org/showthread.php?t=443846]("http://ubuntuforums.org/showthread.php?t=443846")

This is my "blog-thread" of what I tried. Read through it all, the final solution is at the end. It's actually a pretty easy fix, requires editing one file after you boot into a gui.

Good luck!

can i love you more? nah.... good god..it has solved my problem too............................
Thanx a lot mate........I am running my nvidia like hell rite now.... thanx a bunch

---

### Post by angeloj on 2007-07-08
had the same problems for a very long while but with Ubuntu 7.04, nVidia 8500GT and Envy 0.95 ( [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html) ) this all work just fine using the 100.14.11 nvidia drivers

---


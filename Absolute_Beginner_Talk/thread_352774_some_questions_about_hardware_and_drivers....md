---
title: "some questions about hardware and drivers..."
date: 2007-02-03
forum: Absolute Beginner Talk
---

### Post by techno-mole on 2007-02-03
hello.
i am looking for some help with drivers, mainly the graphics driver, im new to linux and ubuntu, i have just installed ubuntu 6.10, myself like alot of people have been using windows for some time and to be honest their latest version, vista has me really annoyed, so i thought id try linux, and i must admit im pleasantly surprised, i wish i had tried it sooner.
anyway my problem is drivers, i have an nvidia geforce 7600 gs agp card, and i am trying to install drivers for it in order to have a little more control over the resolutions and such like, but i cant install the drivers, ive tried downloading the linux drivers for my card from nvidia, but i cant get the pkg file to run,  so where can i get drivers for my card, and how do i install them, ive spent most of the day looking at various things and still im having no luck with it.
any help will be appreciated, ive tried using envy and i either did something wrong or it went wrong.

cheers.

---

### Post by ed-j on 2007-02-03
Novice Alert!

There are Binary Drivers for the 7600GS in Add/Remove>System Tools, type "nvidia" in the search box, click on the new drivers, apply the change. After they install, Restar. Hope this helps.

---

### Post by ed-j on 2007-02-03
That's Restar' with a "t" at the end. Ooops!

---

### Post by techno-mole on 2007-02-04
i did that already and they crashed the system, and i had to re-install ubuntu from scratch.
and yes i am a novice, to say the least, in fact i have been using linux for less than 48 hours now.
basically when i tried the binary drivers in add/remove programs they went on fine, but when i restarted the system and got back to the desk top all i had was the back ground picture and the icons on the desk top, ie firefox, terminal and such like, and the top and bottom bars were gone, and i couldnt get them back.

---

### Post by techno-mole on 2007-02-04
i have just tried the binary drivers again, that is to say i un-installed them and then re-installed them, once its downloaded/updated it says you can enable the driver by typing sudo nvidia-glx-config enable, which i did and i then got - Error: unable to load nvidia kernel driver! Be sure to have installed
the nvidia driver for your running kernel. which i thought would be automatic ? so do i need a different version of the driver ? because thats the one that you can use when you go to add/remove applications, if it is the wrong driver then where do i get the right one ? ive also tried the linux driver from nvidias website and it wont let me install that either.
im running ubuntu 6.10 (dont know what kernal version it is, but i assume its the latest as ive updated) 64 bit version.
nforce 3 mainboard.
amd athalon 3200 64 bit cpu.
nvidia ge force 7600 gs 
1.2 gb or ddr memory.
i have ubuntu installed on a seperate hard drive so as note to get confused.
cheers.

---

### Post by Johan! on 2007-02-04
[http://www.ubuntuforums.org/showthread.php?t=301499](http://www.ubuntuforums.org/showthread.php?t=301499)

---

### Post by techno-mole on 2007-02-04
in my first post i said that i had tried envy, i also tried using the guides that tseliot has posted in various places and i have had no luck with any of them, envy crashed the system completely, and using the guides has basically resulted in nothing happening, im still at square one.
i will however try the guides again as im not proficient with ubuntu (linux) yet it never hurts to practice, i will post again if i have any luck.
cheers

---

### Post by ed-j on 2007-02-04
> **techno-mole said:**
> i have just tried the binary drivers again, that is to say i un-installed them and then re-installed them, once its downloaded/updated it says you can enable the driver by typing sudo nvidia-glx-config enable, which i did and i then got - Error: unable to load nvidia kernel driver! Be sure to have installed
the nvidia driver for your running kernel. which i thought would be automatic ? so do i need a different version of the driver ? because thats the one that you can use when you go to add/remove applications, if it is the wrong driver then where do i get the right one ? ive also tried the linux driver from nvidias website and it wont let me install that either.
im running ubuntu 6.10 (dont know what kernal version it is, but i assume its the latest as ive updated) 64 bit version.
nforce 3 mainboard.
amd athalon 3200 64 bit cpu.
nvidia ge force 7600 gs 
1.2 gb or ddr memory.
i have ubuntu installed on a seperate hard drive so as note to get confused.
cheers.

Morning!

Firstly, my apologies for the misconception of "Novice Alert!". I was warning you that I am a novice and very new to Linux. Sorry about that.

However, your system sounds very similar to my new system (3.2 AMD64, AM2, 7600GS and 1gig of DDR2 533). I also use my hard-drive in a Caddy.

I also experienced lots of problems with Nvidia's drivers by loading the AMD64/EMT64 form their site. For my own novice education, either today or tomorrow, i will try the 32Bit drivers for a laugh. Of all the installations I have made in the last 2 weeks, I think I succeeded by: Install 6.1, install Nvidia Binary Drivers from Add/Remove, download updates for 6.1, Restart, type sudo dpkg-reconfigure xserver-xorg into Terminal, choose 1600x1200 and 1280x1024 (1024x768 and below are defaults, I left them as they were), I chose Medium in the Refresh section: Arrow down to bottom of list, Arrow up to top of list, Arrow down one by one, eventually I came to 1600x1200@75Hz. The system then sets all of the other Refresh Rares for the chosen resolutions. I have an old 19" CRT, if you have an LCD or TFT, the default settings will only work at one particular resolution at 50 or 60Hz but with no flicker.

Best I can do! Please let me know how you get on

---

### Post by ed-j on 2007-02-04
> **techno-mole said:**
> in my first post i said that i had tried envy, i also tried using the guides that tseliot has posted in various places and i have had no luck with any of them, envy crashed the system completely, and using the guides has basically resulted in nothing happening, im still at square one.
i will however try the guides again as im not proficient with ubuntu (linux) yet it never hurts to practice, i will post again if i have any luck.
cheers

Apparently, Envy seems to be a "use at your own risk" kind of Lemming! Pretty much the same as in Real Life really. Just letting you know.

---

### Post by techno-mole on 2007-02-04
ok, so i must have done something right as before i was not getting 3d acceleration, i still dont have any resolution options, so ill try having ago again, one other question though, ive downloaded the linux drivers from nvidias website, but i cant get them to run, every time i type the 
command to run it (as per the instructions on nvidias website) i get errors, ive had just error come up, ive also had that it needs to run as a root ? dont know how to do that, ive also had that it isnt even on the pc ? anybody got any ideas ?

---

### Post by Bachstelze on 2007-02-04
Instead of using the installer from nvidia.com, try to follow [these steps](https://help.ubuntu.com/community/BinaryDriverHowto), which are specific to Ubuntu.

---

### Post by techno-mole on 2007-02-04
ok, so when i start up i now have an nvidia splash screen, which means the drivers are working and such like, i have another question, is there an easy ish way to adjust the resolution, and the refresh rate, i can go into system/preferences, then monitor resolution, but i have the grand total of one choice and thats the one its set to, that is 1152x768 @ 55 hz while this resolution is ok, my monitor which is just a bog standard crt has a slight flicker to it at frequencies lower than 65/75, i normally run it on 75 hz and a resolution of 1152x800, there is one small catch, that being that the monitor is just a crt, without taking it apart i cant tell who made it, and there in lies another problem, that being i dont know the exact capabilities of the monitor.
by the way thank you all for the help, and heres to companies like nvidia being a little more helpful with drivers and such like.

---

### Post by techno-mole on 2007-02-04
ignore my last post, ive found what i need, many thanks again for the help given.
):P

---

### Post by ed-j on 2007-02-04
> **techno-mole said:**
> ok, so i must have done something right as before i was not getting 3d acceleration, i still dont have any resolution options, so ill try having ago again, one other question though, ive downloaded the linux drivers from nvidias website, but i cant get them to run, every time i type the 
command to run it (as per the instructions on nvidias website) i get errors, ive had just error come up, ive also had that it needs to run as a root ? dont know how to do that, ive also had that it isnt even on the pc ? anybody got any ideas ?

I'm afraid I've given you the all advice I can. I am only a novice and a very new one at that. It would be best for me to hope you can find some other help. You'll get there!

---

### Post by ed-j on 2007-02-04
> **techno-mole said:**
> ignore my last post, ive found what i need, many thanks again for the help given.
):P

Brilliant! Ignore mine too. Thanks for letting me know.

---


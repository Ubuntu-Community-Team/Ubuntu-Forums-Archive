---
title: "XP -&gt; Ubuntu Issues"
date: 2007-12-08
forum: Absolute Beginner Talk
---

### Post by Curse on 2007-12-08
Hey, so I have decided to install Ubuntu on my old desktop, which is running XP.

I made my own boot disk, everything seemed to work just fine on that end, so I reboot the comp with the disk in the drive, and get the splash screen that gives you the option to View/Install Ubuntu etc.

I hit enter, and it goes to the Ubuntu loading screen, then after a bit goes to what looks like MS DOS, and comes up with a few lines of errors ([  255.809775] Buffer I/O error on device hdb, logical block 0   and others). It goes through some of those, then it goes through lines starting up parts of Linux, with [OK] at the end of them. 
Afterwards, it flashes a multicolored flashy screen, where nothing else works, as far as I can tell.

Before this I had an old xbox HD that I was messing around with still hooked up as a slave, and while this was hooked in, it would go through the lines of error code (without showing me the splashscreen first) then end up at the flashy colors screen again.

Help? :[

---

### Post by lswest on 2007-12-08
try starting it in safe graphics mode, seems to me that there is a slight driver issue with your gfx card.  and the buffer I/O for the hard drive...not really sure why that would even occur, as liveCDs run in RAM...

---

### Post by jrharvey on 2007-12-08
What kind of video card do you have??? If you are trying to run the live cd then you may want to put up your system specs such as how much memory you have, video card and so on. Keep in mind that it takes a while to boot up a live CD but hopefully no longer than 15 minutes.

---

### Post by Curse on 2007-12-08
How do I start it in safe graphics mode? (sorry, such a noob :[  )

I have a Geforce 6600GT, 1 stick of 1gb of ram.... I think i have a 256mb stick next to it, which could be causing issues. 

Older AMD 1.2 gigahertz processor

---

### Post by jrharvey on 2007-12-08
try highlighting the START UBUNTU option from when you first boot and hit other options (i think it is F6) There will appear some text at the bottom, try deleting "quiete" and add "nosplash" instead of splash. This worked for me because ubuntu would never boot the live cd with the nvidia card that i had.

---

### Post by lswest on 2007-12-08
and to start in safe graphics mode there is an option under "start or install ubuntu"in the menu i believe

---

### Post by Curse on 2007-12-08
After highlighting it, hitting f6 doesn't bring anything up that I can see...

---

### Post by lswest on 2007-12-08
there is a small list of other options on the bottom of the boot menu, see what F key the "other" options are bound to, F6 might be wrong.

---

### Post by Curse on 2007-12-08
Tried doing it in safe graphics mode, it went through as usual and instead of displaying colored lines, the monitor got an unusable signal :/

---

### Post by Curse on 2007-12-08
Okay, nevermind about the cdrom thing.. anyway.

For some reason it isn't displaying the visual cues with the f1-f6 stuff, I think the screen isn't going down far enough to show it for some reason. I was able to navigate to set it to 800x600x16, hopefully this will work.. Trying it now.

Thanks for your help so far by the way.

---

### Post by Curse on 2007-12-08
Well, here's where I am now:

I have a brand new hard drive, and it still does the same thing.

However, except when booting, it doesn't show the screen with the options to Start/Install Ubuntu, and the 30 second countdown timer, etc.. It just goes straight into loading the kernel.

After it gets to the flashy colors screen, if I hit ctrl + alt + f1 it brings it to a black and white screen with similar lines down it, and gives me a command line, though when I type, nothing shows up.

I tried the text (alternate) installation, and all it did was after loading the kernal (the lines with [OK] at the end) the screen just went blank. :/

---

### Post by jrharvey on 2007-12-08
Ok so you have an nvidia card right? Do you have an onboard graphics card or is the nvidia the main card? Also are you trying to use the 32bit or 64bit ubuntu? I got my CD's mixed up one day and tryed to install 64bit OS on a 32bit processor and had similar problems. If you do have a standard onboard graphics card then try using that one instead of the nvidia until you can get it installed.

---

### Post by jrharvey on 2007-12-08
Also the hard drive should not affect the live cd. I used the live CD on a computer that had a broken hard drive for a while and it always worked fine. I was never able to install but i could use it from the ram.

---

### Post by Curse on 2007-12-08
As far as I know, there are no onboard graphics. I will take a shot of the back of my comp though. The only VGA related plugins appear to be female ends... which doesn't seem right. 

Also, took some 'screenshots' :p

[Flashy screen](http://i170.photobucket.com/albums/u279/Andrelommech/DSC00118.jpg)
[B&W screen with command prompt](http://i170.photobucket.com/albums/u279/Andrelommech/DSC00117.jpg)



[Back of comp](http://i170.photobucket.com/albums/u279/Andrelommech/DSC00125.jpg)

---

### Post by jrharvey on 2007-12-08
You are definitely having video card issues here. This is weird because this card is suppose to be compatible with all versions that I know of. So you can't even get into the main options of ubuntu any more? Can you still boot into XP? If you can then I may want to try WUBI and see if that works. WUBI is a way to install ubuntu from XP. Its actually a really cool program and if you ever want to get rid of linux then you simply uninstall it.

---

### Post by jrharvey on 2007-12-08
If WUBI sounds cool then I would go with the 7.10 Alpha.

---

### Post by Curse on 2007-12-08
I may just pick up a new card..... Would that fix the issue, you think?

---

### Post by jrharvey on 2007-12-08
well it may, but it may not. I would try some things b4 you go spend over $100.

So XP boots fine and with no problems?????

---

### Post by Curse on 2007-12-08
> **jrharvey said:**
> well it may, but it may not. I would try some things b4 you go spend over $100.

So XP boots fine and with no problems?????

Yup. I'd have to hook up my 40gb HD, but i'm sure it does, it did the last time I tried it, which was last night. Nothing has changed except the boot order :p



EDIT: Hm. Maybe there is a problem. Now it says 'BOOT DISK FAILURE. INSERT SYSTEM DISK'

Hm.

---

### Post by jrharvey on 2007-12-08
Ok someone else is gonna have to jump in here. I have never had that error before and I have never installed anything on a fresh HD.

---

### Post by Curse on 2007-12-08
Nevermind, I guess I can boot in windows -.-

I set up the new HDD as master and windows HDD as slave... booted to windows. 

I'll see if I can find WUBI.

You know what would be cool.. If I could just install Ubuntu on the new HDD from the old HDD?

---

### Post by Curse on 2007-12-08
By the way, I burned a copy of Ubuntu 6.06 properly (the others had been recording at like 24x, instead of 4x) and tried it.

It went through the same things, except I ended up with:

[This](http://i170.photobucket.com/albums/u279/Andrelommech/DSC00128.jpg)

And, when I hit ctrl + alt + f1:
[this](http://i170.photobucket.com/albums/u279/Andrelommech/DSC00127.jpg)

What commands shall I run?

---

### Post by jrharvey on 2007-12-09
Have you tried ubuntu 7.10. I have never used your version. I know it is the LTS but gutsy gibbon might have better support for your card. I know this seems frustrating right now just trying to get it to even install but I am sure it will all be worth it.

---

### Post by Curse on 2007-12-09
> **jrharvey said:**
> Have you tried ubuntu 7.10. I have never used your version. I know it is the LTS but gutsy gibbon might have better support for your card. I know this seems frustrating right now just trying to get it to even install but I am sure it will all be worth it.

I've been trying 7.10, and its been failing, 6.06 has at least gotten me a working command screen :/

---


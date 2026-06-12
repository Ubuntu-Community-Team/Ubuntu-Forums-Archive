---
title: "3 screens, how to turn off 2?"
date: 2007-12-03
forum: Absolute Beginner Talk
---

### Post by skyout on 2007-12-03
I am new to Linux, new to Ubuntu.  As an interesting exercise to motivate me through the learning curve I am attempting to set up a modest multi-media server.  My goal is to play my music collection, streaming audio, slideshows and videos.  I pretty much have everything working and am now doing the refinements, but I have run into a problem that I hope someone might be willing to help with.  

I have 2 video cards running 3 monitors.  One card is an older ATI (3D Rage IIC, ati driver) and the other is a fairly new nvidia (GeForce FX 5200, nvidia driver).  The ATI card is driving a 19" Samsung CRT, and the nvidia card is driving a 19" Optimus CRT  and a TV (through the SVideo output).  The monitors are set as three different xscreens.  As my screensaver I have a slideshow which cycles through my photo collection, three at a time, a different one on each monitor.  I use Amarok to play streaming audio or my local collection.   I use Totem to play DVDs and Videos.  I have it set up so that if a CD is inserted Amarok stops what it is doing and plays the CD.  If a DVD is inserted Totem starts up in full screen mode and plays the DVD on the TV.  So far so good.  What I would like to do, (and so far have not been able to) is to automatically blank the two 19" monitors when the DVD is inserted. 

Using $DISPLAY on each of the different xscreens I have identified the two 19" monitors as :0.0 and :0.1.  The TV is :0.2

I have tried using xset ('xset -display :0.0 dpms force off' and 'xset -display :0.1 dpms force off'), however, both commands turn off all three screens.  A little experimenting showed that any display parameters of :x.y where x is 0 and y is 0, 1, or 2 turned off all three screens.  Anything other than 0 for x or 1, 2, or 3 for y returns 'xset:  unable to open display ":x.y" '

I have also tried using image viewer to bring up a blank picture and display it full screen, however even though I can run a separate instance of image viewer in each xscreen for some reason I can only have one displayed full screen at a time.  

Right now my solution to the problem is to turn off the power switch to the two extra monitors, but that is both awkward and inelegant; and it doesn't get me anywhere on the Linux/Ubuntu learning curve.

Suggestions, anyone?

Thanks,

Dave  C.

---

### Post by cacycleworks on 2007-12-03
Oooo! I hope you get an answer soon. I use my laptop in a docking station and wish to know how to turn off the laptop's screen. I ended up reorganizing my desk with another mouse and kybd so that the docking station can live somewhere away from me and the laptop stay closed during use. So technically, my problem is solved... but I'm pretty curious! :)

---


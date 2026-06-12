---
title: "frequency out of range"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by bnhrobotics on 2007-04-22
Hello all. 

I am new to Linux and to Ubuntu. I decided to dual boot and install Ubuntu 6.10. For some reason 7.04 was not installing properly. However, in both cases on the install and even now booting up and shutting down I get a really bizarre error. For about a minute when starting up my computer the screen goes blank except for a message telling me that the frequency is out of range. It displays the vertical and horizontal screen frequencies. This is not so much of an issue on the start up because I get the login screen after about a minute. However, when I shut down my computer, this message comes up indefinitely and I have to manually shut the power off to turn my computer off. 

About my computer:
I cant remember all the specs on my computer (most of my documentation is at home)  but it is probably 6 years old now. Its got an AMD Athalon 1300 MHz Processor, 512 MB of ram 40GB hard drive. I believe the video card is either built in to the mother board or it uses the RAM for some sort of virtual video card. 

Any ideas what could be causing this problem or what I can do to fix it? Thanks

Bryan

---

### Post by oilchangeguy on 2007-04-22
is your monitor as old as the computer? try a lower resolution. if you're using 1024x780, try 800x600.

---

### Post by bnhrobotics on 2007-04-22
Actually I just bought the monitor a few weeks ago. Its a 19" flat screen LCD but my computer is too old to support its maximum resolution. I will try a few different screen resolutions and see what that does. Thanks.

Bryan

edit:

I just tried several different resolutions and nothing changed. The message also says Vertical Frequency = 35.5 kHz and Horizontal = 87 Hz.

---

### Post by Rohen on 2007-08-14
I have exactly the same problem... I've been looking around in the forum but there's no clear solution to this problem I have.[-X

My machine is a SONY VAIO 2.0 Ghz 512 RAM 80 GB HD.  19" LCD Flat screen.  Current resolution right now is 1280x1024.

To sum things up: While my VAIO is booting it shows the out of frequency range message, up until it gets to the login screen. Then I can see everything perfectly.  This only occurs while it's booting up.  In other words I can't see my computer booting up, i've never seen what goes on while it boots... I would love to fix this!:(

Any HELP?? ANYONE PLEASE??? ](*,)

---

### Post by nvrpunk on 2007-08-14
You need to go to the Manufacturer's Website of the Monitor/LCD panel you are using and look up it's specifications.  

Horizontal Refresh Range
Vertical Refresh Range 

It should look something like 31-85Hz  

If it is a laptop it should be found in the user manual.  

xorg.conf should look like this. 

Section "Monitor"
	Identifier   "My Monitor"
	HorizSync 30-85
	VertRefresh 50-160

-nvrpunk-

---

### Post by Rohen on 2007-08-14
> **nvrpunk said:**
> You need to go to the Manufacturer's Website of the Monitor/LCD panel you are using and look up it's specifications.  

Horizontal Refresh Range
Vertical Refresh Range 

It should look something like 31-85Hz  

If it is a laptop it should be found in the user manual.  

xorg.conf should look like this. 

Section "Monitor"
	Identifier   "My Monitor"
	HorizSync 30-85
	VertRefresh 50-160

-nvrpunk-

Thanks a lot man I'll look into this and post the results.  Thanks!

---


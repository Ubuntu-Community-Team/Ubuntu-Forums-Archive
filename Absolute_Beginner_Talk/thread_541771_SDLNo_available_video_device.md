---
title: "SDL::No available video device"
date: 2007-09-03
forum: Absolute Beginner Talk
---

### Post by renjith on 2007-09-03
Hi,

I have a video capture test application .
Capture driver is working fine. 
I have installed sdl and the required other libs as well.
But i am getting an Error like ,

unable to initialize SDL: No available video device

when I run my test app.

kindly gimme a suggestion....
I was going thru the forum comments as well. and as per the suggestions,
I tried with
xhost +local:root
and
export DISPLAY=:0.0 in a new terminal.

But the result is same.

I am using my video card as follows,
           Section "Device"
           Identifier "ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]"
           Driver "ati"
           BusID "PCI:1:0:0"
           EndSection

Now, after commenting the "DRI " lines in the /etc/x11/xorg.conf, I can play video with
mplayer but , still the test app using sdl is giving the same errror.... 

pls advice..

Thanks
Ren

---

### Post by rpjanaka on 2008-01-18
Same error message got to me while I am run the player example of theora codec (beta 2 version). :( :( :( 

Please help me....................

---


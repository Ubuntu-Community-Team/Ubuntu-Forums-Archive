---
title: "Changing screen resolution?"
date: 2006-09-28
forum: Absolute Beginner Talk
---

### Post by meniscus on 2006-09-28
You know the way you can alter thr resolution in windows by going into the desktop settings...how do you do it in ubuntu?

---

### Post by xpod on 2006-09-28
System-preferences-screen resoloution....

To start with at least.....:D

---

### Post by gn2 on 2006-09-28
And if the settings you want aren't there, 

try this: sudo dpkg-reconfigure xserver-xorg

---

### Post by bigken on 2006-09-28
> **gn2 said:**
> And if the settings you want aren't there, 

try this: sudo dpkg-reconfigure xserver-xorg


use the space bar to select the required resolutions

---

### Post by meniscus on 2006-09-28
I typed in the terminal command ye said and its asking me to "select the desired x server driver"

Ive a btx motherboard with integrated videocard. Here are all the choices...

apm
ark
ati
chipscirrus
cyrixfbdevglintil128i740i810imsttmganeomagic
newport
nsc
nv
rendition
s3
s3verge
savage
siliconmotion
sis
sisusb
tdfx
tga
trident
tseng
vesa
vga
via
vmware
voodoo


How do i find out which 1? I dont have the mobo manual!

---

### Post by bigken on 2006-09-28
pop the side off the box and gett he board number ect but for now you can use vesa ;)

---

### Post by meniscus on 2006-09-28
R u being serious or joking? Will vesa do the job?

---

### Post by bigken on 2006-09-28
it will get you up and running until you know which graphics chip you have ;)

i asume you have already had ubuntu running so why dont you look in system/administration/device manager and what your video chip is ?

---

### Post by xpod on 2006-09-28
Cant he just look in "device manager" to see what he uses??

Mines is listed in there.
Of course that dosent stop me breaking in:twisted:

---

### Post by meniscus on 2006-09-28
Right!Ive gone throught the whole process of the terminal way with the correct video card driver(ati) and chosen a higher resolution. But it stall hasnt changed!Its still on 600*400 which is desperate! Do i need to reboot or something?

---

### Post by bigken on 2006-09-28
try it are you sure your selecting the right resolutions for your card 
do you know which ati card it is

---

### Post by meniscus on 2006-09-28
Sorry yes, its an ATI Radeon xpress 200 series driver version 8.172.0.0. I was just checking on my windows there. it allows 1024*768 pixels! Why is it not on ubuntu?

---

### Post by meniscus on 2006-09-28
yes!The second reboot did it! Thank you very much for your time and patience:-D

---

### Post by lounsbud on 2006-09-28
Good morning. I am having the exact same problem and am also a brand new user.

I just installed on an old Pentium II Compaq Proliant server and also can see no other resolution than the absolute lowest. My video is integrated and is an ATI 3D Rage IIC 215IIC [Mach64 GT IIC] according to the Device Manager. I will watch this thread closely to see what solutions are found.

---

### Post by bodhi.zazen on 2006-09-28
I think you need to install the ati drivers.

[[color=blue]How to ATI[/color]](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

I prefer method 2....

To answer your first question, to change screen resolution (once you are up and running with the ati driver)```
Ctrl-+
```

That is the Control key and the + key on the numeric keyboard pad.

control and - key to reduce.

This also works with the font size in Firefox....

8-)

---

### Post by bigken on 2006-09-28
> **meniscus said:**
> yes!The second reboot did it! Thank you very much for your time and patience:-D

ok now enjoy the ride ;)

---

### Post by xpod on 2006-09-28
>  	Good morning. I am having the exact same problem and am also a brand new user.

I just installed on an old Pentium II Compaq Proliant server and also can see no other resolution than the absolute lowest. My video is integrated and is an ATI 3D Rage IIC 215IIC [Mach64 GT IIC]

I got kubunto on a compaq 5130 and its got a "Rage LTPRO" card in it and the basic onboard "Mach 64 utah" thing as well..

Unfortunately the rage thing seems knackered on that and i think it uses the utah onboard thing instead but thats on kubunto so it`s a bit different.

A good day to you & good luck too

---

### Post by lounsbud on 2006-09-28
> **bodhi.zazen said:**
> I think you need to install the ati drivers.

[[color=blue]How to ATI[/color]](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

I prefer method 2....

To answer your first question, to change screen resolution (once you are up and running with the ati driver)```
Ctrl-+
```

That is the Control key and the + key on the numeric keyboard pad.

control and - key to reduce.


This also works with the font size in Firefox....

8-)

Thanks for the feedback. I tried method 1 because method 2 says it is not for cards older than the 9500 which this is I am sure.

I did find an installer on the ati site. Downloaded it with no problem but when I run it I get an error that says I need to be logged in as a super user. I have checked the user setting but can find no reference to super user nor can I see the whole screen (because the resolution is so off). Its a catch 22 and getting frustrating...any other ideas?](*,)

---

### Post by winvado on 2006-09-28
This works in Xubuntu when you swap back and forth to Fluxbox, which seems to upset thing with resolutions and font sizes etc.

Go to (open) a terminal.

type "xrandr"

you get a list of resolution options

type "xrandr -s 1" for exampe to give 1024 * 768

Its not permanent but in the scheme of things with most these buggy window managers its good enough to get you where you want to be.


regards

---

### Post by bodhi.zazen on 2006-09-28
> **lounsbud said:**
> Thanks for the feedback. I tried method 1 because method 2 says it is not for cards older than the 9500 which this is I am sure.

I did find an installer on the ati site. Downloaded it with no problem but when I run it I get an error that says I need to be logged in as a super user. I have checked the user setting but can find no reference to super user nor can I see the whole screen (because the resolution is so off). Its a catch 22 and getting frustrating...any other ideas?](*,)

use sudo. It will ask for a PW. use you log in PW.

```
sudo <command>
```

---

### Post by lounsbud on 2006-09-28
> **winvado said:**
> This works in Xubuntu when you swap back and forth to Fluxbox, which seems to upset thing with resolutions and font sizes etc.

Go to (open) a terminal.

type "xrandr"

you get a list of resolution options

type "xrandr -s 1" for exampe to give 1024 * 768

Its not permanent but in the scheme of things with most these buggy window managers its good enough to get you where you want to be.

regards

Thanks for the tip. When I tried it I got a list of resolutions but the highest resolution available was the one I am currently using (640x400). Any other ideas? I will continue to play around with it and see what I can come up with. ](*,) 

I GREATLY appreciate all the help!!! :)

---

### Post by bodhi.zazen on 2006-09-28
Any luck with the AVI driver?

---

### Post by lounsbud on 2006-09-28
> **bodhi.zazen said:**
> Any luck with the AVI driver?

I did get it to install with sudo. Thanks for that but still no other screen resolutions available (in GNOME) besides the 640x400. Is there a next step that I am missing?

---

### Post by bodhi.zazen on 2006-09-28
> **lounsbud said:**
> I did get it to install with sudo. Thanks for that but still no other screen resolutions available (in GNOME) besides the 640x400. Is there a next step that I am missing?

Did you re-boot?

If so, what is the output of```
sudo fglrxinfo
```

---

### Post by lounsbud on 2006-09-28
I did reboot.

Output to sudo fglrxinfo as follows:
Xlib: extension "XFree86-DRI" missing on disply "0.0".
display: 0.0 screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX indirect
OpenGL version string: 1.2 (1.5 Mesa 6.4.1)

Is that helpful?

---

### Post by lounsbud on 2006-09-29
Did my last post help or would more or other information help?

---

### Post by bodhi.zazen on 2006-09-29
sorry you last post helped me, but I can not (yet) return the favor.

It seems the installation of the ati driver failed and I do not know if it is because you did not follow the directions fully or if you card is not supported.

Starting with what can possibley be fixed, did you follow all the steps and enter all the various comands from the link I sent you?

sorry you last post helped me, but I can not (yet) return the favor.

It seems the installation of the ati driver failed and I do not know if it is because you did not follow the directions fully or if you card is not supported.

Starting with what can possibly be fixed, did you follow all the steps and enter all the various commands from the link I sent you?

If not, you will need to and let us know if you get error messages or stuck on any step.

If so, perhaps you will have better luck on the ATI forums.

I was hoping someone familiar with ATI would respond by now, looks like you are stuck with me :)

I was reading some other threads and some were talking about removing the ati driver, then removing the MEAS driver, and re-installing the ati driver.

Seemed like major surgery on X and I think the patient died. :twisted:

All I can say is I will keep your problem in mind.

Would you be so kind as to re-post your video card and monitor. That way it is somewhat easier as we do not need to read through 2-3 pages of posts to find it.

You could always start a new thread. In the title put something like help with ati driver and list your video card and monitor in your post. That may draw the attention of someone more knowledgeable with ati.

---

### Post by lounsbud on 2006-09-29
I will try your suggestions one more time to be sure I didn't mess something up alomg the way and repost if it doesn't work.

Thanks for all of your help and patience.

---

### Post by swp6499 on 2006-09-29
[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

i had the same problems and this is how i got it working for me...

hope i works for u

---


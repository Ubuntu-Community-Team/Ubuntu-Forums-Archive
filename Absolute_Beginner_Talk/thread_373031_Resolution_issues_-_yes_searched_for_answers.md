---
title: "Resolution issues - yes searched for answers"
date: 2007-02-28
forum: Absolute Beginner Talk
---

### Post by KatieCook on 2007-02-28
I have typed  sudo dpkg-reconfigure xserver-xorg into my term  ... What I do not know is where to find out which graphic card I have so when I type that in all it does is ask me for what driver and I do not know.  I am stuck at 640X480 res and I have a 19 inch screen.. It worked but today when I switched my boot from my other os it is stuck at this res.. ??

---

### Post by batholith on 2007-02-28
Just want to make sure I understand...you _do _or _do not_ know what kind of graphics card you have?

The best bet, whatever your card may be,  is to choose the "VESA" driver. That choice should work with the majority of cards out there and should give you the resolutions you're looking for....that said, it your wanting decent acceleration and want full performance out of your graphics card, I'd figure out what make/model card you have, then go through the appropriate setup for that particular card...

Good luck

---

### Post by confused57 on 2007-02-28
> **KatieCook said:**
> I have typed  sudo dpkg-reconfigure xserver-xorg into my term  ... What I do not know is where to find out which graphic card I have so when I type that in all it does is ask me for what driver and I do not know.  I am stuck at 640X480 res and I have a 19 inch screen.. It worked but today when I switched my boot from my other os it is stuck at this res.. ??

In a terminal, try:
```
lspci
```

Here's mine:
```
0000:01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 MX 420 ] (rev a3)
```
which clearly shows my video card.

---

### Post by KatieCook on 2007-03-01
> **confused57 said:**
> In a terminal, try:
```
lspci
```

Here's mine:
```
0000:01:00.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 MX 420 ] (rev a3)
```
which clearly shows my video card.

Thank You!!! 

  I am sorry if my question didnt sound clear it was just i could hardly see anything on the page I had to send that from my other linux boot.. I will go and try to fix that right now .. Thank you so much

---

### Post by kelbizzle on 2007-03-01
Alberto Milone's Nvidia script might help you out with no problems.

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by KatieCook on 2007-03-01
I found out which one I have,  but when I try to reconfigure it it does not change am I missing something?  It is so strange .. It worked and now it does not, the only thing that was done was my daughter was doing something on disney.com and it seemed fine, but when I switched ubuntu from freespire (which is working just fine) and then went back again, it is now at the "new" resolution.. I tried to change the resolution but it only offers one setting and thats it.  I am stumped.. Please help someone

---

### Post by randiroo76073 on 2007-03-01
I had to edit "xorg.conf" to get my resolution right, do following:
Open a terminal and type:     sudo gedit  /etc/X11/xorg.conf
when your editor opens scroll down till you see Section "Device Identifier" & a video card name[mine is @ line 91], check that it's reading the right card.
Just below that you will see a section "Monitor" , see if that has the right monitor in it[this is the section I had to change to get mine right] check HorizSync & VertRefresh. If you don't know, look on back of monitor or go to mfg's website.  Should look aprox like this:
"Monitor"
	Identifier	"ViewSonic PF790"
	Option		"DPMS"
	HorizSync	30-99
	VertRefresh	50-180

Below again is "Screen" top should look similar:
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV18 [GeForce4 MX 440 AGP 8x]"
	Monitor		"ViewSonic PF790"
	DefaultDepth	24
        Subsection    "Display"
scroll thru this till you see last 2:
they should read similar to:
	SubSection "Display"
		Depth		16
		Modes		"1400x1050" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1400x1050" "1280x1024" "1024x768" "800x600" "640x480"
If you need higher res add to beginning of "Modes"
Hope this helps

PS:  Be careful not to set anything higher than your monitor/videocard will run or you could damage them, a little homework here saves later headaches :)

---

### Post by confused57 on 2007-03-01
This guide may help you:
[http://users.bigpond.net.au/hermanzone/p7.html](http://users.bigpond.net.au/hermanzone/p7.html)
you could try to get dpkg-reconfigure xserver-xorg to automatically try to detect your hardware & if this doesn't work, then follow the directions from the above link, making sure to select the correct video driver & the resolutions that you want to use in X.
you could also try:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
when finished configuring, logout, then press ctrl+alt+backspace

You may have to manually edit your xorg.conf, as randiroo76073 suggested.

---

### Post by KatieCook on 2007-03-01
> **randiroo76073 said:**
> I had to edit "xorg.conf" to get my resolution right, do following:
Open a terminal and type:     sudo gedit  /etc/X11/xorg.conf
when your editor opens scroll down till you see Section "Device Identifier" & a video card name[mine is @ line 91], check that it's reading the right card.

  Ok the problem is, I can not see anything in that box I have a tab that of xorg.conf but that tab is empty..You said scroll down.. LOL there is nothing to scroll to. I am not sure what that means but it is empty. :confused:

---

### Post by confused57 on 2007-03-01
> **KatieCook said:**
> Ok the problem is, I can not see anything in that box I have a tab that of xorg.conf but that tab is empty..You said scroll down.. LOL there is nothing to scroll to. I am not sure what that means but it is empty. :confused:

Try to copy & paste this into a terminal:
```
gksudo gedit /etc/X11/xorg.conf
```

you might first want to create a backup, before opening & editing the file:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_bak
```

In fact, there may be a backup xorg.conf file in your /etc/X11 directory, you can check:
```
cd /etc/X11
ls
```

---

### Post by KatieCook on 2007-03-01
Oh my soul I think I figured out what caused it... Although I still dont know how to fix it but I have a pretty good idea what is causing it... I hooked up a Y splitter on the monitor as this is my daughters' computer and since I wiped out their windows and installed 2 linux distros on there they have only ever worked in windows and I was helping them out from across the room. So.. I got the y splitter so that we could both be looking at the same screen at the same time.  I have been trying to get these things to work and it just doesn't. So should I just go back to the way it was or is there a way to fix the new set up?
The strange thing is the freespire works like normal and that is why I think I didnt notice it because my daughter likes the ubuntu better and she booted it up and that was when we noticed it.  I think there has to be a way to set it up for ubuntu too.. :-k

---

### Post by KatieCook on 2007-03-02
*Bump*   Sorry I just cant use my ubuntu until it is fixed and I miss it, so far nothing I have tried is working. thanks

---


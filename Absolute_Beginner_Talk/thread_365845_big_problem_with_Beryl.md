---
title: "big problem with Beryl"
date: 2007-02-20
forum: Absolute Beginner Talk
---

### Post by goodbyewindows on 2007-02-20
I've got a new Ubuntu install on an old laptop. I've just installed Beryl. when I run it my screen goes all green and it's doubled in the top half of my monitor. It's unusable, when I hover over menus they're distorted and everything just goes 'funny'. See image to see what I'm talking about. When I press Ctrl-Alt-Backspace I see an NVidia logo then I log in, evrything seems normal. Then, my home directory opens up in Nautilus. The title bar on all windows has gone so I can only close apps with File>Quit. I'm unable to move them, running apps dont appear along the bottom panel, when I click on the show desktop icon I get an error message: "your window manager does not support the show desktop button, or you are not running a window manager"
[IMG]http://img400.imageshack.us/img400/8876/screenbr6.jpg[/IMG]

---

### Post by ashmew2 on 2007-02-20
Which nVidia card are u using ?and which version of Ubuntu ?  I was having that home directory thingy (it came in black white sorta colours) when i had installed Cmpiz.

---

### Post by Rhubarb on 2007-02-20
Wow!  That's a really nice psychedelic desktop there!  :p

You said that you're running it on an old laptop.
Perhaps your laptop is too old and hence doesn't have a powerful enough GPU to display Beryl?

Please state what graphics / processor / RAM you have in your old laptop.

IMO I would do without Beryl on an old laptop - it may be quicker for you to just re-install Ubuntu and stay away from Beryl.

---

### Post by goodbyewindows on 2007-02-20
The fractal wallpaper really adds to the effect! I have a Nvidia Quadro4 500 GoGL  and Ubuntu Edgy. Processor: Pentium 4M and 256mb of RAM. (im not too sure about all this, device manager only tells me about my graphic card, everything else has generic names)

---

### Post by grogger13 on 2007-02-20
Please correct me if im wrong(and i know this really isn't the whole problem), 256mb to run Beryl doesn't sound very good.

---

### Post by orb9220 on 2007-02-20
> I have a Nvidia Quadro4 500 GoGL

My guess is video driver and using shared memory for system and video.

What video driver are you using?

---

### Post by antharr on 2007-02-20
I agree with the previous post. 256 Megs of RAM isn't gonna cut it. Even if you get it up and going , things are gonna be sluggish.

---

### Post by goodbyewindows on 2007-02-20
Aww, no cool rotating cube thingys for me. I still love Ubuntu though. Any uninstallation guides for Beryl?

---

### Post by sephirothsigep on 2007-03-01
in your xorg.config make sure that you card is set for a depth of 24 instead of 16 so it would look like this. doing this fixed the greeen mess for me

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV34M [GeForce FX Go5200]"
	Monitor		"Generic Monitor"
	**DefaultDepth	24**
	SubSection "Display"

---

### Post by goodbyewindows on 2007-03-23
> **sephirothsigep said:**
> in your xorg.config make sure that you card is set for a depth of 24 instead of 16 so it would look like this. doing this fixed the greeen mess for me

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV34M [GeForce FX Go5200]"
	Monitor		"Generic Monitor"
	**DefaultDepth	24**
	SubSection "Display"

Cool, this fixed my problem. Wobbly windows and cube all working!

---


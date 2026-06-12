---
title: "Change Screen Resolution"
date: 2007-08-21
forum: Absolute Beginner Talk
---

### Post by jp316ad on 2007-08-21
I'm trying to install Ubuntu to dual boot on my computer, but the windows are so big that I can't even scroll down to click on "next". The only options I have are 600 and 800 - I would like to change it to 1024. Please help or point to a guide I can read. Thanks.

---

### Post by Inxsible on 2007-08-21
you'd probably have to change the settings in xorg.conf file.

```
gksudo gedit /etc/X11/xorg.conf
```Add the resolutions your graphics card can support in the Screen section.

---

### Post by chrome307 on 2007-08-21
This is something I would like to do as well but the resolutions are limited in the config file, however I do know that the gfx card that I am using supports 1280x1024 ( rough guess) 

```


Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Rage 128 Pro Ultra TF"
	Monitor		"AOC Spectrum"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection


```

---

### Post by LowSky on 2007-08-21
I had this problem too..

All i did was move the too menu bars to the right side of the screen and moved the install window a little higher

Once you install ubuntu everything should look better

---

### Post by Inxsible on 2007-08-21
> **chrome307 said:**
> This is something I would like to do as well but the resolutions are limited in the config file, however I do know that the gfx card that I am using supports 1280x1024 ( rough guess) 

```


Section "Screen"
    Identifier    "Default Screen"
    Device        "ATI Technologies Inc Rage 128 Pro Ultra TF"
    Monitor        "AOC Spectrum"
    DefaultDepth    24
    SubSection "Display"
        Depth        1
        Modes        [COLOR=Red]"1280x1024"[/COLOR] "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        4
        Modes        [COLOR=Red]"1280x1024"[/COLOR] "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        8
        Modes        [COLOR=Red]"1280x1024"[/COLOR] "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        15
        Modes        [COLOR=Red]"1280x1024"[/COLOR] "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        16
        Modes        [COLOR=Red]"1280x1024"[/COLOR] "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection "Display"
        Depth        24
        Modes        [COLOR=Red]"1280x1024"[/COLOR] "1024x768" "800x600" "640x480"
    EndSubSection
EndSection


```

Add the resolution that you know your card can support. I have put those in red for you. Technically you need only one resolution there, if you are not planning to change it often because by default, xorg will pick the highest resolution that your card can support. But its safe to keep the ones that were already there :)

---

### Post by jp316ad on 2007-08-21
Once I install Ubuntu, will I have to run a code so I can change the screen resolution? My card can handle 1280 x 1024 on Windows but I don't remember the limits right now since I am at work but will check when I get home.

---

### Post by Inxsible on 2007-08-21
> **jp316ad said:**
> Once I install Ubuntu, will I have to run a code so I can change the screen resolution? My card can handle 1280 x 1024 on Windows but I don't remember the limits right now since I am at work but will check when I get home.
Depends. If your graphics card drivers are installed correctly, you might not have to change anything and everything might work out of the box.

But even if it doesn't, I am sure it will be an easy fix and people here are pretty helpful :)

---

### Post by DVisions on 2007-08-21
I have just ran into this problem as well, here are the steps I took:

Put in the LiveCD
From the first menu hit the F4 button before selecting install.
Select 1024x768 16bit (just incase driver issues for 32bit color)
Install as normal.

Hope that helps.

---

### Post by jp316ad on 2007-08-21
Will try that and get back to ya. 

Thanks

---

### Post by chrome307 on 2007-08-21
[COLOR="Red"]**@ Inxisible**[/COLOR]

Works perfectly .... mucho gracias :)

Just a tiny problem ........ using my browser the text is miniscule now LOL ..... pt 8 ..... I should be able to change that somehow!!

---

### Post by Inxsible on 2007-08-21
> **chrome307 said:**
> [COLOR=Red]**@ Inxisible**[/COLOR]

Works perfectly .... mucho gracias :)

Just a tiny problem ........ using my browser the text is miniscule now LOL ..... pt 8 ..... I should be able to change that somehow!! Try changing the font size in the browser. If you are using Firefox then I think its at View --> Text Size. Increase or decrease it to the level you want.

---

### Post by chrome307 on 2007-08-21
That's okay it was easy enough to figure out use FireFox's help guide

EDIT--->PREFERENCES--->CONTENT ..... Fonts and Colors ..... Advanced ---> then change the minimum font size to 15

Alternatively as you suggested CTRL and +/- would do the same thing on a temporary basis, the above is permanent.

Thank you again :)

---

### Post by Inxsible on 2007-08-21
> **chrome307 said:**
> Thank you again :)Glad to help. i hope the OP is also able to fix his issues :)

---

### Post by chrome307 on 2007-08-21
With the help provided here by members I'm sure he will :)

---

### Post by jp316ad on 2007-08-23
I am still unable to change the resolution. I type the code in the terminal and this warning comes out but then what?

---

### Post by Qaeria on 2007-08-28
I have the same computer as the guy who started this thread, but I'm stuck on 800x600.  I really want to go to 1024x768, but no matter what, I can't.  I have ensured this resolution is in the .conf file, and tried setting the VGA from the live disc, but still no result.  I am using my Desktop effects, so I don't know if that is causing a problem.  I also have the proprietary Driver installed.

Anyone please help!

---


---
title: "trouble fixing refresh rate"
date: 2006-07-21
forum: Absolute Beginner Talk
---

### Post by Bocephus on 2006-07-21
I read through many threads before posting this and I am beginning to solve my issue but I'm stuck. When I first started Ubuntu my refresh rate was stuck at 60Hz. My first step was to go to Viewsonic's site and get the timings for my CRT. Here's what the user manual told me:                                                          
```

Maximum       VESA   1600 x 1280 NI @ 72 Hz     VESA 640 x 480 NI @ 160 Hz 
Refresh       VESA   1600 x 1200 NI @ 77 Hz     Mac  1152 x 870 @ 104 Hz   
Rates**       VESA   1280 x 1024 NI @ 89 Hz     Mac  1024 x 768 @ 117 Hz   
              VESA   1024 x 768 NI @ 117 Hz     Mac   832 x 624 @ 142 Hz
              VESA    800 x 600 NI @ 148 Hz     Mac   640 x 480 @ 160 Hz

```Notice how it doesn't list the horizontal and vertical sync rates seperately, only the product of those rates. Although I didn't have the exact numbers I decided to roll the dice and try modifying /etc/x11/xorg.conf anyway. In this section:
```
Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-192
	VertRefresh	43-60
EndSection
```I changed VertRefresh to 43-100 because 100Hz is the rate that I've used in Windows for years without issue on this display. 

Next I restarted X and now the Ubuntu desktop is set to a refresh rate of 85Hz by default. Any idea why that is? Shouldn't it set itself to 100Hz? Also, when I view the screen resolution preferences it gives me choices of 60, 70, 75, 85 and 87Hz at 1024x768 resolution whereas before it only gave me the option of choosing 60Hz at this resolution.
When I use the controls on my monitor to view more info it tells me that currently the horizontal rate is set to 68.65KHZ+ and vertical is set to 85 HZ+. I tried using this method to obtain H and V rates before modifying /etc/x11/xorg.conf but the monitor won't tell me what rates are available, only what the current rates are. Any ideas what's going on here? Thanks in advance to anyone who helps, this is my first post on these forums so be gentle.

---

### Post by OU812 on 2006-07-21
I have a viewsonic va520. After a few startups, my resolution suddenly was too low. So I decided to edit the refresh rates. I got the rates using sandra utilites in windows. If you still have windows, try using sandra to get the refresh rates for you. The standard edition of the program is free. Maybe check for it at [www.download.com](www.download.com)

john

---

### Post by Bocephus on 2006-07-22
> **OU812 said:**
> I got the rates using sandra utilites in windows. If you still have windows, try using sandra to get the refresh rates for you.I got Sandra and installed it. One problem though, it still only lists the product of the V and H refresh rates, not the seperate rates:```
Established Timings

Mode 0 : 720x400 70Hz NI

Mode 1 : 720x400 88Hz NI

Mode 2 : 640x480 60Hz NI

Mode 3 : 640x480 67Hz NI

Mode 4 : 640x480 72Hz NI

Mode 5 : 640x480 75Hz NI

Mode 6 : 800x600 56Hz NI

Mode 7 : 800x600 60Hz NI

Mode 8 : 800x600 72Hz NI

Mode 9 : 800x600 75Hz NI

Mode 10 : 832x624 75Hz NI

Mode 11 : 1024x768 87Hz I

Mode 12 : 1024x768 60Hz NI

Mode 13 : 1024x768 70Hz NI

Mode 14 : 1024x768 75Hz NI

Mode 15 : 1280x1024 75Hz NI

Mode 16 : 1152x870 75Hz NI
```

---

### Post by OU812 on 2006-07-22
Hmm. Well, try this: I use 1024x768. Horizontal: 30-62 Vertical: 50-75 (original config file had H=28-51 and V=43-60)

Sorry sandra didn't work for you. Try a google search - maybe someone has the technical specs you need.

john

---


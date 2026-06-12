---
title: "Four Minute Boot Time! Sony Vaio Notebook"
date: 2011-07-14
forum: Any Other OS
---

### Post by Rubicon421 on 2011-07-14
I just upgraded my Sony Vaio VGN-SZ650N Notebook from Linux Mint 9 (32 bit) to Linux Mint 11 (32 Bit). Previous boot time was less than a minute. Now, on a fresh install it takes almost four minutes to boot! 

I'm not sure where to start looking for the cause but will gladly post any info you need to help me determine it. Here's the product page for my model, with a link to the specs sheet:
[URL="http://javascript%3Cb%3E%3C/b%3E:moreinfowindow%28%27http://www.docs.sony.com/reflib/docget.asp?manualid=101886&template_id=1&region_id=1&DL=%27,600,560,10,10,%27Manuals%27%29"]
[/URL][http://esupport.sony.com/US/perl/model-documents.pl?mdl=VGN-SZ650N&region_id=1](http://esupport.sony.com/US/perl/model-documents.pl?mdl=VGN-SZ650N&region_id=1)


I think it has something to do with the video card drivers. This model has a hard ware switch to select the video mode and either run off of an integrated video chipset or an external, high performance card. 

*FROM THE SPECS SHEET:*
HYBRID GRAPHICS SYSTEM
Exclusive to VAIO® PCs, the revolutionary Hybrid Graphics System lets you
set your graphics performance. A simple hardware switch enables you to
toggle between an internal Mobile Intel® Graphics Media Accelerator X3100
for optimal power consumption with excellent performance and an
external NVIDIA® GeForce® 8400M GS GPU for even more robust
performance.

With Linux Mint 9, I always kept the switch in "Speed" mode- which uses the NVidia card and never had a problem. Now, I get the longer boot time in this mode, but in the "Stamina" switch position it boots in under 30 seconds. 

With the NVidia card activated, I have checked the Additional Drivers GUI and there are two drivers listed; the current version and version 173. Initially I chose the current (recommended) version, but I've also tried rebooting with version 173 activated and I get the same results. 

One other thing I have noticed is that the resolution of the GRUB boot menu is different depending on which card is activated. Also, the "stage" of the boot sequence that is longer is between *selecting a boot option* and when the cursor first appears. Before the boot option screen, and after the cursor appears, the system performs at the same speed in either mode. 

Any help or suggestions would be greatly appreciated! 

Thanks :)

---

### Post by Vansch76 on 2011-07-14
Rubi

Im have never used Mint, but it sounds like a bad install to me

if you are not to far along with installing your other files
I would try it again and let it reformat the entire drive again.

I seen this with Ubuntu Studio a few years ago, reinstalling 
did the trick

Hope this helps

Vanessa

---

### Post by Rubicon421 on 2011-07-14
I had already tried that before posting but thank you for the suggestion. 

I was playing around with some start up settings and changed the resolution of the GRUB menu. I went from the lowest one (which was currently selected) to the highest and that seems to have fixed it. I don't remember the exact resolution it was set to or what I changed it to, and I'm at work so I can't check- but that did make it boot way faster. 

When I get home I'm going to retest it a few times and make sure I can repeat the problem and then repeat fixing it.I also want to see what resolutions work, which ones don't, and which ones are native to my display so I can leave a more complete description before marking the thread solved, incase anyone else has a similar issue.

---

### Post by Perfect Storm on 2011-07-17
Moved to Other OS/Distro Talk.

---

### Post by Rubicon421 on 2011-07-17
I've retested it a few times and it looks like I only encounter the longer boot times when I have a low resolution (640X480 or 800X600) selected for the boot menu AND the graphics card switch is in "speed" mode.

I'm still not sure of the exact technical reason, maybe something to do with native resolutions.

---


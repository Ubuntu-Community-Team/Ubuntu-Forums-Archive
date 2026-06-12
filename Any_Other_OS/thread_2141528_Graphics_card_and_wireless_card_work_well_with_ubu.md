---
title: "Graphics card and wireless card work well with ubuntu and linux mint?"
date: 2013-05-02
forum: Any Other OS
---

### Post by snowlizard31 on 2013-05-02
I'm building a computer and I'd like to know if these parts will run on linux and do they have reliable drivers on linux. I'd like to game on my future rig using linux but I don't want into problems. I'm not too sure about the wireless adapter though can some one show me to a reliable one that runs great both in linux and windows? Thanks for the help in advanced!:)


[http://www.newegg.com/Product/Product.aspx?Item=N82E16814202030](http://www.newegg.com/Product/Product.aspx?Item=N82E16814202030)
[http://www.newegg.com/Product/Product.aspx?Item=N82E16833320074](http://www.newegg.com/Product/Product.aspx?Item=N82E16833320074)

---

### Post by mips on 2013-05-03
[http://ubuntuforums.org/showthread.php?t=1814675](http://ubuntuforums.org/showthread.php?t=1814675)
[http://ubuntuforums.org/showthread.php?t=1988161](http://ubuntuforums.org/showthread.php?t=1988161)

So that card looks like it could be a problem but wait and see what others have to say.


GPU will work and is supported by later AMD Catalyst drivers. Personally I would go for nVidia but that's due to my belief that they have better driver support in Linux. They also support their cards for much longer than AMD wrt to drivers.

---

### Post by kevdog on 2013-05-03
Mips -- that's interesting what you say about the NVIDIA cards with the neuvaux driver.  I always hear complaints about how the driver breaks with kernel upgrades.  I dont have a NVIDIA card so I really can't comment.  

The only video cards I have in computers that are running Linux have either the integrated intel chipset -- which works really well, and an ATI card which is supported by the xf86-video-ati (Open source driver), rather than the closed source catalyst driver (which I couldn't get working with the version of my card although it said it was supported). In all honesty I've heard a ton of complaints about the catalyst driver as well, so I'm not sure what the best solution is here.  I did the support after I got the hardware -- meaning had the hardware and then looked to see whatever would work.  I haven't done what is described in this thread which is buy the hardware that best works for linux - for GPU cards.

On another note I did buy a wireless linux adapter (USB) that stated on the box it was specifically supported by Linux.  The good and the bad on that one was the minute I picked it up and plugged it in it worked.  The bad part is that the hardware keeps going into some sleep type of state with activity and won't wake up unless I'm physically sitting at the computer its at so running a server off the machine is a nightmare.  I've tried posting numerous times which I've received some support but no failsafe solution.  I've adjusted the Qos settings which help but don't eliminate the problem.  Needless to say I'd take any so called problem Broadcom chipset over this supported Asus USB N-13 device -- in which I can't for the life of me recall the chipset inside.

---

### Post by mips on 2013-05-03
> **kevdog said:**
> Mips -- that's interesting what you say about the NVIDIA cards **with the neuvaux driver**.  I always hear complaints about how the driver breaks with kernel upgrades.  I dont have a NVIDIA card so I really can't comment. 

No no no no :D I'm talking about the proprietary nVidia drivers which is what I have always used.

---

### Post by snowlizard31 on 2013-05-03
Thank you guys! But If you don't mind can someone tell me what the equivalent of a  AMD Radeon 7870 HD would be with Nividia. The original reason for choosing the 7870 was because I want to run games on utlra and it seeems like this card can do the job but if Nividia has better support for linux than I might opt out to get one of their cards.

Hey kedog how has your experience been  AMD GPU's- if you don't mind me asking - are they reliable for use in linux? I have an AMD ATI Radeon 2600 Pro HD but my experience with linux hasn't been to well with that particular card.

---

### Post by mips on 2013-05-03
> **snowlizard31 said:**
> Thank you guys! But If you don't mind can someone tell me what the equivalent of a  AMD Radeon 7870 HD would be with Nividia.

Earlier on you mentioned a 7950 [http://www.newegg.com/Product/Product.aspx?Item=N82E16814202030](http://www.newegg.com/Product/Product.aspx?Item=N82E16814202030) so wich is it?

In linux that card you mentioned compares to the GTX 680 which costs more I think so if you do most of your gaming in windows go for the AMD/ATI card.

[http://www.newegg.com/Product/Product.aspx?Item=N82E16814202030](http://www.newegg.com/Product/Product.aspx?Item=N82E16814202030)

You gotta be a bit more specific. Like what's your budget for a GPU and on which platform do you intend to do most of your gaming?

---

### Post by snowlizard31 on 2013-05-04
Sorry mips I meant to say the 7950 and my budget would have to be 400 and below. I'm mostly going to game on windows but I want to be able to render stuff fast in blender on linux and also not have problems with the graphics driver.

---

### Post by Perfect Storm on 2013-05-04
I'm doing gaming with a GTX285 (1GB) on Ubuntu 13.04 on max settings (res. 1680x1050) smoothly.

GTX x10-x20 = lowend
GTX x40-x60 = midend
GTX x85-x95 = highend

The x is version of Nvidia card.

---

### Post by mips on 2013-05-04
> **snowlizard31 said:**
> Sorry mips I meant to say the 7950 and my budget would have to be 400 and below. I'm mostly going to game on windows but I want to be able to **render stuff fast in blender on linux** and also not have problems with the graphics driver.

Currently your only option for GPU acceleration is via CUDA which is only supported by nVidia cards. Acceleration via OpenCL which would work on nvidia & amd/ati is currently on hold due to technical issues and there's no time frame for when it will be implemented, if ever.

[http://wiki.blender.org/index.php/Dev:Ref/Release_Notes/2.61/Cycles](http://wiki.blender.org/index.php/Dev:Ref/Release_Notes/2.61/Cycles)
[http://www.studiorola.com/news/cycles-blenders-gpu-accelerated-renderer/](http://www.studiorola.com/news/cycles-blenders-gpu-accelerated-renderer/)
[http://wiki.blender.org/index.php/Dev:2.6/Source/Render/Cycles](http://wiki.blender.org/index.php/Dev:2.6/Source/Render/Cycles)

[http://wiki.blender.org/index.php/Dev:2.6/Source/Render/Cycles/ToDo#On_Hold](http://wiki.blender.org/index.php/Dev:2.6/Source/Render/Cycles/ToDo#On_Hold)
> 
[LIST]
[*]OpenCL support for AMD/NVidia GPU rendering is currently on hold. Only a small subset of the entire rendering kernel can currently be compiled, which leaves this mostly at prototype. We will need major driver or hardware improvements to get full cycles support on AMD hardware.
[/LIST]


So my advice would be to get the best nVidia GPU you can for $400. GTX 670 is definitely in that price range and maybe you can squeeze a GTX 680 in if you shop around or look for deals on the net. Financially a good GTX 670 would make more sense than a GTX 680. Gaming wise the performance is not that far of but as far as I know the GTX 670 has a few less CUDA cores than the GTX 680 but then again for rendering a GTX 670 will work while a AMD 7950 would not. If it was me I would get a nice GTX 670 and save a $100 or so over a GTX 680, but at the end of the day the decisions is yours and yours alone to make. Can also look for cards with BOOST feature.

---

### Post by mips on 2013-05-04
> **Artificial Intelligence said:**
> I'm doing gaming with a GTX285 (1GB) on Ubuntu 13.04 on max settings (res. 1680x1050) smoothly.


For linux that card is fine but if you wanna game in windows with modern titles you gonna struggle as they can be demanding. Also not great for CUDA assisted rendering in Blender.

---

### Post by snowlizard31 on 2013-05-04
Thanks mips the information you've given has really helped I will get a gtx 670 then :)

---


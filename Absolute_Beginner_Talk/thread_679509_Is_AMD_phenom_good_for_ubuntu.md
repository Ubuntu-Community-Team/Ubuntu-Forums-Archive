---
title: "Is AMD phenom good for ubuntu?"
date: 2008-01-27
forum: Absolute Beginner Talk
---

### Post by Bluestick on 2008-01-27
he guys im building a new PC. 
 AMD Phenom 9500 2.2
 2 gig ram
 200 gig HD
 gForce 7900 GT factory OC.
----- what u guys think? im all about UBUNTU 7.10 :)
i currently have a amd athlon 3400+ with 1.5 ram but single core!!! wich sucks

 i herd the AMD phenon is a good match with Ubuntu...

---

### Post by toupeiro on 2008-01-27
I cannot foresee a problem with the Phenom processor and ubuntu.  The 2.6 SMP kernel will handle quad x64 just fine.  Enjoy that beast.

---

### Post by Twintop on 2008-01-28
Bluestick, when you get your system up and running can you report back something for me? I just build a Phenom 9600 BE system with a Biostar T770 A2+ motherboard, but haven't been able to get CPU Frequency Scaling to even be detected at all, even after upgrading the BIOS on it. If you can get your system to work so CPU Scaling, it'd be able to tell me if it is my motherboard or a lack of support in the Kernel for it right now. Thanks!

---

### Post by EnglishRob on 2008-03-09
Hi Bluestick / Twintop,

Bluestick, ot sure if you've built your Phenom system yet.  I've built up a system with a Phenom 9600 with 4GB of ram.  Under Ubuntu 7.10 I was getting all sorts of random freezes.  Sometimes it would run for 5 minutes and freeze, other times it would run for an hour or so without freezing.

I've now installed Ubuntu 8.04 Alpha 6 and I'm happy to report it works fine.

Not saying that you'd find that though.  If it's any help, I'm using an MSI K9A2 CF motherboard, 4GZ of OCZ PC8000 DDR2 memory, NVidia Geforce 7200GS and a Zalman heatsink and fan to cool the thing down.

Twintop, I've also had problems with CPU scaling.  Not sure if it's just the Phenom which isn't supported?

Didn't work for me on Ubuntu 7.10 and it still doesn't work on 8.04.

Rob

---

### Post by jmontelius on 2008-03-13
Have had 7.10 on a ASUS M3A32-MVP Deluxe with a 9500 Phenom. Everything was up and running from start. lm-sensors does not yet support the K10 architecture but apart from that everything runs smoothly... and fast , try make -j4  :)

---

### Post by jseiser on 2008-03-13
i have a 9500 and geforce 9600 and ubuntu gutsy/hardy 64, and arch 64 both crash when using the nvidia driver.  32 bit works fine with arch.   I imagine the problem is with the nvidia driver.  but this thing flies on arch, i took the AMD patch off in the bios, and started o clocking, and its still stable.

---

### Post by isigrim on 2008-04-15
Hi all,

i am new here, but since i worked with ubuntu for some time now, i thought signing up here would be a good idea.

To Ubuntu and Phenom:
- install powernowd *(sudo apt-get install powernowd)* ([link to the powernowd ubuntuusers wiki](http://wiki.ubuntuusers.de/powernowd))
- load module for powernow-k8 (there is no k10 module yet, as far as i know) *(sudo modprobe powernow-k8 )*
- set powernowd to passive mode *(sudo powernowd -m 2)*


this helped me getting at least two steps (1200Mhz and 2400 Mhz) on my Phenom 9750
thats not much, but helps to cool everything down a little better. Even setting 13 steps (+-100Mhz each) manually didn't help.

A big problem i still have is the performance when rendering in blender though.
With 2 threads and 1200 Mhz i get almost the same speed as with 4 threads and 2400 Mhz. Don't think that this is correct....

My configuration
MB: Asus M3N78-EH
CPU: Phenom X4 9750
RAM: 2 GB DDR-2 800Mhz
GC: ATI Radeon 3450
OS: Ubuntu 8.04 beta

---

### Post by stchman on 2008-04-15
> **Bluestick said:**
> he guys im building a new PC. 
 AMD Phenom 9500 2.2
 2 gig ram
 200 gig HD
 gForce 7900 GT factory OC.
----- what u guys think? im all about UBUNTU 7.10 :)
i currently have a amd athlon 3400+ with 1.5 ram but single core!!! wich sucks

 i herd the AMD phenon is a good match with Ubuntu...

Yes, the Linux kernel can make use of all those cores.  I run a quad core and rarely does any of the 4 cores get over 30%.  I used to run a single core Athlon 64 and it would go near 100% when being taxed.

---

### Post by Twintop on 2008-04-15
isigrim, I had downloaded the powernow-k8 but never modprobed it. I followed your instructions and have two options, 1.15GHz / 2.30GHz (Phenom 9600 BE) as well as the govenor options Conservative/Ondemand/Performance/Powersave.  Even though I was hoping to have more scaling frequencies, I'm excited about this because one of the great features of the Phenom line is independant scaling/govenoring of each core...and IT WORKS. I've got 1 core running at 2.30GHz, another at 1.15GHz, and the other two at Ondemand and the first two are staying constant while the second two are fluctuating as needed (and as advertised!). 

This is really important to me because I've had the TLB errata affect me, and, I've read that it is in the 3rd core (of the 4, not core3 as the system sees it) frequency that causes the TLB to pop it's head up. So, in theory, if I can clock that core to a lower frequency I'll be stable. If it means that for the time being one core is at 50%, then so be it. It's better than having the system choke and reboot.

---

### Post by isigrim on 2008-04-16
I am glad that i was able to help you.

Don´t forget to write the powernow-k8 into your /etc/modules so that it is loaded at startup. 
ii also read that it helps inserting cpufreq-ondemand.

---

### Post by Csylleste on 2008-04-16
This is not to bash on anyone for building a quad-core system, but I suggest leaving them be for the time being. The quad-core set is not yet entirely stable, even in the AMD's. I personally suggest giving AMD another 6 months before building a quad-core system. This should give those guys enough time to stabilize the system.

Other than that. Quad-core is actually perfect for Linux in general because of the new 128 potential of the heardware, since Ubuntu 6.10 and higher have the architecture to support it.

---

### Post by stchman on 2008-04-16
> **Csylleste said:**
> This is not to bash on anyone for building a quad-core system, but I suggest leaving them be for the time being. The quad-core set is not yet entirely stable, even in the AMD's. I personally suggest giving AMD another 6 months before building a quad-core system. This should give those guys enough time to stabilize the system.

Other than that. Quad-core is actually perfect for Linux in general because of the new 128 potential of the heardware, since Ubuntu 6.10 and higher have the architecture to support it.

I run a Core 2 Quad under Feisty and is supported OOB and is completely stable.

---

### Post by isigrim on 2008-04-17
Stability doesn't seem to be the problem, at least with Hardy (8.04) from what i can see. The stability issues are not a problem anymore with the phemons (9x50) produced with the b3 stepping.
I wanted to set up my system with W**dows first but then decided to give ubuntu 8.04 beta a try, which was a good idea to say the least. 
But: The performance of the Phenom is (at the moment) not at all too impressive, especially when compared to my Core2 E6600, which has the same Mhz, but only two cores compared to the four of the phenom.
I hope this situation will improve with future Kernels and developments in Ubuntu.

Still i think there is nothing bad about using the new Phenoms with Ubuntu. The Quad core systems are quite stable i think, but there has to be done - in some cases - a lot of software customization to support more than two cores efficiently.

When it comes to power consumption, i would suggest waiting (in case of AMD) or saving money (in case of intel) for the 45nm quadcores

---

### Post by cubeist on 2008-04-20
Phenom 9550 quad is great.  Absolutely rock solid using hardy heron RC.  During normal use the four cores rarely move above the powernow 1100 MHz step...for example, writing this message while listening to music and downloading file in background: two cores are at 0.1%, one core around 4% and one at about 14%, all at 1100MHz.

In regards to performance, for the price of an AMD quad system, I don't think it can be beat.  Sure the intels test faster, but for day to day system usage the AMD 9550 is perfectly snappy.  I have no regrets for choosing AMD over Intel.

---

### Post by PhatKat on 2008-05-10
OMG OMG! I may be able to get a 9600 B2 on the (dirt) cheap - am currenly on Gutsy and x2 4000+/VIA mATX so am thinking of moving up to x4 9600/780G mATX and 64 bit Heron. How is that integrated Radeon 3200 performing with Heron anyone know? Also if running on integrated you think an Antec Eartwatts 380W would suffice with 1-2 HDDs, 2 x 120mm fans, 1-2 optical drives?

---

### Post by wallyworld on 2008-05-12
Phatkat:

I'm running a Gigabyte GA-MA78GM-S2H with the 780G chipset and HD3200 integrated graphics with a Phenom 9550.  It works fine.  Used the Hardware Drivers app to load up the ATI driver and it seems to work OK.  Still need to figure out how to get full support for Cool N Quiet (as yet I run with it turned on in BIOS, but not recognized in Ubuntu).  Only issue I ran into was Avahi hostname resolution doesn't work unless I enable multicast on eth0.  As far as a powersupply goes, the EA380 should be fine.  I have 2 HDs in RAID 0, 1 DVD drive and under a full CPU load, it's about 170W.  With a full CPU load and the graphics working, about 180W.  Performance-wise, the HD3200 doesn't do as well as even some low end NVIDIA stuff for 3D, but for 2D it's great.  I would say it's due to the poor driver support for Linux from ATI.  Have fun with your new system!

---

### Post by PhatKat on 2008-05-13
Thanks Wallyworld but i'm still researching the exact 780G mobo to get and hopefully it officially supports 9850BE but heard theres a 95W version coming up end of the year anyway so i'm in a bit of a limbo :P

---

### Post by cubeist on 2008-05-13
> **PhatKat said:**
> Thanks Wallyworld but i'm still researching the exact 780G mobo to get and hopefully it officially supports 9850BE but heard theres a 95W version coming up end of the year anyway so i'm in a bit of a limbo :P

I'll add a +1 for the GA-MA78GM-S2H.  Everything on the board was fully recognized in ubuntu (haven't tested the hdmi or esata yet). The 780g is a competent chipset (although it seems to run really, really hot!).  The 3200 gets me about 3300.0 fps in glxgears which is fine unless you are a serious gamer.

A word of caution... There are no 780g boards that support the 9850...well, not really well... here, read these two articles:

[http://www.anandtech.com/showdoc.aspx?i=3279&p=3](http://www.anandtech.com/showdoc.aspx?i=3279&p=3)

[http://anandtech.com/mb/showdoc.aspx?i=3299](http://anandtech.com/mb/showdoc.aspx?i=3299)

---

### Post by cubeist on 2008-05-13
> **wallyworld said:**
> Phatkat:

I'm running a Gigabyte GA-MA78GM-S2H with the 780G chipset and HD3200 integrated graphics with a Phenom 9550.  It works fine.  Used the Hardware Drivers app to load up the ATI driver and it seems to work OK.  Still need to figure out how to get full support for Cool N Quiet (as yet I run with it turned on in BIOS, but not recognized in Ubuntu).(..)

I am not sure I understand what you mean by full cool n quiet support... As far as I know, all cool and quiet does is measure the cpu temp in bios and adjust the cpu's fan speed.  There is no cool n quiet program outside of bios...However, for user space applications, do you have powernow configured... because powernow is the program (daemon actually) that adjusts cpu frequency on the fly according to program demand.  Unfortunately there are only two steps on phenom processors in linux, half speed and full speed...

---

### Post by cesaraugustosimoncalle on 2008-05-22
Hi, I have a same computer like you, all the same, but my graphical card is geoforce 8500. I can´t install ubuntu 8.04 64 bit, when is installing the copi files is slow other time not run I download 3 times de cd live and saw the md5sum, and all ok, Please Why I can´t install the ubuntu. I install in my partition d: that I say in instalation that format this in ext3 format, this i do when the installation ask me where install I put manual and put D: like ext3 for \, I don´t use any partition to memory to the instalation because I have 8 gb

---

### Post by PhatKat on 2008-05-23
Hi again! Just to confirm with you guys: is this CPU support list for real on this site:
[http://global.msi.com.tw/index.php?func=prodcpusupport&prod_no=1436&maincat_no=1&cat2_no=171&cat3_no=#menu](http://global.msi.com.tw/index.php?func=prodcpusupport&prod_no=1436&maincat_no=1&cat2_no=171&cat3_no=#menu)
If so i may have settled the motherboard part of my next PC :guitar:

---

### Post by PhatKat on 2008-05-29
Hmm i am getting a bit worried when i read of how Vista SP1 forces TLB fix onto phenom B2 users:
[http://www.hardwarecanucks.com/forum/microsoft-o-s-s-xp-vista/5634-helping-hand-vista-service-pack-1-vs-your-phenom.html](http://www.hardwarecanucks.com/forum/microsoft-o-s-s-xp-vista/5634-helping-hand-vista-service-pack-1-vs-your-phenom.html)
I am assuming there isn't such thing in Ubuntu 8.04lts right?

---

### Post by arnabt on 2008-05-29
looks perfectly good to me

---

### Post by soxs on 2008-06-02
> **Twintop said:**
> isigrim, I had downloaded the powernow-k8 but never modprobed it. I followed your instructions and have two options, 1.15GHz / 2.30GHz (Phenom 9600 BE) as well as the govenor options Conservative/Ondemand/Performance/Powersave.  Even though I was hoping to have more scaling frequencies, I'm excited about this because one of the great features of the Phenom line is independant scaling/govenoring of each core...and IT WORKS. I've got 1 core running at 2.30GHz, another at 1.15GHz, and the other two at Ondemand and the first two are staying constant while the second two are fluctuating as needed (and as advertised!). 

This is really important to me because I've had the TLB errata affect me, and, I've read that it is in the 3rd core (of the 4, not core3 as the system sees it) frequency that causes the TLB to pop it's head up. So, in theory, if I can clock that core to a lower frequency I'll be stable. If it means that for the time being one core is at 50%, then so be it. It's better than having the system choke and reboot.
Don't care about TLB bug, since kernel 2.6.2x (don't know the exact number of x) there is a fix included^^.

---

### Post by Twintop on 2008-06-02
> **soxs said:**
> Don't care about TLB bug, since kernel 2.6.2x (don't know the exact number of x) there is a fix included^^.

soxs, is that the fix that decreases the performance by ~20%? It's good to know that the problem has a fix of some sort included, though. Thanks!

---

### Post by soxs on 2008-06-03
> **Twintop said:**
> soxs, is that the fix that decreases the performance by ~20%? It's good to know that the problem has a fix of some sort included, though. Thanks!
I do not know about performence decreaments because of that fix. But as far as i heard it should be only get in rare cases beyond the 5% line. So this is a quite small a mount and it won't hurt you that bad.

---

### Post by Twintop on 2008-06-03
Thanks again, soxs. I did some hunting and found a thread on AMD's forums about this ([http://forums.amd.com/forum/messageview.cfm?catid=319&threadid=94240](http://forums.amd.com/forum/messageview.cfm?catid=319&threadid=94240)) and it says is only a 1-2% performance hit. Sounds great to me. :-D

---

### Post by PhatKat on 2008-06-03
Hmm is that confirmed cos the fix in windows had far greater impact on phenom performance! If phenom B2 takes such a minor hit in linux then bring on the used B2 phenom at low low prices to us Ubuntu users i say :guitar:

---

### Post by bobpur on 2008-06-04
Thanks for all of the info concerning the AMD Quad-cores. You all have answered a few of the questions I've knocked about as I sit here amongst the boxes and manuals of my next build. A 9850 AMD 4 core on an Asus M2R32-MVP mobo (Gotta flash the BIOS to get this board to work with a Quad Core) 8 Gbs Corsair RAM, An Asus 3870 x 2 Videocard (A second for Crossfire will be here in another day or so).
If I can't get the 4 core to work with this mobo; I have an AMD 6400 X2 that will work in it for now.
It'll run either 64-bit Ubuntu or 64-bit Vista (or both).

---

### Post by soxs on 2008-06-04
> **PhatKat said:**
> Hmm is that confirmed cos the fix in windows had far greater impact on phenom performance! If phenom B2 takes such a minor hit in linux then bring on the used B2 phenom at low low prices to us Ubuntu users i say :guitar:
Well, I confirm this. Ubuntu!=M$ ^^ so that clarifies a lot :-P
I've got phenom 9500 from stepping 2 (which has the TLB bug) well, and it didn't hurt in any cases so far.
[COLOR=Red][B]
STOP[/B][/COLOR]
>  An Asus 3870 x 2 Videocard (A second for Crossfire will be here in another day or so).CROSSFIRE IS STILL NO GO ON LINUX!!! You won't be able to use both of your GPUs!!

---


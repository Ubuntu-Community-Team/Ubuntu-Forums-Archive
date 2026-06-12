---
title: "[SOLVED] beginer here"
date: 2008-01-18
forum: Absolute Beginner Talk
---

### Post by cragger on 2008-01-18
hey everyone, i have have just installed ubuntu onto my second partition with vista being first OS. i have been trying for hours to get my graphics card to work and my wireless interent to work, i have an hp pavili dv2410ca laptop and it would be great for any of you guys to help me, tell me what i need to tell you so u can help me,
thanks, ryan

---

### Post by bwhite82 on 2008-01-18
[Have you perused the Wiki?]("http://help.ubuntu.com/community")

---

### Post by JoshuaRL on 2008-01-18
What exact type of graphics card and wireless card does it have?

---

### Post by thelatinist on 2008-01-18
> **cragger said:**
> hey everyone, i have have just installed ubuntu onto my second partition with vista being first OS. i have been trying for hours to get my graphics card to work and my wireless interent to work, i have an hp pavili dv2410ca laptop and it would be great for any of you guys to help me, tell me what i need to tell you so u can help me,
thanks, ryan

Let's start by finding out exactly what graphics card and wireless card you have:

Please open the Terminal (Applications > Accessories > Terminal) and run the following commands:

```
lspci | grep VGA
```

and

```
lspci | grep Wireless
lspci | grep 802.11
```

Post the results here.

---

### Post by cragger on 2008-01-19
lspci | grep VGA

00:05.0 VGA compatible controller: nVidia Corporation C51 [Geforce 6150 Go] (rev a2)



the other command wasnt working.. like it didnt do anything when i typed it in


ryan@ryan-laptop:~$ lspci | grep Wireless
ryan@ryan-laptop:~$ lspci | grep 802.11
ryan@ryan-laptop:~$

---

### Post by JoshuaRL on 2008-01-19
Is your wireless card one you put into the card slot?

---

### Post by mitar on 2008-01-19
I was thinking about installing Linux on mu HP pavilion dv6000 but people from hp say that "hp doesn't support Linux", which means you will have to find the drivers somewhere. Once, I installed Windows XP over Vista and I ended up calling hp support to ask them to send me recovery CDs, because both graphic card and internet were not working properly. I could not find those drivers for xp anywhere. SO... if someone has an idea where we could find these drivers, it will be great.

---

### Post by JoshuaRL on 2008-01-19
Technically, HP doesn't support Linux.  Which means that when you have a problem you can't just call HP and have them tell you how to fix it.  But, that's why there's the Ubuntu Forums.  

I have Xubuntu running on an old HP Omnibook and it works great.  It detected the graphics, keyboard, DVD drive, everything.  It works really well.  And all on a laptop that would never be able to run Vista.  

If you have any problems, come here and we will be happy to help you fix whatever you need.

---

### Post by doorknob60 on 2008-01-19
What isn't working about your graphics card? Nvidia cards work well in Ubuntu and I think my HP laptop has the same one :O (It works fine by the way). Also, your wireless internet could be a Broadcom, which is a pain in the butt (trust me it is), but there are plenty of guides and how to's but don't look yet until we know what your wireless card is. Can you post the output of ```
lspci
``` Because apperantly the last two lspci commands didn't show anything...

---

### Post by mitar on 2008-01-19
I do not have linux (yet) but I would like to install it, since vista is very demanding (that's why I switched it for windows XP) and I would like to try something different. I am starting to learn programming in c/c++ languages so it would be great if I could make use of it, and that command line wouldn't be any problem since I use it on Autocad and Rhino very often. So do you know how to fix the problem with the graphic card and Internet (because I am pretty sure I will have big problems if I install it). And if live cd would work would it mean that full version will work also?

---

### Post by JoshuaRL on 2008-01-19
It should, yeah.  But how about we take it slow.  If you could post your video card, we could see if you will have any problems.  What exactly are you concerned about with internet?  Are you using wired or wireless?

---

### Post by ubuntu-freak on 2008-01-19
If you do install Ubuntu, use my how-to and get streaming, multimedia, video (including encrypted DVD's) working.
 
[http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)
 
It's how I set my system up. Beats searching different threads.
 
Nathan

---

### Post by mitar on 2008-01-19
Ok. The graphic card is Nvidia Ge Force 7150 with 559 Mb of total video memory (64 from dedicated video memory and 495 mb from shered system memory). 
You know how some laptops have a switch for wireless? Well, when I swithced to XP, it did not work. I thought it's broken first. I also tried with the cable and it did not work either.

---

### Post by JoshuaRL on 2008-01-19
Cool with the wireless.  Nvidia is pretty well supported in linux so it should work really well.

But I'm not sure about the wireless.  Could you explain a little more?

---

### Post by mitar on 2008-01-19
look, I am foreigner so I can't always express myself the way I want :-) but,... I think the problem occurs because the drivers for vista and xp are not the same. Actually, (some) drivers that were installed on vista could not be found for xp anymore (at least, that's with hp PCs). I remember I had to find every single driver becaues nothing was working properly (keybord was aslo big problem). For graphics, there was some kind of driver, because it was able to do something visually :-) but I could not choose any resolutions and it was very slow when I tried to move certain window or scroll the page. but for the internet, it looked like it's not there. That's all I can say. [COLOR="Black"]That's just like you turn the light switch in the room but the light can not be turned on. You change the bulbs but the same thing heppens. you open the switch to chech for electricity, everything looks ok. we assume the power is not gone.[/COLOR]

When I asked hp person, he literally told me "if you want to use linux on hp laptop you can, but you will have to find all the drivers on your own (if any)". Dell PCs, on the other hand, have no problems with changing operating systems.

---

### Post by JoshuaRL on 2008-01-19
> **mitar said:**
> look, I am foreigner so I can't always express myself the way I want :-)
Don't worry man, we're here to help.  You actually do really well for starting from another language.  I promise the switch to Linux will be easier than that.  You rock.

> but,... I think the problem occurs because the drivers for vista and xp are not the same. Actually, (some) drivers that were installed on vista could not be found for xp anymore (at least, that's with hp PCs). I remember I had to find every single driver becaues nothing was working properly (keybord was aslo big problem). For graphics, there was some kind of driver, because it was able to do something visually :-) but I could not choose any resolutions and it was very slow when I tried to move certain window or scroll the page.
Don't worry about all those Windows issues.  As amazing as it may seem since they have a monopoly on the operating systems on PCs, Microsoft messes stuff up come upgrade time.  They would rather have you buy a new one than try to only upgrade the OS.  But a lot is supported and automagically detected out of the box for linux, especially Ubuntu.  So you may have a way easier time.

> but for the internet, it looked like it's not there. That's all I can say. [COLOR="Black"]That's just like you turn the light switch in the room but the light can not be turned on. You change the bulbs but the same thing heppens. you open the switch to chech for electricity, everything looks ok. we assume the power is not gone.[/COLOR]
Okay.  Is this in the Ubuntu Live CD, a fresh install of Ubuntu, or from Windows?  I think this may be the only problem you have, and maybe not a problem anyway.

> When I asked hp person, he literally told me "if you want to use linux on hp laptop you can, but you will have to find all the drivers on your own (if any)". 
True, but that's the way it is on all computers except ones you buy with Linux preinstalled.  That's what's so great about Linux, it supports the majority of computers without having to track down obscure drivers.  And even if you do have to manually configure stuff, it's so so much easier since Linux is open source and designed for you to be able to tweak it.  Honestly, I think the HP person said that because they kinda want you to be scared away from Linux since they don't have control over it and can't fix it for you.

> Dell PCs, on the other hand, have no problems with changing operating systems.
Oh dude, so not true.  I had a ton of problems getting my video drivers working for my ATI Radeon Mobility 7500.  But now they are and I understand a ton more about the system.  So cheer up, we'll get it solved.

---

### Post by cragger on 2008-01-19
ok, so the problem with my graphics card is it wont let me change the visual effects from none t extra, like when i click to change it it asks me to enable driver but when i enable it another window opens saying 
"The software source for the package
               nvidia-glx-new
              is not enabled."

so i was assuming there was something wrong with it.

and with the wireless i go though the whole configuration and it never works... maybe my problem is simpler than it seems but im not sure what to do, 

the code that you told me type into the terminal resulted in the following:


ryan@ryan-laptop:~$ lspci
00:00.0 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C51 Memory Controller 0 (rev a2)
00:00.2 RAM memory: nVidia Corporation C51 Memory Controller 1 (rev a2)
00:00.3 RAM memory: nVidia Corporation C51 Memory Controller 5 (rev a2)
00:00.4 RAM memory: nVidia Corporation C51 Memory Controller 4 (rev a2)
00:00.5 RAM memory: nVidia Corporation C51 Host Bridge (rev a2)
00:00.6 RAM memory: nVidia Corporation C51 Memory Controller 3 (rev a2)
00:00.7 RAM memory: nVidia Corporation C51 Memory Controller 2 (rev a2)
00:02.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:03.0 PCI bridge: nVidia Corporation C51 PCI Express Bridge (rev a1)
00:05.0 VGA compatible controller: nVidia Corporation C51 [Geforce 6150 Go] (rev a2)
00:09.0 RAM memory: nVidia Corporation MCP51 Host Bridge (rev a2)
00:0a.0 ISA bridge: nVidia Corporation MCP51 LPC Bridge (rev a3)
00:0a.1 SMBus: nVidia Corporation MCP51 SMBus (rev a3)
00:0a.3 Co-processor: nVidia Corporation MCP51 PMU (rev a3)
00:0b.0 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0b.1 USB Controller: nVidia Corporation MCP51 USB Controller (rev a3)
00:0d.0 IDE interface: nVidia Corporation MCP51 IDE (rev f1)
00:0e.0 IDE interface: nVidia Corporation MCP51 Serial ATA Controller (rev f1)
00:10.0 PCI bridge: nVidia Corporation MCP51 PCI Bridge (rev a2)
00:10.1 Audio device: nVidia Corporation MCP51 High Definition Audio (rev a2)
00:14.0 Bridge: nVidia Corporation MCP51 Ethernet Controller (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 02)
05:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller
05:09.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
05:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 01)
05:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
05:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)

---

### Post by cragger on 2008-01-20
o, and if this helps, heres the info on my laptop

# 1.8GHz AMD Turion™ 64 X2 Dual-Core Mobile Technology TL-56 (512KB+512KB L2 Cache)
# 1GB DDR2 SDRAM (expandable to 2GB)
# 160GB 5400RPM SATA Hard Drive
# LightScribe Super Multi 8X DVD±R/RW with Double Layer Support
# 14.1" WXGA High-Definition BrightView Widescreen (1280 x 800)
# NVIDIA GeForce Go 6150 (UMA) video graphics, up to 287MB Shared Video RAM
# 802.11b/g WLAN and Bluetooth
# Integrated 10/100BASE-T Ethernet LAN
# High speed 56k modem
# HP Pavilion WebCam with Integrated Microphone
# Ports: 5-in-1 integrated Digital Media Reader for Secure Digital cards, MultiMedia cards, Memory Stick, Memory Stick Pro, or xD Picture cards; 3 USB 2.0; 2 Headphone out, one with SPDIF Digital Audio and one Stereo; 1 microphone-in; 1 VGA (15-pin); 1 TV-Out (S-video); 1 RJ-11 (modem); 1 RJ-45 (LAN); 1 Expansion Port 3; 1 IEEE 1394 Firewire (4-pin); 1 Consumer IR

---

### Post by SunnyRabbiera on 2008-01-20
> **JoshuaRL said:**
> Technically, HP doesn't support Linux.  Which means that when you have a problem you can't just call HP and have them tell you how to fix it.  But, that's why there's the Ubuntu Forums.

right, though HP usually comes with stuff that works fairly well with linux in my experience... in hardware at least.

---

### Post by JoshuaRL on 2008-01-20
> **SunnyRabbiera said:**
> right, though HP usually comes with stuff that works fairly well with linux in my experience... in hardware at least.

Oh dude totally.  That's what I was trying to get at.  Most computers work really well with linux, especially Ubuntu.  So despite any misgivings the manufacturers' tech departments have, there isn't much to worry about.  I've got an old HP Omnibook that works great with Xubuntu.

---

### Post by cragger on 2008-01-20
wow in this forum i get very quick answers to other peoples questions within my thread, if you have other problems not relating the original problem dont bring it up in this thread start your own, am i right?

---

### Post by cragger on 2008-01-20
ive posted all of the information you requested near the middle of this page, hope you can make something out of it

---

### Post by JoshuaRL on 2008-01-20
Alright dude.  I agree in principle, and I understand your delima.  But let's not throw out the baby with the bathwater.  I see from what you posted that your video card is from Nvidia.  I really can't help there, but I think you should be okay.  As for wireless, I see it's a Broadcom chipset.  Again, not sure how to help so I just left that alone.  I really hope you get the help you need.

As for the other poster, I could help him and decided to ignore the fact that he hijacked the thread and do what I would hope someone would do for me.  I hope you understand man.

---

### Post by cragger on 2008-01-20
ya, no i get it,.. this is way too much hassle, vista is bad but, at this point in time i dont have the time to be able to get all this to work..   i guess *it just **doent** work *for me lol, thanks tho

---

### Post by SunnyRabbiera on 2008-01-20
eh well maybe another distro might be better suited for you.
In my experience Ubuntu gutsy can be a hassle to get cooking sometimes.
one i would try is mandriva (my current preferred distro)
it seems to fare better then gutsy in my experience.

---

### Post by cragger on 2008-01-20
well ya i was thinkin about trying others,

---

### Post by SunnyRabbiera on 2008-01-20
Mandriva is a good one to start.
Mepis is another one I like to use off and on.
there isnt much I would personally use at this pooint and time but those two I swear by if ubuntu is too fluky... mostly mepis though as I had issues with mandirva in the past but its more recent versions are great.

---

### Post by bwtranch on 2008-01-20
# 1.8GHz AMD Turion™ 64 X2 Dual-Core Mobile Technology TL-56 (512KB+512KB L2 Cache)
# 1GB DDR2 SDRAM (expandable to 2GB)
# 160GB 5400RPM SATA Hard Drive
# LightScribe Super Multi 8X DVD±R/RW with Double Layer Support
# 14.1" WXGA High-Definition BrightView Widescreen (1280 x 800)

# NVIDIA GeForce Go 6150 (UMA) video graphics, up to 287MB Shared Video RAM# NVIDIA GeForce Go 6150 (UMA) video graphics, up to 287MB Shared Video RAMN
# 802.11b/g WLAN and Bluetooth
# Integrated 10/100BASE-T Ethernet LAN
# High speed 56k modem
# HP Pavilion WebCam with Integrated Microphone
# Ports: 5-in-1 integrated Digital Media Reader for Secure Digital cards, MultiMedia cards, Memory Stick, Memory Stick Pro, or xD Picture cards; 3 USB 2.0; 2 Headphone out, one with SPDIF Digital Audio and one Stereo; 1 microphone-in; 1 VGA (15-pin); 1 TV-Out (S-video); 1 RJ-11 (modem); 1 RJ-45 (LAN); 1 Expansion Port 3; 1 IEEE 1394 Firewire (4-pin); 1 Consumer IR
__________________
Thanks Reply With Quote Multi-Quote This Message Quick reply to this message
cragger
View Public Profile
Send a private message to cragger
Find all posts by cragger
Add cragger to Your Buddy List

Hi,

The first thing I would try is commenting out the line:
NVIDIA, that is removing the #
My four year-old is playing with the computer and I think she already did it!

---

### Post by ubuntu-freak on 2008-01-20
I think your problems can be resovled. Did you enable the restricted drivers manager? Is that when it says the software source isn't available?
 
What I used to do as a newbie was cut and paste the error messages into google and search. You could add 'Ubuntu' to the search too.
 
There's always someone else who had your problem.
 
Hope you get everything sorted.
 
Nathan

---

### Post by bwtranch on 2008-01-20
No, she didn't, but she tried. Just take that # out of there and save. It should work then.

---

### Post by Rabindranath on 2008-01-20
I always use 'envy' for installing drivers for my nvidia 8500 GT and it is very easy.
Download envy here 
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
Install it and click "install nvidia driver" and it will download and install the nvidia driver from the nvidia website. It will also configure your x server. I find the driver from nvidia to be better than the open source one. (atleast for me:))

---

### Post by thelatinist on 2008-01-20
> **cragger said:**
> wow in this forum i get very quick answers to other peoples questions within my thread, if you have other problems not relating the original problem dont bring it up in this thread start your own, am i right?

Well, you have an NVidia graphics card.  This is good, as it should be fairly easy to get it going.  Use the restricted drivers manager to enable the driver for your card.  If you have questions about how to do that, please search the forums.  There are lots of posts about this same issue.

Your wireless card is more problematical.  Broadcom has proprietary drivers only for Windows and has refused to release the specs on their chips so that others can write drivers for them.  Many people are able to get them working by using the Windows driver with a special helper program called NDIS wrapper which allows Linux to use them.  I've never tried this, so I would again suggest you do a search for your chipset on the forums.

If you still can't find the information you need, post a new thread for each problem with a title reflecting the specific problem ("nVidia Geforce 6150" or "Broadcom BCM94311MCG" or "Cannot enable restricted drivers" or whatever).  You are much more likely to get the help you need that way.

---

### Post by cragger on 2008-01-20
ok thanks, will do, i was trying to get the NDIS wrapper working but i really had no clue how to get the driver for it... ive been recently trying many other live cds (fedora, PClinusOX, Mandriva, Sabayon) i really do want to get linux system to work well.

---

### Post by shak541 on 2008-03-19
mitar if you are still watching this thread please compare your laptop with mine... I have a Dv6622ca with ubuntu 7.10 working without any problems at all.... everything works flawlessly and better in ubuntu. :D

if our laptops are very similar or the same then I could give you links to the guides i found to get my laptop fully working :D

---


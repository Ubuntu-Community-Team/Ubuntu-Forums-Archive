---
title: "Use ONLY nVidia discrete graphics on Optimus laptop N56VZ Ubuntu 13.04"
date: 2013-09-14
forum: Asus Ubuntu Support (CLOSED)
---

### Post by bmass on 2013-09-14
I used to have an ASUS G74Sx RoG laptop with an nVidia GeForce GTX 560M 3GB on Ubuntu 13.04 on which I used the nVidia proprietary drivers (310 I think) from my Additional Drivers section of my software sources. Everything worked great.

I recently purchased a new N56VZ which I was led to believe had a GeForce GT 650M 2GB, but I had no idea about the nVidia Optimus technology or that it was actively using both integrated and dedicated graphics. I assumed it was like every other computer I've used before with a dedicated graphics card. What's worse is neither the retailer nor ASUS has any indication on their websites that this laptop has anything but the discrete graphics card.

So obviously I'm having issues with Optimus. I feel jipped. And I'm trying to figure out if there is any reasonable graphics setup I can have with this laptop before contacting the retailer for a refund (which I'm hoping they will grant me on the grounds that the laptop was not advertised as having Optimus or anything other than the discrete graphics card). Below I will indicate my needs, what I've tried, what my understanding is from my past two weeks of research, and why I don't believe Bumblebee provides a solution for my situation:

I don't run any games, but I do run some graphically intense software like video editors; mainly I use the HDMI output to watch VLC on an extended monitor (TV) while working in the main desktop on the laptop screen (HDMI out to TV and then optical from TV to sound system). I also like to put a lot into having the computer run very flashy and graphics intensive in the desktop. This why I opted for a somewhat high end graphics card even though I don't do any gaming. This is also why, to my understanding, Bumblebee does not provide a suitable solution by allowing me to run specific applications with the discrete graphics card as I would want the whole system, at least especially the DE, window manager, and every other app I run to use the discrete graphics card.

I've contacted ASUS and they told me that the HDMI out was wired into the integrated chip and confirmed that there was no way to use the BIOS to disable the integrated graphics and that if I did disable integrated graphics that the HDMI output would not work. I've also seen a workaround on webupd8 to get HDMI output working with Bumblebee by running another desktop environment out of the HDMI using a piece of software called Primus (i think) but I've also read that people were mostly unsuccessful in getting sound through the HDMI. If I can't find any configuration to essentially use the nVidia discrete graphics 100% of the time, I will dig further into this workaround and see if there is some way I can get a good feasible working setup with HDMI output and sound. This is because I've considered some of the advantages of having the HDMI output in a second DE (e.g., workspaces on the laptop but not on the TV).

So to clarify, there is no way to use Bumblebee to run the all of Ubuntu with the discrete graphics (and working HDMI out) as far as I know (which is what I really want to do), and there is no way to get Bumblebee working with HDMI video and audio output. If there is a way to get either of these two things to work on Bumblebee please point me to a guide or where people have figured it out and I will give it a try.

Obviously installing any standard nVidia drivers that are supported for my GeForce GT 650M breaks Unity. Unity can be restarted through compiz and resolving conflicts with gnome but it doesn't exactly run smooth and clean like it should. I've read that people who can select which GPU to use in their BIOS are able to successfully latest nVidia proprietary drivers without issue by turning off integrated graphics and using only the discrete graphics card. As far as I understand this is not an option for me as confirmed by ASUS (and I've gathered this similarly rules out using vga switcheroo).

=======================
CONCLUSIONS
=======================
=======================

I have absolutely no interest in power savings or using the integrated graphics chip. I didn't know it had to be active in the laptop when I purchased and wish I didn't have it and had only the GeForce GT 650M advertised to come with the laptop. I can see why some people would want it but I feel like I've essentially wasted money on the cost of the graphics card (but I've had lengthy e-mail correspondence with ASUS about this and how it suggests they are trying to force people to use windows). Any way I can figure out to run all of Ubuntu using only the GeForce graphics card 100% of the time is all I'm looking for (to use the graphics card advertised with the computer).


From what I've researched:

1. Bumblebee is not option because no HDMI or ability to run all of Ubuntu with discrete graphics

2. Normal proprietary drivers conflict with the integrated graphics chip

3. Latest stable nVidia Optimus drivers for linux are version 319.49 and are certified. I still need to try these. I haven't found any online documentation regarding them, even how to install them. I've seen some documentation on the 319.12 beta drivers and the majority of people having issues or recommending to stick with Bumblebee. Since I have not found an installation guide for the latest stable nVidia drivers that are SUPPOSED to support Optimus in linux, I have not gotten around to trying it yet but that's essentially what I'm going to do right after this post and let you guys know how it works.

4. If anyone else has any other suggestions that I have not thought of or tried then please let me know. I got a great deal on this laptop (I got one for me and one for a friend) so I don't want to have to return the two of them. Thanks for reading.

---

### Post by Linuxisfast on 2013-09-14
Remove Ubuntu 13.04, download Ubuntu 12.04.3 LTS and install, you will have automatic Optimus support on your laptop out of the box with latest nvidia 319 drivers. [https://wiki.ubuntu.com/X/HybridGraphics](https://wiki.ubuntu.com/X/HybridGraphics) Works beautifully with my ASUS K55VM hybrid i7 laptop with HDMI out fully functional including audio.

---

### Post by bmass on 2013-09-15
Thanks for the reply. I was thinking of rolling back to 12.04 to see if I got out of the box support. So if I install 12.04 I can just select the optimus drivers through Software Sources > Additional Drivers?

I will definitely give this a try and confirm that it works for me.

I still want to ask, since when I was buying this laptop I was under the impression it only had one active GPU, is there a way to just use the discrete card 100% of the time? I'm not really interested in the battery savings, just looking for high graphic performance from the desktop, video players and video editors. When I spoke to ASUS they said that if I was using Windows they would tell me how to use the discrete card 100% of the time but since I was using Linux they told me to shove it up my a$$ (I indicated to them that if that was their official stance on Linux that I would never purchase or recommend ASUS products again), I was essentially wondering if I could do the same thing in Ubuntu? ASUS implied that this was a setting that could be changed in the nVidia configuration so I will take a look after installing 12.04 but maybe you can indicate to me whether this is possible?

The reason I was asking is because I was getting very poor performance through my external display (cursor trailing and so on) through the integrated card. I imagine it will be better with the Optimus drivers in 12.04 but like I said, I was never interested in power savings and just want optimal performance. Since you've been using the drivers maybe you could let me know if it's possible to use the discrete card 100% of the time or if switching between the two provides similar performance quality? I'm really not liking the idea behind this Optimus technology and am considering returning my laptops for one with a single GPU. It seems a lot more beneficial to gamers and more like a nuisance to non-gamers. Or maybe I've just got the wrong impression from all the trouble I've had to go through trying to get it working? Thanks, any opinions are welcome and appreciated. I'll admit this last week has left a pretty bad taste in my mouth regarding ASUS, nVidia and dual-GPU technology so I could have a pretty strong negative bias that I'd be open to have corrected if it is indeed wrong.

---

### Post by Linuxisfast on 2013-09-15
> **bmass said:**
> Thanks for the reply. I was thinking of rolling back to 12.04 to see if I got out of the box support. So if I install 12.04 I can just select the optimus drivers through Software Sources > Additional Drivers?

I will definitely give this a try and confirm that it works for me.

I still want to ask, since when I was buying this laptop I was under the impression it only had one active GPU, is there a way to just use the discrete card 100% of the time? I'm not really interested in the battery savings, just looking for high graphic performance from the desktop, video players and video editors. When I spoke to ASUS they said that if I was using Windows they would tell me how to use the discrete card 100% of the time but since I was using Linux they told me to shove it up my a$$ (I indicated to them that if that was their official stance on Linux that I would never purchase or recommend ASUS products again), I was essentially wondering if I could do the same thing in Ubuntu? ASUS implied that this was a setting that could be changed in the nVidia configuration so I will take a look after installing 12.04 but maybe you can indicate to me whether this is possible?

The reason I was asking is because I was getting very poor performance through my external display (cursor trailing and so on) through the integrated card. I imagine it will be better with the Optimus drivers in 12.04 but like I said, I was never interested in power savings and just want optimal performance. Since you've been using the drivers maybe you could let me know if it's possible to use the discrete card 100% of the time or if switching between the two provides similar performance quality? I'm really not liking the idea behind this Optimus technology and am considering returning my laptops for one with a single GPU. It seems a lot more beneficial to gamers and more like a nuisance to non-gamers. Or maybe I've just got the wrong impression from all the trouble I've had to go through trying to get it working? Thanks, any opinions are welcome and appreciated. I'll admit this last week has left a pretty bad taste in my mouth regarding ASUS, nVidia and dual-GPU technology so I could have a pretty strong negative bias that I'd be open to have corrected if it is indeed wrong.

You just have to download latest 12.04.3 and install, select third party tab during install and nvidia is automatically installed when you reboot. No need to do anything, its installed with all the requisite  components needed including xrandR, xserver and nvidia-prime. The optimus driver uses nvidia card piped through the Intel graphic so HDMI works and there is power saving via nvidia blob. What you faced with ASUS support you will face with any other company when you mention the LINUX word but its all changing as ASUS is now selling OEM Ubuntu laptops in China, India and elsewhere. As for dual GPU support, it has nothing to do with ASUS, its all to do with Nvidia and thats why the middle finger outrage of Torvalds at Nvidia. Thankfully people like David Airlie of Red Hat and his hard work with nvidia prime, now Optimus support is possible.

I also abhorred discrete GPU laptops due to their heat generation and battery issue and always used the onboard Intel GPU but lately none of the manufacturers selling i7 make one without discrete card. For marketing reason, they always tag a discrete card along. However when Optimus was out for Ubuntu I tried and was impressed with the performance of the discrete card during accelerated web browsing. Do bear in mind that Chrome doesn't enable the hardware features by default, they need to be enabled via flags. I don't do any gaming but I do need CUDA which I use on my desktop, now I can use it on my laptop as well.

---

### Post by bmass on 2013-09-19
> **Linuxisfast said:**
> You just have to download latest 12.04.3 and install, select third party tab during install and nvidia is automatically installed when you reboot. No need to do anything, its installed with all the requisite  components needed including xrandR, xserver and nvidia-prime. The optimus driver uses nvidia card piped through the Intel graphic so HDMI works and there is power saving via nvidia blob. What you faced with ASUS support you will face with any other company when you mention the LINUX word but its all changing as ASUS is now selling OEM Ubuntu laptops in China, India and elsewhere. As for dual GPU support, it has nothing to do with ASUS, its all to do with Nvidia and thats why the middle finger outrage of Torvalds at Nvidia. Thankfully people like David Airlie of Red Hat and his hard work with nvidia prime, now Optimus support is possible.

I also abhorred discrete GPU laptops due to their heat generation and battery issue and always used the onboard Intel GPU but lately none of the manufacturers selling i7 make one without discrete card. For marketing reason, they always tag a discrete card along. However when Optimus was out for Ubuntu I tried and was impressed with the performance of the discrete card during accelerated web browsing. Do bear in mind that Chrome doesn't enable the hardware features by default, they need to be enabled via flags. I don't do any gaming but I do need CUDA which I use on my desktop, now I can use it on my laptop as well.

So I installed Ubuntu 12.04.3 and selected to install 3rd party software and updates. I ran sudo apt-get update && sudo apt-get upgrade and plugged in my HDMI... nothing. At least in 13.04 a vanilla install detected the TV and was able to output video to HDMI (but no audio). The nVidia 319 were installed and working by default like you said though. I checked in additional drivers and switched from the post-release drivers to the recommended drivers and restarted. Still no HDMI output.

Please let me know if you have any ideas why HDMI might not be working. Thanks.

---

### Post by Linuxisfast on 2013-09-20
> **bmass said:**
> So I installed Ubuntu 12.04.3 and selected to install 3rd party software and updates. I ran sudo apt-get update && sudo apt-get upgrade and plugged in my HDMI... nothing. At least in 13.04 a vanilla install detected the TV and was able to output video to HDMI (but no audio). The nVidia 319 were installed and working by default like you said though. I checked in additional drivers and switched from the post-release drivers to the recommended drivers and restarted. Still no HDMI output.

Please let me know if you have any ideas why HDMI might not be working. Thanks.


Was nvidia prime package installed as well, HDMI works fine here on my laptop and I use post release. Did you try the detect displays button? Also on sound settings did you have HDMI sound selected?

---

### Post by ronmaster on 2013-09-21
I have been following this thread since the beginning. I too have N56VZ and 650m  card and has the same problem as bmass. I downgraded from 13.04 to 12.04.03 and installed nvidia-prime, activated nvidia-updates, etc. Still looking for a working solution

---

### Post by Linuxisfast on 2013-09-21
> **ronmaster said:**
> I have been following this thread since the beginning. I too have N56VZ and 650m  card and has the same problem as bmass. I downgraded from 13.04 to 12.04.03 and installed nvidia-prime, activated nvidia-updates, etc. Still looking for a working solution


No HDMI out for you either? Nvidia Optimus doesn't need to be installed as its automatically installed in Optimus laptops during Ubuntu installation.

---

### Post by Linuxisfast on 2013-09-21
> **ronmaster said:**
> I have been following this thread since the beginning. I too have N56VZ and 650m  card and has the same problem as bmass. I downgraded from 13.04 to 12.04.03 and installed nvidia-prime, activated nvidia-updates, etc. Still looking for a working solution


No HDMI out for you either? Nvidia Optimus doesn't need to be installed as its automatically installed in Optimus laptops during Ubuntu installation.

---

### Post by ronmaster on 2013-09-21
maybe it is... maybe it is contained in the nvidia driver:
> 
lspci -k | grep -iA2 vga
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
    Subsystem: ASUSTeK Computer Inc. N56VZ
    Kernel driver in use: i915
--
01:00.0 VGA compatible controller: NVIDIA Corporation GK107M [GeForce GT 650M] (rev a1)
    Subsystem: ASUSTeK Computer Inc. N56VZ
    Kernel driver in use: nvidia
ron@N56VZ:~$ dpkg --get-selections | grep -i nvidia
nvidia-319                    install
nvidia-319-updates                install
nvidia-common                    install
nvidia-prime                    install
nvidia-settings-319                install
nvidia-settings-319-updates            install
ron@N56VZ:~$ lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.3 LTS
Release:    12.04
Codename:    precise




---

### Post by ronmaster on 2013-09-21
could it be because the intel card is incative in the xorg.conf?
>  more /etc/X11/xorg.conf
# Warning: This file is autogenerated by nvidia-prime. All changes to this file will be lost.

Section "ServerLayout"
    Identifier "layout"
    Screen 0 "nvidia"
    Inactive "intel"
EndSection

Section "Device"
    Identifier "nvidia"
    Driver "nvidia"
    BusID "1:0:0"
EndSection

Section "Screen"
    Identifier "nvidia"
    Device "nvidia"
    # Uncomment this line if your computer has no display devices connected to
    # the NVIDIA GPU.  Leave it commented if you have display devices
    # connected to the NVIDIA GPU that you would like to use.
    Option "UseDisplayDevice" "none"
EndSection

Section "Device"
    Identifier "intel"
    Driver "modesetting"
EndSection

Section "Screen"
    Identifier "intel"
    Device "intel"
EndSection



---

### Post by ronmaster on 2013-09-21
The NVIDIA driver version from the nvidia-updates package is 319.32

---

### Post by bmass on 2013-09-22
> **Linuxisfast said:**
> Was nvidia prime package installed as well, HDMI works fine here on my laptop and I use post release. Did you try the detect displays button? Also on sound settings did you have HDMI sound selected?

nvidia-prime is already the latest version. The detect displays button did not do anything and there was no option for HDMI sound in sound settings. Only for speakers and S/PDIF output. 

Thanks for the help so far. Still have no idea what to do about his issue.

@ronmaster: have you managed to get HDMI output working in any setup with sound on your N56VZ?

---

### Post by Linuxisfast on 2013-09-23
> **bmass said:**
> nvidia-prime is already the latest version. The detect displays button did not do anything and there was no option for HDMI sound in sound settings. Only for speakers and S/PDIF output. 

Thanks for the help so far. Still have no idea what to do about his issue.

@ronmaster: have you managed to get HDMI output working in any setup with sound on your N56VZ?

Did you try the detect displays via nvidia-settings?

---

### Post by ronmaster on 2013-09-25
I had the same problem that @bmass. I installed the 319.49 nvidia driver, the very last one. Although I can load the nvidia module and use it, I cannot blast a second display through HDMI (saying in the /var/log/Xor.0.log that the 3D vision feature is not supported when I connect the cable) nor could I see the hdmi option in the output section of sound control. Just to test, I have installed Fedora 19. the install went well and the ivybridge intel driver is running the card. The hdmi display looks smoother on the LCD tv than the 12.04.03 LTS vanilla install. but sill no sound. I could not install yet the nvidia proprietary driver. It just failed while compiling it. I am thinking of installing the kmod-nvdia rpm but I suspect the embeded nvidia driver is not the lastest one. 

Since Linuxisfast could successfully make the hdmi work, with the sound, on another laptop model, I am wondering if there could be a hardware difference between the hdmi connection and the nvidia card, wich is the same nvidia model. This difference is making the n56Vz  to be a pain in the ass with the external display. anyway. I will still make tests with it and I will go with the linux distribution with wich I will have success. mainly fedora or ubuntu. (maybe ubuntu 13.10 will have a better luck)

---

### Post by bmass on 2013-09-29
Yeah I contacted ASUS about the fact that their website doesn't mention this model laptop as having 2 active GPUs or say anything at all about the intel GPU or the nVidia Optimus technology. They didn't seem to care that it would be nearly impossible to tell that laptop had two GPUs active without having it physically in front of you to run some sort of hardware analysis.

I also complained to ASUS about how they did a crappy job building the laptop but hooking the discrete card into the mobo through the integrated chip insteaed of plugging both in separately (the way they build the laptop makes it impossible to use ONLY the discrete card.... which is the card advertised as being in the laptop). 

It should be noted that for those laptops built with an option to select to use only the discrete GPU in the BIOS, the standard proprietary drivers can be downloaded and installed from nVidia's website or by any of the normal methods. The activity of the intel GPU interferes with these drivers... that's balderdash but as soon as I mentioned Linux to ASUS they popped me the middle finger.

I was never able to get this working. I contacted the retailer I purchased these laptops and my S56CM from and demanded a refund because the laptops were not advertised with 2 GPUs (I also had a lot of other issues with the retailer including them trying to send me a cheaper model of the N56VZ without mentioning anything or crediting my account; then they shiested me even further when I contacted them about it which is why I am returning all of my laptops).


Thank you for your help. I will doing a little more research for my laptop purchase to find one that only uses one GPU and no intel graphics.I

Incidently the retailer is NMicroVIP, I intend to report them on ripoffreport, redflagdeals, and a bunch of other sites as soon as I get a new working laptop.

---

### Post by Linuxisfast on 2013-09-30
All laptops sold today are Muxless so that means only way to switch them is via Bumblebee in Linux or use Windows where Nvidia driver does it automatically for you.

---

### Post by ayjayz-stuff on 2013-10-03
OK, So I have an Asus N56VZ as well with the GT-650M card running Linux Mint 15 (Basically Ubuntu 13.04).. Same problem, as everyone else whereby xrandr doesn't detect the HDMI port :-( If I export the display (export DISPLAY=:8.0) and I run xrandr it only sees the HDMI port.. I still haven't got my head around this as yet but I managed to get my display to use my HDMI port to my TV via scripts. I was using the nvidia proprietry driver (ver 325.15) and the latest version of bumblebee.. (note when I run  optirun Nvidia-settings -c :8 it sees the HDMI output (TV) but no other monitor such as my LVDS-0) 

e.g. 

#/bin/bash


#Set the HDMI Display


export DISPLAY=:8.0 LD_LIBRARY_PATH=/usr/lib/nvidia-325:$LD_LIBRARY_PATH LD_PRELOAD="libpthread.so.0 libGL.so.1" __GL_THREADED_OPTIMIZATIONS=1


optirun nvidia-settings -c :8 --assign CurrentMetaMode="DFP-0: 1920x1080 {ViewPortIn=1920x1080, ViewPortOut=1820x1020+50+30}" &


sleep 1


optirun mate-wm &


sleep 2


optirun steam



 It is an ugly hack but it really works well for Steam games.. Now the tricky bit is I just installed nvidia-prime and randr 1.4 and now I have no need to run the optimus script which great and if you can believe it I am getting approx. 1400fps when testing glxspheres (32bit I think) at a rez of 1920x1080 on the LVDS laptop screen.. Only prob is now I cannot see my HDMI port any longer.. As this has been a work in progress I may have corrupted some things so I am going to attempt a re-install from scratch of everything with how i think it should be installed and in what order. I'm slowly piecing this together as currently there are so many changes with the new version of randr coming out, the latest nvidia drivers etc.. 

Also I installed from the same install disk a vanilla copy of Ubuntu (I did this with mint as well) 4 times to see what would happen.. No matter what I did I would end up with a slightly different config each time, It depended on what version in the repository was available at the time of install.. So good luck and hopefully together we can get this solved..

---

### Post by bcschmerker on 2013-10-03
Thanks for a heads up on both a means to use nVIDIA® GPU's on an Intel® Core™ i7™ rig and complications to watch out for.  My own current plans for a Haswell build include an ATi®-based video card due to better open-source support; but the Bumblebee Project™ gives me an option in the event that I do need a video card based on an nVIDIA® GK-series GPU (192-, 256-, and 384-bit GeForce® GTX™ 4xx, 5xx, or 6xx models) for specific functionality such as TwinView™ for presentations.  I plan to use the in-APU Intel® Multimedia Accelerator™ primarily as a text display for back-end monitoring, to stand in for a dedicated serial terminal.

---

### Post by Vormeph on 2013-10-03
Why not use Bumblebee? It has worked for me and it provides power-saving alongside performance. 

From Ubuntu 13.10 and onwards, Bumblebee will be in official repositories alongside the nvidia-319 drivers. Have fun!

---

### Post by Linuxisfast on 2013-10-23
One reason is framerate, its far higher with nvidia-prime than Bumblebee.

---

### Post by ajd-nanthakumar on 2013-11-02
I have asus k55vm with nvidia gt 630m. I have installed bumblebee+opimus in ubuntu 12.04.3. But it returned all error messages whenever I started discrete graphics mode and did not show the nvidia properties box. Later I found in a forum that ubuntu 13.10 onwards optimus support is good. I installed 13.10 and nvidia properties box started displaying when i gave  the follwing code in terminal:
         *  optirun -b none nvidia-settings -c :8*
Also bumblebee gave me options to use dicrete card for individual applications like gimp, chrome, etc. Better install 13.10

---


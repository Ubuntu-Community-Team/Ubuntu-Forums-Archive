---
title: "Testers wanted for UbuntuMATE 14.04 for PPC"
date: 2015-01-07
forum: Apple Hardware Users
---

### Post by este.el.paz on 2015-01-07
Folks:

A flavor of Ubuntu with MATE DE is available spun for PPC . . . the more PPC people that can test it out, the better.

[http://1drv.ms/1wgsdUk](http://1drv.ms/1wgsdUk)   Is the link to the Onedrive site, in my newly installed MATE system on my iBook G4 the link would not load, complaining about my browser, etc.  Otherwise, MATE is a great DE, might be pushing the envelope with my raging 540MB RAM, but it's worth it to see the GNOME Floating Feet screensaver.  I added the radeon mods suggested on the knownissues page to the yaboot.config file, and configured an xorg.conf file--both of which I did in the Lu 14.04 install.  Added the "b43" firmware for wifi.  Had some issues with freezing during the install, possibly because I have dual boot OSX, seems to be OK now--one remaining problem left over from base 14.04 is the issue(s) with failing to revive from suspend, and here in MATE, no "hibernate" . . . and some glitches around logging out and/or suspend, requiring a shut down.  Minor details.  And, sure, no sound . . . not so much of a concern for me as the "revive" or "drop into suspend" . . . .  Oh, uh, the fan seems to be blowing for even minor "thoughts" . . . or any "thought-gathering" process that the processor tries to gather "steam" for . . . .  : - )

Enjoy,

e.e.p.

---

### Post by themacmeister on 2015-01-09
Downloading to test on G5 Power Mac DP 2.5

6GB RAM

Airport

Bluetooth etc.

Will report back.

---

### Post by este.el.paz on 2015-01-10
Cool.  MATE is a good DE.

> EDIT: Release notes are here [http://1drv.ms/13ElEQW](http://1drv.ms/13ElEQW)&#65279;

md5sum 2bb57b2bbf87b668a94c38dd0393b263  ubuntu-mate-14.04.1-dev.34508-desktop-powerpc.iso

sha1sum 9fe995a2832e2c0bcce5604b08095fb7217882ac  ubuntu-mate-14.04.1-dev.34508-desktop-powerpc.iso

sha256sum b53d2836c00a2f9180353e908f09ee9eb4b17138dcc72bf692c6bd68b2756032  ubuntu-mate-14.04.1-dev.34508-desktop-powerpc.iso&#65279;

---

### Post by Dukenukemx on 2015-01-11
Got my old PowerBook G4 Platinum 15" to work with 14.04 except for the Radeon 9600 graphics.  Stuck on software rendering.  Went into the /etc/yaboot.conf and added "radeon.modeset=0".  Then I created xorg.conf and threw this in there.  After reboot, glxinfo still shows software rendering.  Got a solution for this?  

```

Section "Device"
Identifier "Radeon 9600"
Driver "radeon"
## BusID "PCI:0:16:0"
Option "DynamicClocks" "true"
Option "AGPMode" "4"
Option "AGPFastWrite" "true"
Option "UseFBDev" "false"
Option "DRI" "true"
Option "GARTSize" "64"
Option "AddARGBGLXVisuals" "true"
Option "XAANoOffscreenPixmaps"
Option "DisableGLXRootClipping" "true"
Option "AllowGLXWithComposite" "true"
Option "EnablePageFlip" "true"
EndSection

Section "Extensions"
Option "Composite" "Enable"
EndSection
```

---

### Post by Dukenukemx on 2015-01-11
I remember now.  I need these files.  Anybody know where I can get them?  

libgl1-mesa-dri_7.11-0ubuntu3_powerpc.deb
libgl1-mesa-glx_7.11-0ubuntu3_powerpc.deb
libglapi-mesa_7.11-0ubuntu3_powerpc.deb
libglu1-mesa_7.11-0ubuntu3_powerpc.deb

**EDIT**
Found them [here.](https://launchpad.net/ubuntu/+source/mesa/7.11-0ubuntu3)  No luck getting 3D acceleration to work though.

---

### Post by rican-linux on 2015-01-12
> **Dukenukemx said:**
> I remember now.  I need these files.  Anybody know where I can get them?  

libgl1-mesa-dri_7.11-0ubuntu3_powerpc.deb
libgl1-mesa-glx_7.11-0ubuntu3_powerpc.deb
libglapi-mesa_7.11-0ubuntu3_powerpc.deb
libglu1-mesa_7.11-0ubuntu3_powerpc.deb

**EDIT**
Found them [here.](https://launchpad.net/ubuntu/+source/mesa/7.11-0ubuntu3)  No luck getting 3D acceleration to work though.

Look at the Ubuntu 12.04 known issues page [here]("https://wiki.ubuntu.com/PowerPCKnownIssues#A12.04_Precise_Pangolin").

However I am not sure if this will work if you are on 14.04

---

### Post by Dukenukemx on 2015-01-12
> **rican-linux said:**
> Look at the Ubuntu 12.04 known issues page [here]("https://wiki.ubuntu.com/PowerPCKnownIssues#A12.04_Precise_Pangolin").

However I am not sure if this will work if you are on 14.04

I got the files installed but I get this when running glxinfo.
```

name of display 0.0
Error: couldn't find RGB GLX  visual or fbconfig
Error: couldn't find RGB GLX  visual or fbconfig

```

Then I tried glxgears and got this. 
```

Error: couldn't get an RGB, Double-buffered visual

```
I locked the 7.11 files and ran Ubuntu update.  It must have replaced them cause now I don't get those errors but instead back to software rendering.  So far 14.04 has a lot of things working for it.  I have sound, wifi, bluetooth, and proper power management.  But no 3D acceleration, which makes UI's and basic games run like ****.  So I probably have to go down to 12.04, cause I know that works.  Why doesn't 3D works for 14.04 anyway?  Is it that graphics aren't compiled for PowerPC?  Last I Google'd Radeon 9600 works on x86 with 14.04.  My old Clevo laptop with a Radeon 7500 has working 3D acceleration.

---

### Post by rican-linux on 2015-01-12
read [here]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1377878"). I think you will need to downgrade to 12.04 for USM to work.

---

### Post by xeno74 on 2015-01-12
It works. :-)

[[img]http://www.supertuxkart-amiga.de/amiga/Kernel_3.19_Ubuntu_MATE_AMIGA_one_X1000-thumbnail.jpg[/img]](http://www.supertuxkart-amiga.de/amiga/Kernel_3.19_Ubuntu_MATE_AMIGA_one_X1000.jpg)

---

### Post by Dukenukemx on 2015-01-12
> **xeno74 said:**
> It works. :-)

[[img]http://www.supertuxkart-amiga.de/amiga/Kernel_3.19_Ubuntu_MATE_AMIGA_one_X1000-thumbnail.jpg[/img]](http://www.supertuxkart-amiga.de/amiga/Kernel_3.19_Ubuntu_MATE_AMIGA_one_X1000.jpg)

How?  You must tell me!  Seriously 3.19-rc4_A-EON_AMIGA_one_X1000_Nemo?  I'm only using 3.17 on my i3 Laptop.  :P  I must know xeno74, por favor.

---

### Post by xeno74 on 2015-01-13
Hola Dukenukemx,

How??? Simple it works more not. Ubuntu Mate 14.10 works on an [AMIGA one X1000](http://www.a-eon.com/?page=x1000).

Adiós

Christian

---

### Post by Dukenukemx on 2015-01-13
Sure is a lot of things about AMIGA computers.  They still make PowerPC computers?  No way to get graphics working on the PowerBook G4?  Looks like I'll be installing 12.04 tomorrow.  :(

---

### Post by Nate_Olander on 2015-01-15
I've got this running decently on a mid-2005 iBook G4. 1.33GHz processor, 512MB RAM, 60GB HDD. Yay for old hardware given another chance!

I had actually been running Lubuntu 12.04 & Lubuntu 14.04 prior to installing MATE 14.04. Lubuntu 12.04 worked great, and then I upgraded to 14.04 and everything went to heck. I kinda just gave up on it, then read about this and gave it a go.

Since the iBook I had doesn't support USB booting by default I had to go into OpenFirmware (*gasp* - O.O - *the belly of the beast!*) and run boot ud:,\\:tbxi and I was able to boot from USB. Funny thing, this only worked when I plugged the USB stick into the USB port closest to the screen.

I booted the LiveUSB via yaboot (adding the video=radeonfb:1024-768-32 flag) and it installed just fine. I had to download the b43 drivers via ethernet, but that's a known issue with Ubuntu on PPC mac computers with the airport chip they have. After installing those drivers, WiFi worked just fine (had to reboot first) and the computer seemed just fine.

I *di**d *notice th[SIZE=2]a[/SIZE]t the[SIZE=2] Mesa issuing false colors in games cropped up in Pinta (as noted [here]("https://wiki.ubuntu.com/PowerPCKnownIssues#A14.04_Trusty_Tahr")) - so I've been working on getting the 10.4 version of Mesa installed to correct that.

One final thing I noticed was that if I shut the laptop lid/screen thing (thus putting it to sleep) it would start up again - but without working WiFi and I don't have the ability to use sudo anymore until I full reboot.
[/SIZE]

---

### Post by Dukenukemx on 2015-01-16
I put Kubuntu 12.04 on the PowerBook G4 and despite my efforts I couldn't get 3D acceleration.  Same "Error: couldn't get an RGB, Double-buffered visual".  I gave up, I will put back Mac OS X 10.4.  I can make this work.  

NOPE!

Firstly the wifi barely works.  Worked perfectly in Ubuntu but in Mac OS X is works on and off.  I remember those days.  Then the only working barely considered up to date web browser was TenFourFox.  It was able to play YouTube videos at a bad frame rate.  Certainly no better than 14.04.  So yea, 14.04 Mate is the way to go.  BTW KDE runs like snot on PPC.  

I'm going to give 14.04 another try, cause I think I can get 3D working.  I think what I need to do is place this in the /etc/yaboot.conf along with those files.  

```

Linux radeon.modeset=1 video=offb:off video=radeonfb:off video=1024x768-32 radeon.agpmode=-1
```

---

### Post by luigiburdo on 2015-01-16
Im already testing it ;)
Quad G5 8gb 7800gtx 512mb and Radeon HD 6570 2gb
... first build video exit on RadeonHD (glitched i was able to see the mate logo )for me it was a great news :-P
Second build (totally glitched graphic on Nvidia 7800gtx  and no video RadeonHD ) i had the same issue with Lubuntu 15.x

On MacMini G4 1.5ghz  1ghz ati 9200 64mb vram:
Perfect loading without any kernel options , Icons and menu gui perfect showed but ... images and windows contents totally glitched .
dmesg | grep radeon gave me a strange firmware error of radeonfb
i will check with kernel options and report
In any case the graphics look like accelerated because is really fast in windows mooving

---

### Post by Dukenukemx on 2015-01-16
Well I figured the reason why non of my yaboot entries were working was cause I needed to run "sudo ybin -v".  Not very different from Grub.  Before it boots I see "drm radeon get_bios error unable to locate a bios rom".  Then when I try to run glxinfo or glxgears I get "libGL error: failed to load driver: r300".  Not sure what's going on.

---

### Post by rican-linux on 2015-01-16
Can you post the entire output of 'glxinfo |grep render'

---

### Post by Dukenukemx on 2015-01-17
Sure, here's what I get.

libGL error: failed to load driver: r300
libGL error: failed to load driver: swrast
Error: couldn't find RGB GLX visual or fbconfig
Error: couldn't find RGB GLX visual or fbconfig

---

### Post by rican-linux on 2015-01-17
If you are using radeon card you see [the wiki]("https://wiki.ubuntu.com/PowerPCFAQ#Radeon_cards"). Here is the key section:

"There are a lot of 'wonder' xorg.conf files knocking around the internet that claim to have the secret formula to fantastic 3d performance. I've only found two things that make a big difference. The first is to reduce the colour depth (for example put DefaultDepth 16 into the screen section), but I prefer a greater colour depth so I don't do this. The second is to turn on HyperZ. This isn't done in xorg.conf, but in a ".drirc" file in your home folder. Install Driconf from the software centre/synaptic so that you can turn it on using the applet. I have no idea what this actually does, only it makes the numbers go up in glxgears!"

---

### Post by luigiburdo on 2015-01-17
[COLOR=#000000][FONT=Roboto]guys i fixed probably on MacMini G4 1.5 ghz and 64mb radeon 9200... now everything is right color ... 
i will check the other things better and other kernels options
[/FONT][/COLOR][COLOR=#000000][FONT=Roboto]  live video=radeonfb: off video=offb: off radeon.agpmode=-1[/FONT][/COLOR]

---

### Post by luigiburdo on 2015-01-17
[SIZE=3][FONT=arial]Installation of Ubuntu Mate with the paramethers posted before goes perfect without problems.Everything was smooth and fast in windows moving Browsing with Firefox from LiveCD.
[/FONT][/SIZE][COLOR=#000000][FONT=Roboto][SIZE=3][FONT=arial]After installed everything the mini booted perfect from the Hd no video glitched and problems ... but ... everytime i open something the system freeze ... i can move only the mouse but cant move menu' or open something... totally frozen[/FONT][/SIZE]
[/FONT][/COLOR]

---

### Post by Nate_Olander on 2015-01-17
What yaboot parameters did you use exactly? Also, what device?

---

### Post by luigiburdo on 2015-01-18
Hi Nate
this is the yaboot params [COLOR=#000000][FONT=Roboto][SIZE=4]live video=radeonfb: off video=offb: off radeon.agpmode=-1 [/SIZE]

Note: the issue i posted before is present on Lubuntu 14.04ts too i just make a clean install of it and face the same as on Mate.
My Machine is MacMini G4 1.5 ghz 1gb ram Radeon 9200 64mb
 
Like i write before on Live CD booting everything is working perfect with that parameters ... in  Mate and Lubuntu
after installing everything on HD i face the issue
 
umm... i think there is a bug someware in lightdm or in lxde.
Why i writing this ? because after /etc/init.d/lightdm stop ... i do everything without problem in screen console.. startx and xinit dont make any crash.
After /etc/init.d/lightdm start ... bam freeze
 
Now im try to switch to kdm or gdm for  check if there will have the same problem

Edit: kdm freeze too ... Xorg issue?[/FONT][/COLOR]

---

### Post by abtabt on 2015-01-18
luigiburdo

 you can try driver fbdev in the xorg.conf 

and nodm if 14.04 have that

---

### Post by Dukenukemx on 2015-01-18
> **rican-linux said:**
> If you are using radeon card you see [the wiki]("https://wiki.ubuntu.com/PowerPCFAQ#Radeon_cards"). Here is the key section:

"There are a lot of 'wonder' xorg.conf files knocking around the internet that claim to have the secret formula to fantastic 3d performance. I've only found two things that make a big difference. The first is to reduce the colour depth (for example put DefaultDepth 16 into the screen section), but I prefer a greater colour depth so I don't do this. The second is to turn on HyperZ. This isn't done in xorg.conf, but in a ".drirc" file in your home folder. Install Driconf from the software centre/synaptic so that you can turn it on using the applet. I have no idea what this actually does, only it makes the numbers go up in glxgears!"

I followed the guide and did most of everything except compile my own driver.  Though after a minute or two the screen goes nuts and then nothing else happens.  Just the mouse works.  Gotta remove video=ofonly to get it not to freeze.  

I'm thinking there's no driver for the Radeon 9600 so I may need to build, [according to this guide.](http://www.x.org/wiki/radeonBuildHowTo/)  But when I get to the part where I need to "./autogen.sh --prefix=/opt/xorg" I get this error.  

```

configure: error: Package requirements (libdrm >= 2.4.58) were not met:  
Requested 'libdrm >= 2.4.58' but version of libdrm is 2.4.56

```

According to Synaptic Package Manager I'm using 2.4.56.  How do I upgrade that?

---

### Post by rican-linux on 2015-01-19
I have never compiled the radeon driver but that version of libdrm can be found [here]("https://launchpad.net/ubuntu/+source/libdrm"). Share your results if that works or not.

---

### Post by luigiburdo on 2015-01-19
Hi rican-linux
how i can compile something if Mate or Lubuntu 14.04 freeze before i can do the first step ? ;-)

I had been tested with Debian Wheezy and after compiled/upgraded the kernel to 3.10.65 i see somthing strange there.
Pratically the video from software resterized had been upgraded to Mesa/Gallium the radeon 9200 was perfect recongnized 
but after 10 seconds of using ... bam ... freeze there too... 
i m start thinking the freeze on Lubuntu and Mate are caused from something related the Firmware-nonfree or Kernel 
because the same freeze issue start on Debian Wheezy with upgrading only this two components.

Note the glxgears on Radeon 9200 gave me more than 600  fps in 5sec  on mini .... if compared with 300fps of nv6600 on  Quad G5 i think something is not going right...
can be possible the firmware soft overclock the Radeon 9200 and because of this Lubuntu and Mate freeze like the Debian with Last kernles ? ? ? ?


edit: i found something related radeon and kms ... will check it if will fix the issues on PPC machine too
[https://forums.opensuse.org/showthread.php/469668-Issues-with-old-ATi-card-and-radeon-driver-%28image-corruption-BUSType-AGPMode-et-al-not-used%29/page2?](https://forums.opensuse.org/showthread.php/469668-Issues-with-old-ATi-card-and-radeon-driver-%28image-corruption-BUSType-AGPMode-et-al-not-used%29/page2?)

edit2: and found something related PowerBooks too: 
[http://forums.debian.net/viewtopic.php?f=7&t=103723](http://forums.debian.net/viewtopic.php?f=7&t=103723)


EDIT3: DHO!!!!!!!

> [COLOR=#000000][FONT=Arial]The legacy radeon framebuffer (radeonfb) is nolonger built-in to the kernel, but is now compiled as a module - see [/FONT][/COLOR][bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1377878")[COLOR=#000000][FONT=Arial]. This means KMS is on and active from the go![/FONT][/COLOR][COLOR=#000000][FONT=Arial]Like previous versions, some systems will need the yaboot parameter radeon.agpmode=-1 to circumvent freezes (so far this is confirmed for Radeon 9200 chips in AGP based G4 iBook's). You might need to set that yaboot parameter again after an installation as that might not carry over from the booted ISO - see [/FONT][/COLOR][FAQ]("https://wiki.ubuntu.com/PowerPCFAQ#How_do_I_make_a_yaboot_parameter_permanent.3F")[COLOR=#000000][FONT=Arial] for how to do this.[/FONT][/COLOR]

---

### Post by rican-linux on 2015-01-19
In Wheezy I had downgrade my mesa drivers and set up UMS to get 3D acceleration. I followed the instructions [here]("http://ppcluddite.blogspot.com/2012/03/installing-debian-linux-on-ppc-part-iv.html#graphics"). In Jessie and in Lubuntu I used the following yaboot parameters to get a working desktop "video=radeonfb:off video=offb:off radeon.modeset=1 radeon.agpmode=-1"

---

### Post by rican-linux on 2015-01-19
In Wheezy I had downgrade my mesa drivers and UMS to get 3D acceleration. I followed the instructions [here]("http://ppcluddite.blogspot.com/2012/03/installing-debian-linux-on-ppc-part-iv.html#graphics"). In Jessie and in Lubuntu I used the following yaboot parameters to get a working desktop

 ```
"video=radeonfb:off video=offb:off radeon.modeset=1 radeon.agpmode=-1"
```

---

### Post by luigiburdo on 2015-01-20
i will check if after installation adding the radeon.modeset=1 i will not have the frozen issue on mini.
Wow i had been installed in 7 day 55 times linux there poor mini ;-)

---

### Post by rican-linux on 2015-01-20
I am sure the mini will survive! Apple hardware is resilient like that.

---

### Post by luigiburdo on 2015-01-20
rican i confirm  everything  is working here on Mini  with adding radeon.modeset=1 mesa 10.1.3 too :),
 now i found a small issue here look like the module of audio is not loaded and isnt blacklisted too ...


here is ... macmini g4 in 1920x1080 res with compositing and 3d ... no audio :P

[IMG]https://fbcdn-sphotos-e-a.akamaihd.net/hphotos-ak-xaf1/v/t1.0-9/10390098_10203445305034894_250214643903734218_n.jpg?oh=b0c7c35ba2e9a6892e3fdd5594e37d7d&oe=55641DDB&__gda__=1432558956_28690e0dabd876235a7789e025107afe[/IMG]

---

### Post by rican-linux on 2015-01-20
try this 'sudo modprobe snd-aoa-i2sbus' if that works add the module to /etc/modules. 

Give a brief walk through on how you got it 3D working?

---

### Post by luigiburdo on 2015-01-21
Hi rican ... will check leater the sound module thank you for your tips.
About Mesa 3d .. didnt need any configuration for make everything running for very beginning.
The only thing i did was  insert  from the installation of Mate the live with your kernel parameters and everything goes with 0 issues.
I just found a little instability with Xorg usually it crash (not heavy) but i think it come because the little vmem of mini and hi resolution ... in any way every time it crash i send the report to the developes 

Thank you 
Luigi

---

### Post by este.el.paz on 2015-01-21
> **luigiburdo said:**
> 
I just found a little instability with Xorg usually it crash (not heavy) but i think it come because the little vmem of mini and hi resolution ... in any way every time it crash i send the report to the developes 

Thank you 
Luigi

@L:

As I posted on G+, did you set up an xorg.conf file?  Following PowerPCFAQ instructions?

e.e.p.

---

### Post by luigiburdo on 2015-01-21
Hi  Este,
I dont have any xorg.conf in /etc/X11/  in any way i didnt setup nothing there , everything was made by Mate installation on Mini G4... I dont know if on PowerBook because the 
different video board was needed something related xorg.conf and there i think rican_linux can gave help more then me.
if you need i can generate one and copy here.

Sorry about g+ i will reply soon as possible there too.


Rican... the module work .. now i have audio too :) Thanks!!!

---

### Post by rican-linux on 2015-01-21
To get any working 3D on Ubuntu I needed a xorg.conf but I still had issues the same when I ran Debian Jessie. In Wheezy I just down graded to use UMS.

---

### Post by este.el.paz on 2015-01-21
> **luigiburdo said:**
> Hi  Este,
I dont have any xorg.conf in /etc/X11/  in any way i didnt setup nothing there , everything was made by Mate installation on Mini G4... I dont know if on PowerBook because the 
different video board was needed something related xorg.conf and there i think rican_linux can gave help more then me.
if you need i can generate one and copy here.

Sorry about g+ i will reply soon as possible there too.


@LB:

Well, indeed, the installer didn't set up the xorg file for me either . . . but many flavors of linux need one to "figure out" the display . . . it's simple enough to "configure" one, which I did for this MATE install, or, previously for the Lu install I "wget" -ed on from the "linuxjemac.be" site . . . and then "mv" to the /etc/X11/xorg.conf  position.  Doing that stopped the "freezes" in the GUI.  Try it, but follow the FAQ . . . have to "stop" lightdm and then after configuring "start" it, etc.  It should help with the "crashes."  You could copy it here, but someone else would have to comment on it, particularly for the 3D stuff you might have to "adjust" the xorg.conf file--I know nothing about 3D.

No worries on the G+, we can "talk" here.  If your MATE system is installed, then the only question is whether you have to type your boot params at the second Yaboot window, or whether you've added them to the Yaboot file--sounds like you already did that--should be OK if you add the xorg.conf file.

e.e.p.

---

### Post by luigiburdo on 2015-01-21
here is my yaboot. 
"sudo nano /etc/yaboot.conf"
"sudo ybin -v" for install the new config

> 

image=/boot/vmlinux
        label=Linux
        read-only
        initrd=/boot/initrd.img
        append="video=radeonfb: off video=offb: off radeon.modeset=1 radeon.agpmode=-1" (no space where off are because :OFF make  :off smiley here)



and my generated Xorg conf.

ection "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
    ModulePath   "/usr/lib/xorg/modules"
    FontPath     "/usr/share/fonts/X11/misc"
    FontPath     "/usr/share/fonts/X11/cyrillic"
    FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/Type1"
    FontPath     "/usr/share/fonts/X11/100dpi"
    FontPath     "/usr/share/fonts/X11/75dpi"
    FontPath     "built-ins"
EndSection

Section "Module"
    Load  "glx"
EndSection

Section "InputDevice"
    Identifier  "Keyboard0"
    Driver      "kbd"
EndSection

Section "InputDevice"
    Identifier  "Mouse0"
    Driver      "mouse"
    Option        "Protocol" "auto"
    Option        "Device" "/dev/input/mice"
    Option        "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
    Identifier   "Monitor0"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "NoAccel"                # [<bool>]
        #Option     "SWcursor"               # [<bool>]
        #Option     "EnablePageFlip"         # [<bool>]
        #Option     "ColorTiling"            # [<bool>]
        #Option     "ColorTiling2D"          # [<bool>]
        #Option     "RenderAccel"            # [<bool>]
        #Option     "SubPixelOrder"          # [<str>]
        #Option     "AccelMethod"            # <str>
        #Option     "EXAVSync"               # [<bool>]
        #Option     "EXAPixmaps"             # [<bool>]
        #Option     "ZaphodHeads"            # <str>
        #Option     "EnablePageFlip"         # [<bool>]
        #Option     "SwapbuffersWait"        # [<bool>]
    Identifier  "Card0"
    Driver      "radeon"
    BusID       "PCI:0:16:0"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
    SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

---

### Post by este.el.paz on 2015-01-21
@LB:

Cool.  Looks fine.  Is it working?  No GUI freezes?

e.e.p.

---

### Post by luigiburdo on 2015-01-22
For me works :)

---

### Post by este.el.paz on 2015-01-22
> **luigiburdo said:**
> For me works :)

Good news. 

e.e.p.

---

### Post by luigiburdo on 2015-01-23
Hi guys i found the way here to... PowerMac G5 Quad with Nvidia and Radeon 4650HD in Couple "Work" with mate with full 2D/3D acceleration too.

There is only a strange and bad issue to report the mouse pointer disappear or swap alone to thescreen (screen2 where is the nvidia) and not return on the RadeonHD (screen0)...
I think this is an Xorg bug ... 

for made run "live video=nouveaufb:off nouveau.modeset=0 radeon.modeset=1"


In the shot Mate on Quad G5 Nvidia 7800gtx 16x pcie slot , RadeonHD 4650 in pcie 8x slot.


[IMG]https://scontent-a-ams.xx.fbcdn.net/hphotos-xpa1/v/t1.0-9/10942755_10203455171281544_4976995945031155359_n.jpg?oh=9a71d65828770b00771ee250f7a19ff7&oe=5560B38C[/IMG]

---

### Post by xeno74 on 2015-01-24
New Mesa install instructions for ubuntu MATE 14.10 PowerPC (for example for a Radeon HD6870): [http://forum.hyperion-entertainment.biz]("http://forum.hyperion-entertainment.biz/viewtopic.php?f=35&p=31539#p31539")

[[IMG]http://forum.hyperion-entertainment.biz/download/file.php?id=1495&t=1[/IMG]]("http://forum.hyperion-entertainment.biz/download/file.php?id=1495&mode=view")

---

### Post by Dukenukemx on 2015-01-24
Still trying to fix the 3D acceleration on my PowerBook G4 Titanium.  Tried xeno74's suggestion but with r300 instead of r600.  This is what glxinfo | grep render shows.  Am I the only person who can't get 3D working on their PowerBook?  Also I made a /etc/X11/xorg.conf.  
```

libGL error: failed to load driver: swrast
libGL error: Try again with LIBGL_DEBUG=verbose for more details.
direct [COLOR="#B22222"]render[/COLOR]ing: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
GLX_MESA_mutlithread_makecurrect, GLX_MESA_query_[COLOR="#B22222"]render[/COLOR]er,
OpenGL [COLOR="#B22222"]render[/COLOR]er string: Gallium 0.4 on softpipe

```

---

### Post by luigiburdo on 2015-01-25
Everything look like is working ... except  a stupid bug on mouse "it desappear in other dimension" if i move it neear the deskop borders and the doubled elements on task bars.

[IMG]https://scontent-a-mxp.xx.fbcdn.net/hphotos-xpa1/t31.0-8/10945797_10203467465188884_7552388214439503051_o.jpg[/IMG]

---

### Post by xeno74 on 2015-01-25
> **Dukenukemx said:**
> Still trying to fix the 3D acceleration on my PowerBook G4 Titanium.  Tried xeno74's suggestion but with r300 instead of r600.  This is what glxinfo | grep render shows.  Am I the only person who can't get 3D working on their PowerBook?  Also I made a /etc/X11/xorg.conf.  
```

libGL error: failed to load driver: swrast
libGL error: Try again with LIBGL_DEBUG=verbose for more details.
direct [COLOR=#B22222]render[/COLOR]ing: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
GLX_MESA_mutlithread_makecurrect, GLX_MESA_query_[COLOR=#B22222]render[/COLOR]er,
OpenGL [COLOR=#B22222]render[/COLOR]er string: Gallium 0.4 on softpipe

```

3D  acceleration doesn't work with your Radeon chip. The problem is, the **r300_dri.so** that is  shipped with the unofficial Mesa version is the Gallium driver. This only works with  DRI2. Unfortunately it seems your ATi Radeon chip isn't compatible with DRI2, so all of the 3d rendering is done via **softpipe**. I compiled **Mesa 7.11.2 classic (DRI 1)** for old graphics cards.

Download: [http://www.file-upload.net/download-10203572/Mesa-7.11_Debian7.7_classic_dri.tar.gz.html](http://www.file-upload.net/download-10203572/Mesa-7.11_Debian7.7_classic_dri.tar.gz.html)

 I compiled it for Debian 7.7. I hope it works for you.

_Installation instructions_:

[LIST=1]
[*] Copy the unpacked Mesa directory to /usr/local: 

```
cp -R Mesa7.11.2-without-gallium /usr/local
``` 
[*] ```
mv /usr/lib/powerpc-linux-gnu/dri/r300_dri.so /usr/lib/powerpc-linux-gnu/dri/r300_dri.so.bak
``` 
[*] ```
cp /usr/local/Mesa7.11.2-without-gallium/lib/dri/r300_dri.so /usr/lib/powerpc-linux-gnu/dri
``` 
[*] ```
mv /usr/lib/powerpc-linux-gnu/libGL.so.1.2 /usr/lib/powerpc-linux-gnu/libGL.so.1.2.bak
``` 
[*] ```
cp /usr/local/Mesa7.11.2-without-gallium/lib/libGL.so.1.2 /usr/lib/powerpc-linux-gnu/
``` 
[/LIST]
      
I tested SuperTuxKart 0.8.1 but it doesn't work because of the old GPU. But I could start SuperTuxKart 0.6.2a.

---

### Post by luigiburdo on 2015-01-25
Christian on minig4 supertux cart was working great the lastest... the only problem is the speed and the low vram ... but there im using the 0.8 , mesa 10 from mate and no patch.
the patch for sure is needed on radeonhd ... and we have to say thanks to you for this ;)

---

### Post by rican-linux on 2015-01-25
Sadly things are not going to get better for old mac PPC users. I do not think anyone is going to fix the **r300_dri.so** issue.

---

### Post by Dukenukemx on 2015-01-25
> **xeno74 said:**
> 3D  acceleration doesn't work with your Radeon chip. The problem is, the **r300_dri.so** that is  shipped with the unofficial Mesa version is the Gallium driver. This only works with  DRI2. Unfortunately it seems your ATi Radeon chip isn't compatible with DRI2, so all of the 3d rendering is done via **softpipe**. I compiled **Mesa 7.11.2 classic (DRI 1)** for old graphics cards.

Download: [http://www.file-upload.net/download-10203572/Mesa-7.11_Debian7.7_classic_dri.tar.gz.html](http://www.file-upload.net/download-10203572/Mesa-7.11_Debian7.7_classic_dri.tar.gz.html)

 I compiled it for Debian 7.7. I hope it works for you.

_Installation instructions_:

[LIST=1]
[*] Copy the unpacked Mesa directory to /usr/local: 

```
cp -R Mesa7.11.2-without-gallium /usr/local
``` 
[*] ```
mv /usr/lib/powerpc-linux-gnu/dri/r300_dri.so /usr/lib/powerpc-linux-gnu/dri/r300_dri.so.bak
``` 
[*] ```
cp /usr/local/Mesa7.11.2-without-gallium/lib/dri/r300_dri.so /usr/lib/powerpc-linux-gnu/dri
``` 
[*] ```
mv /usr/lib/powerpc-linux-gnu/libGL.so.1.2 /usr/lib/powerpc-linux-gnu/libGL.so.1.2.bak
``` 
[*] ```
cp /usr/local/Mesa7.11.2-without-gallium/lib/libGL.so.1.2 /usr/lib/powerpc-linux-gnu/
``` 
[/LIST]
      
I tested SuperTuxKart 0.8.1 but it doesn't work because of the old GPU. But I could start SuperTuxKart 0.6.2a.

It works, at least I think it does.  "Glxinfo | grep render" shows this.

```

direct [COLOR="#B22222"]render[/COLOR]ing: Yes
      GLX_MESA_multithread_makecurrent, GLX_MESA_query_[COLOR="#B22222"]render[/COLOR]er,
OpenGL [COLOR="#B22222"]render[/COLOR]er string: Mesa DRI 300 (RV350 4E50) PowerPC/Altivec TCL DRI2

```

But when I run glxgears I get "Segmentation fault (core dumped)".  A small window shows up but black.  Not sure if that means 3D acceleration works or not.  I did fresh install 14.04 cause I had done a lot of things to make 3D work.  There's no xorg.conf now.

**EDIT**

I tried moving the libGL.so.1.2 to the /usr/lib/powerpc-linux-gnu/mesa folder but renamed libGL.so.1.2.0.  Figured maybe you made a mistake?  Tried glxgears and it showed up briefly with wrong colors and entire pc froze.  I did make a libGL.so.1.2.0.bak just in case.

---

### Post by xeno74 on 2015-01-27
There are some soft links to libGL.so.1.2.0. It's very important to replace the binary of libGL not a symbolic link.

Debian 7.7:

ls -l /usr/lib/powerpc-linux-gnu/libGL.so*

lrwxrwxrwx 1 root root 10 Jun 5 2013 /usr/lib/powerpc-linux-gnu/libGL.so -> libGL.so.1
lrwxrwxrwx 1 root root 12 Jan 25 13:50 /usr/lib/powerpc-linux-gnu/libGL.so.1 -> libGL.so.1.2
-rwxr-xr-x 1 root root 2527913 Jan 25 13:40 /usr/lib/powerpc-linux-gnu/libGL.so.1.2 // patched library
-rw-r--r-- 1 root root 457476 Jun 5 2013 /usr/lib/powerpc-linux-gnu/libGL.so.1.2.bak  // old library

---

### Post by Dukenukemx on 2015-01-27
I had restored libGL.so.1.2.0 that I replaced, cause I wasn't sure if I was suppose to do that.  I ran "ls -l /usr/lib/powerpc-linux-gnu/libGL.so*" and got this.  Also I'm using Ubuntu 14.04 Mate and there wasn't any libGL.so.1.2.  

```

 -rwxr-xr-x 1 root root 2527913 Jan 25 14:57 /usr/lib/powerpc-linux-gnu/libGL.so.1.2

```

Here's what "ls -al  /usr/lib/powerpc-linux-gnu/dri" looks like if it helps. 
```

total 50112
drwxr-xr-x  2 root root     4096 Jan 25 14:57 .
drwxr-xr-x 81 root root    69632 Jan 25 14:57 ..
-rw-r--r--  1 root root    17780 Apr 15  2014 dummy_drv_video.so
-rw-r--r--  1 root root  4504364 Oct  1 08:10 nouveau_dri.so
-rw-r--r--  1 root root  4210760 Oct  1 08:10 nouveau_vieux_dri.so
-rw-r--r--  1 root root  4210760 Oct  1 08:10 r200_dri.so
-rwxr-xr-x  1 root root 18330855 Jan 25 14:57 [COLOR="#00FF00"]r300_dri.so[/COLOR]
-rw-r--r--  1 root root  3705636 Oct  1 08:10 r300_dri.so.bak
-rw-r--r--  1 root root  4249892 Oct  1 08:10 r600_dri.so
-rw-r--r--  1 root root  4210760 Oct  1 08:10 radeon_dri.so
-rw-r--r--  1 root root  4210760 Oct  1 08:10 swrast_dri.so
-rw-r--r--  1 root root  3558388 Oct  1 08:10 vmwgfx_dri.so

```

---

### Post by Dukenukemx on 2015-01-27
Ran software update on Ubuntu and it changed some files around.  Had to reload xeno754's files again and glxgears will now freeze the entire machine, but the gears do show up.  \\:D/

The command "ls -l /usr/lib/powerpc-linux-gnu/libGL.so*" now shows this.  
```

lrwxrwxrwx 1 root root      12 Jan 27 14:03 /usr/lib/powerpc-linux-gnu/libGL.so.1 -> libGL.so.1.2
-rwxr-xr-x 1 root root 2527913 Jan 27 14:43 /usr/lib/powerpc-linux-gnu/libGL.so.1.2
-rwxr-xr-x 1 root root 2527913 Jan 27 14:30 /usr/lib/powerpc-linux-gnu/libGL.so.1.2.bak


```

---

### Post by rsavage on 2015-01-30
> **rican-linux said:**
> Sadly things are not going to get better for old mac PPC users. I do not think anyone is going to fix the **r300_dri.so** issue.

[https://ubuntu-mate.community/t/powerpc-14-04-release-notes/68/4?u=smiffy](https://ubuntu-mate.community/t/powerpc-14-04-release-notes/68/4?u=smiffy)

---

### Post by rican-linux on 2015-01-30
@rsavage have you tested them? I downgraded my mesa packages so I can get 3D with UMS.

---

### Post by rsavage on 2015-01-30
In so far as glxgears now works.  This is not my machine, and I'm pretty annoyed that nobody with this card has updated the known issues page with the bug.

> **rican-linux said:**
> @rsavage have you tested them? I downgraded my mesa packages so I can get 3D with UMS.

Can you publish instructions for ums?.....

---

### Post by rican-linux on 2015-01-30
Dan at PPC Luddite posted instructions [here]("http://ppcluddite.blogspot.com/2012/03/installing-debian-linux-on-ppc-part-iv.html#graphics"). I know what you mean. I remember it was driving me insane when I was running Jessie. I eventually had to set my default display to 16 in Xorg just to get working 3D. I am thinking about getting another powerbook or ibook. If I do I will definitely try those patched packages.

---

### Post by rsavage on 2015-01-30
> **rican-linux said:**
> Dan at PPC Luddite posted instructions [here]("http://ppcluddite.blogspot.com/2012/03/installing-debian-linux-on-ppc-part-iv.html#graphics"). 
That's just a re-wording of the instructions I wrote for 12.04.  You need to do a lot more for 14.04, but it is possible.

---

### Post by rican-linux on 2015-01-30
My bad I did not know you were asking about 14.04. 

If that patch works I would much rather go that route than downgrading my packages. It is just right now I am using my powerbook as my primary laptop and I really need it to be stable. So undoing those changes and trying the parched packages is not what I would like to do right now.

---

### Post by Dukenukemx on 2015-02-02
> **rsavage said:**
> [https://ubuntu-mate.community/t/powerpc-14-04-release-notes/68/4?u=smiffy](https://ubuntu-mate.community/t/powerpc-14-04-release-notes/68/4?u=smiffy)

I downloaded the mesa-debs and installed them, but didn't work.  

```

Error: couldn't find RGB GLX visual or fbconfig

```

Whatever the issue is probably has to do with this error I see when booting. Regardless of what I do I keep seeing it.  

```

*ERROR* Unable to locate a BIOS ROM
```

---

### Post by luigiburdo on 2015-02-03
The Video of Ubuntu Mate running on MacMini G4 

[https://www.youtube.com/watch?v=m2mx9lmhEuQ](https://www.youtube.com/watch?v=m2mx9lmhEuQ)

---

### Post by Dukenukemx on 2015-02-05
Mate 1.81 fully works with Radeon 9200 with no issue?  Luigiburdo can you direct me to the Mate that you used?  Besides the PowerBook G4 that I'm still trying to get 3D working, I now have a Mac G5.  Replaced a 120uf 450v capacitor in the powersupply and it now turns on, but with OS X 10.5.  I wanna put Ubuntu Mate on that too but it has a Radeon 9600 graphics card.  So yea.

---

### Post by rican-linux on 2015-02-05
> **luigiburdo said:**
> The Video of Ubuntu Mate running on MacMini G4 

[https://www.youtube.com/watch?v=m2mx9lmhEuQ](https://www.youtube.com/watch?v=m2mx9lmhEuQ)

WOW great job! It was the best presentation I have seen on youtube. Most Linux on PPC vids are just people either giving minal presentations or just complaining. What games were you playing?

---

### Post by luigiburdo on 2015-02-05
Dukenumkemx

No issue with the mini everything working right .
I use the only one Ubuntu Mate PPC done ;)
[COLOR=#404040][FONT=Roboto]Download link: [/FONT][/COLOR][http://1drv.ms/1wgsdUk](http://1drv.ms/1wgsdUk)
[COLOR=#404040][FONT=Roboto]md5sum 2bb57b2bbf87b668a94c38dd0393b263  ubuntu-mate-14.04.1-dev.34508-desktop-powerpc.iso[/FONT][/COLOR]
[COLOR=#404040][FONT=Roboto]sha1sum 9fe995a2832e2c0bcce5604b08095fb7217882ac  ubuntu-mate-14.04.1-dev.34508-desktop-powerpc.iso[/FONT][/COLOR]
[COLOR=#404040][FONT=Roboto]sha256sum b53d2836c00a2f9180353e908f09ee9eb4b17138dcc72bf692c6bd68b2756032  ubuntu-mate-14.04.1-dev.34508-desktop-powerpc.iso&#65279;

```
[/FONT][/COLOR][COLOR=#404040][FONT=Roboto]On G5 with radeon try to install with this line
 "live video=radeonfb:off radeon.modeset=1 radeon.agpmode=-1" 
if you have issiues do
[/FONT][/COLOR][COLOR=#404040][FONT=Roboto]"live video=radeonfb:off radeon.modeset=1 radeon.agpmode=-1 video=offb:off"[/FONT][/COLOR][COLOR=#404040][FONT=Roboto]
```

hope it work for you ;)[/FONT][/COLOR]

---

### Post by luigiburdo on 2015-02-05
Rican-linux
I just install Chromium, Free'Doom' Quake and Frogatto but there are many in Ubuntu Software Center.

---

### Post by rican-linux on 2015-02-05
Chromium is available for ppc??

---

### Post by luigiburdo on 2015-02-06
The game  yes , the browser not :)
if one day will work wine on ppc like it work on arm probably ;)

---

### Post by rican-linux on 2015-02-06
ah that is what I thought. Thanks for your work!

---

### Post by luigiburdo on 2015-02-06
My Xorg.0.log requested in g+ ubuntu mate community... 
hope will help for fix the G5 with RadeonHD issues 

```


[    12.688] 
X.Org X Server 1.15.1
Release Date: 2014-04-13
[    12.688] X Protocol Version 11, Revision 0
[    12.688] Build Operating System: Linux 3.2.0-56-powerpc64-smp ppc Ubuntu
[    12.688] Current Operating System: Linux luigi-desktop 3.13.0-45-powerpc64-smp #74-Ubuntu SMP Tue Jan 13 19:52:11 UTC 2015 ppc64
[    12.688] Kernel command line: root=UUID=04c7aa91-2ba7-4c82-8433-36b8b4db6c57 ro quiet splash video=offb:off video=nouveaufb:off radeon.modeset=1 radeon.agpmode=-1 nouveau.modeset=0 
[    12.688] Build Date: 10 December 2014  06:14:39PM
[    12.688] xorg-server 2:1.15.1-0ubuntu2.6 (For technical support please see http://www.ubuntu.com/support) 
[    12.688] Current version of pixman: 0.30.2
[    12.688]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    12.688] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    12.688] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Feb  6 19:25:22 2015
[    12.691] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    12.691] (==) No Layout section.  Using the first Screen section.
[    12.691] (==) No screen section available. Using defaults.
[    12.691] (**) |-->Screen "Default Screen Section" (0)
[    12.691] (**) |   |-->Monitor "<default monitor>"
[    12.692] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    12.692] (==) Automatically adding devices
[    12.692] (==) Automatically enabling devices
[    12.692] (==) Automatically adding GPU devices
[    12.692] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    12.692]     Entry deleted from font path.
[    12.692] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    12.692]     Entry deleted from font path.
[    12.692] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    12.692]     Entry deleted from font path.
[    12.692] (WW) The directory "/usr/share/fonts/X11/Type1" does not exist.
[    12.692]     Entry deleted from font path.
[    12.692] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    12.692]     Entry deleted from font path.
[    12.692] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    12.692]     Entry deleted from font path.
[    12.692] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    built-ins
[    12.692] (==) ModulePath set to "/usr/lib/powerpc-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    12.692] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    12.692] (II) Loader magic: 0x203ad694
[    12.692] (II) Module ABI versions:
[    12.692]     X.Org ANSI C Emulation: 0.4
[    12.692]     X.Org Video Driver: 15.0
[    12.692]     X.Org XInput driver : 20.0
[    12.692]     X.Org Server Extension : 8.0
[    12.693] (II) xfree86: Adding drm device (/dev/dri/card0)
[    12.695] (--) PCI: (0:10:0:0) 1002:9498:174b:9498 rev 0, Mem @ 0xc0000000/268435456, 0xd0020000/65536, I/O @ 0x00000400/256, BIOS @ 0x????????/131072
[    12.695] (--) PCI:*(1:8:0:0) 10de:009d:10de:004d rev 161, Mem @ 0x82000000/16777216, 0xa0000000/536870912, 0x81000000/16777216, I/O @ 0x00001000/128, BIOS @ 0x????????/131072
[    12.695] Initializing built-in extension Generic Event Extension
[    12.695] Initializing built-in extension SHAPE
[    12.695] Initializing built-in extension MIT-SHM
[    12.695] Initializing built-in extension XInputExtension
[    12.695] Initializing built-in extension XTEST
[    12.695] Initializing built-in extension BIG-REQUESTS
[    12.695] Initializing built-in extension SYNC
[    12.695] Initializing built-in extension XKEYBOARD
[    12.695] Initializing built-in extension XC-MISC
[    12.695] Initializing built-in extension SECURITY
[    12.695] Initializing built-in extension XINERAMA
[    12.696] Initializing built-in extension XFIXES
[    12.696] Initializing built-in extension RENDER
[    12.696] Initializing built-in extension RANDR
[    12.696] Initializing built-in extension COMPOSITE
[    12.696] Initializing built-in extension DAMAGE
[    12.696] Initializing built-in extension MIT-SCREEN-SAVER
[    12.696] Initializing built-in extension DOUBLE-BUFFER
[    12.696] Initializing built-in extension RECORD
[    12.696] Initializing built-in extension DPMS
[    12.696] Initializing built-in extension Present
[    12.696] Initializing built-in extension DRI3
[    12.696] Initializing built-in extension X-Resource
[    12.696] Initializing built-in extension XVideo
[    12.696] Initializing built-in extension XVideo-MotionCompensation
[    12.696] Initializing built-in extension SELinux
[    12.696] Initializing built-in extension XFree86-VidModeExtension
[    12.696] Initializing built-in extension XFree86-DGA
[    12.696] Initializing built-in extension XFree86-DRI
[    12.696] Initializing built-in extension DRI2
[    12.696] (II) LoadModule: "glx"
[    12.707] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    12.723] (II) Module glx: vendor="X.Org Foundation"
[    12.724]     compiled for 1.15.1, module version = 1.0.0
[    12.724]     ABI class: X.Org Server Extension, version 8.0
[    12.724] (==) AIGLX enabled
[    12.724] Loading extension GLX
[    12.724] (==) Matched fglrx as autoconfigured driver 0
[    12.724] (==) Matched ati as autoconfigured driver 1
[    12.724] (==) Matched nvidia as autoconfigured driver 2
[    12.724] (==) Matched nouveau as autoconfigured driver 3
[    12.724] (==) Matched modesetting as autoconfigured driver 4
[    12.724] (==) Matched fbdev as autoconfigured driver 5
[    12.724] (==) Assigned the driver to the xf86ConfigLayout
[    12.724] (II) LoadModule: "fglrx"
[    12.725] (WW) Warning, couldn't open module fglrx
[    12.725] (II) UnloadModule: "fglrx"
[    12.725] (II) Unloading fglrx
[    12.725] (EE) Failed to load module "fglrx" (module does not exist, 0)
[    12.725] (II) LoadModule: "ati"
[    12.725] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    12.725] (II) Module ati: vendor="X.Org Foundation"
[    12.725]     compiled for 1.15.1, module version = 7.3.0
[    12.725]     Module class: X.Org Video Driver
[    12.725]     ABI class: X.Org Video Driver, version 15.0
[    12.725] (II) LoadModule: "radeon"
[    12.726] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    12.739] (II) Module radeon: vendor="X.Org Foundation"
[    12.739]     compiled for 1.15.1, module version = 7.3.0
[    12.739]     Module class: X.Org Video Driver
[    12.739]     ABI class: X.Org Video Driver, version 15.0
[    12.739] (II) LoadModule: "nvidia"
[    12.739] (WW) Warning, couldn't open module nvidia
[    12.739] (II) UnloadModule: "nvidia"
[    12.739] (II) Unloading nvidia
[    12.740] (EE) Failed to load module "nvidia" (module does not exist, 0)
[    12.740] (II) LoadModule: "nouveau"
[    12.740] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    12.742] (II) Module nouveau: vendor="X.Org Foundation"
[    12.742]     compiled for 1.15.0, module version = 1.0.10
[    12.742]     Module class: X.Org Video Driver
[    12.742]     ABI class: X.Org Video Driver, version 15.0
[    12.742] (II) LoadModule: "modesetting"
[    12.743] (WW) Warning, couldn't open module modesetting
[    12.743] (II) UnloadModule: "modesetting"
[    12.743] (II) Unloading modesetting
[    12.743] (EE) Failed to load module "modesetting" (module does not exist, 0)
[    12.743] (II) LoadModule: "fbdev"
[    12.743] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    12.743] (II) Module fbdev: vendor="X.Org Foundation"
[    12.743]     compiled for 1.15.0, module version = 0.4.4
[    12.743]     Module class: X.Org Video Driver
[    12.743]     ABI class: X.Org Video Driver, version 15.0
[    12.743] (==) Matched fglrx as autoconfigured driver 0
[    12.743] (==) Matched ati as autoconfigured driver 1
[    12.743] (==) Matched nvidia as autoconfigured driver 2
[    12.743] (==) Matched nouveau as autoconfigured driver 3
[    12.743] (==) Matched modesetting as autoconfigured driver 4
[    12.743] (==) Matched fbdev as autoconfigured driver 5
[    12.743] (==) Assigned the driver to the xf86ConfigLayout
[    12.743] (II) LoadModule: "fglrx"
[    12.744] (WW) Warning, couldn't open module fglrx
[    12.744] (II) UnloadModule: "fglrx"
[    12.744] (II) Unloading fglrx
[    12.745] (EE) Failed to load module "fglrx" (module does not exist, 0)
[    12.745] (II) LoadModule: "ati"
[    12.745] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[    12.745] (II) Module ati: vendor="X.Org Foundation"
[    12.745]     compiled for 1.15.1, module version = 7.3.0
[    12.745]     Module class: X.Org Video Driver
[    12.745]     ABI class: X.Org Video Driver, version 15.0
[    12.745] (II) LoadModule: "nvidia"
[    12.746] (WW) Warning, couldn't open module nvidia
[    12.746] (II) UnloadModule: "nvidia"
[    12.746] (II) Unloading nvidia
[    12.746] (EE) Failed to load module "nvidia" (module does not exist, 0)
[    12.746] (II) LoadModule: "nouveau"
[    12.746] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    12.746] (II) Module nouveau: vendor="X.Org Foundation"
[    12.746]     compiled for 1.15.0, module version = 1.0.10
[    12.746]     Module class: X.Org Video Driver
[    12.746]     ABI class: X.Org Video Driver, version 15.0
[    12.746] (II) UnloadModule: "nouveau"
[    12.746] (II) Unloading nouveau
[    12.746] (II) Failed to load module "nouveau" (already loaded, 0)
[    12.746] (II) LoadModule: "modesetting"
[    12.747] (WW) Warning, couldn't open module modesetting
[    12.747] (II) UnloadModule: "modesetting"
[    12.747] (II) Unloading modesetting
[    12.747] (EE) Failed to load module "modesetting" (module does not exist, 0)
[    12.747] (II) LoadModule: "fbdev"
[    12.748] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    12.748] (II) Module fbdev: vendor="X.Org Foundation"
[    12.748]     compiled for 1.15.0, module version = 0.4.4
[    12.748]     Module class: X.Org Video Driver
[    12.748]     ABI class: X.Org Video Driver, version 15.0
[    12.748] (II) UnloadModule: "fbdev"
[    12.748] (II) Unloading fbdev
[    12.748] (II) Failed to load module "fbdev" (already loaded, 0)
[    12.748] (II) RADEON: Driver for ATI Radeon chipsets:
    ATI Radeon Mobility X600 (M24) 3150 (PCIE), ATI FireMV 2400 (PCI),
    ATI Radeon Mobility X300 (M24) 3152 (PCIE),
    ATI FireGL M24 GL 3154 (PCIE), ATI FireMV 2400 3155 (PCI),
    ATI Radeon X600 (RV380) 3E50 (PCIE),
    ATI FireGL V3200 (RV380) 3E54 (PCIE), ATI Radeon IGP320 (A3) 4136,
    ATI Radeon IGP330/340/350 (A4) 4137, ATI Radeon 9500 AD (AGP),
    ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
    ATI FireGL Z1 AG (AGP), ATI Radeon 9800SE AH (AGP),
    ATI Radeon 9800 AI (AGP), ATI Radeon 9800 AJ (AGP),
    ATI FireGL X2 AK (AGP), ATI Radeon 9600 AP (AGP),
    ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
    ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP), ATI Radeon 9650,
    ATI FireGL RV360 AV (AGP), ATI Radeon 7000 IGP (A4+) 4237,
    ATI Radeon 8500 AIW BB (AGP), ATI Radeon IGP320M (U1) 4336,
    ATI Radeon IGP330M/340M/350M (U2) 4337,
    ATI Radeon Mobility 7000 IGP 4437, ATI Radeon 9000/PRO If (AGP/PCI),
    ATI Radeon 9000 Ig (AGP/PCI), ATI Radeon X800 (R420) JH (AGP),
    ATI Radeon X800PRO (R420) JI (AGP),
    ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK (AGP),
    ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AGP),
    ATI Radeon Mobility 9800 (M18) JN (AGP),
    ATI Radeon X800 SE (R420) (AGP), ATI Radeon X800XT (R420) JP (AGP),
    ATI Radeon X800 VE (R420) JT (AGP), ATI Radeon X850 (R480) (AGP),
    ATI Radeon X850 XT (R480) (AGP), ATI Radeon X850 SE (R480) (AGP),
    ATI Radeon X850 PRO (R480) (AGP), ATI Radeon X850 XT PE (R480) (AGP),
    ATI Radeon Mobility M7 LW (AGP),
    ATI Mobility FireGL 7800 M7 LX (AGP),
    ATI Radeon Mobility M6 LY (AGP), ATI Radeon Mobility M6 LZ (AGP),
    ATI FireGL Mobility 9000 (M9) Ld (AGP),
    ATI Radeon Mobility 9000 (M9) Lf (AGP),
    ATI Radeon Mobility 9000 (M9) Lg (AGP), ATI FireMV 2400 PCI,
    ATI Radeon 9700 Pro ND (AGP), ATI Radeon 9700/9500Pro NE (AGP),
    ATI Radeon 9600TX NF (AGP), ATI FireGL X1 NG (AGP),
    ATI Radeon 9800PRO NH (AGP), ATI Radeon 9800 NI (AGP),
    ATI FireGL X2 NK (AGP), ATI Radeon 9800XT NJ (AGP),
    ATI Radeon Mobility 9600/9700 (M10/M11) NP (AGP),
    ATI Radeon Mobility 9600 (M10) NQ (AGP),
    ATI Radeon Mobility 9600 (M11) NR (AGP),
    ATI Radeon Mobility 9600 (M10) NS (AGP),
    ATI FireGL Mobility T2 (M10) NT (AGP),
    ATI FireGL Mobility T2e (M11) NV (AGP), ATI Radeon QD (AGP),
    ATI Radeon QE (AGP), ATI Radeon QF (AGP), ATI Radeon QG (AGP),
    ATI FireGL 8700/8800 QH (AGP), ATI Radeon 8500 QL (AGP),
    ATI Radeon 9100 QM (AGP), ATI Radeon 7500 QW (AGP/PCI),
    ATI Radeon 7500 QX (AGP/PCI), ATI Radeon VE/7000 QY (AGP/PCI),
    ATI Radeon VE/7000 QZ (AGP/PCI), ATI ES1000 515E (PCI),
    ATI Radeon Mobility X300 (M22) 5460 (PCIE),
    ATI Radeon Mobility X600 SE (M24C) 5462 (PCIE),
    ATI FireGL M22 GL 5464 (PCIE), ATI Radeon X800 (R423) UH (PCIE),
    ATI Radeon X800PRO (R423) UI (PCIE),
    ATI Radeon X800LE (R423) UJ (PCIE),
    ATI Radeon X800SE (R423) UK (PCIE),
    ATI Radeon X800 XTP (R430) (PCIE), ATI Radeon X800 XL (R430) (PCIE),
    ATI Radeon X800 SE (R430) (PCIE), ATI Radeon X800 (R430) (PCIE),
    ATI FireGL V7100 (R423) (PCIE), ATI FireGL V5100 (R423) UQ (PCIE),
    ATI FireGL unknown (R423) UR (PCIE),
    ATI FireGL unknown (R423) UT (PCIE),
    ATI Mobility FireGL V5000 (M26) (PCIE),
    ATI Mobility FireGL V5000 (M26) (PCIE),
    ATI Mobility Radeon X700 XL (M26) (PCIE),
    ATI Mobility Radeon X700 (M26) (PCIE),
    ATI Mobility Radeon X700 (M26) (PCIE),
    ATI Radeon X550XTX 5657 (PCIE), ATI Radeon 9100 IGP (A5) 5834,
    ATI Radeon Mobility 9100 IGP (U3) 5835,
    ATI Radeon XPRESS 200 5954 (PCIE),
    ATI Radeon XPRESS 200M 5955 (PCIE), ATI Radeon 9250 5960 (AGP),
    ATI Radeon 9200 5961 (AGP), ATI Radeon 9200 5962 (AGP),
    ATI Radeon 9200SE 5964 (AGP), ATI FireMV 2200 (PCI),
    ATI ES1000 5969 (PCI), ATI Radeon XPRESS 200 5974 (PCIE),
    ATI Radeon XPRESS 200M 5975 (PCIE),
    ATI Radeon XPRESS 200 5A41 (PCIE),
    ATI Radeon XPRESS 200M 5A42 (PCIE),
    ATI Radeon XPRESS 200 5A61 (PCIE),
    ATI Radeon XPRESS 200M 5A62 (PCIE),
    ATI Radeon X300 (RV370) 5B60 (PCIE),
    ATI Radeon X600 (RV370) 5B62 (PCIE),
    ATI Radeon X550 (RV370) 5B63 (PCIE),
    ATI FireGL V3100 (RV370) 5B64 (PCIE),
    ATI FireMV 2200 PCIE (RV370) 5B65 (PCIE),
    ATI Radeon Mobility 9200 (M9+) 5C61 (AGP),
    ATI Radeon Mobility 9200 (M9+) 5C63 (AGP),
    ATI Mobility Radeon X800 XT (M28) (PCIE),
    ATI Mobility FireGL V5100 (M28) (PCIE),
    ATI Mobility Radeon X800 (M28) (PCIE), ATI Radeon X850 5D4C (PCIE),
    ATI Radeon X850 XT PE (R480) (PCIE),
    ATI Radeon X850 SE (R480) (PCIE), ATI Radeon X850 PRO (R480) (PCIE),
    ATI unknown Radeon / FireGL (R480) 5D50 (PCIE),
    ATI Radeon X850 XT (R480) (PCIE),
    ATI Radeon X800XT (R423) 5D57 (PCIE),
    ATI FireGL V5000 (RV410) (PCIE), ATI Radeon X700 XT (RV410) (PCIE),
    ATI Radeon X700 PRO (RV410) (PCIE),
    ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X700 (RV410) (PCIE),
    ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X1800,
    ATI Mobility Radeon X1800 XT, ATI Mobility Radeon X1800,
    ATI Mobility FireGL V7200, ATI FireGL V7200, ATI FireGL V5300,
    ATI Mobility FireGL V7100, ATI Radeon X1800, ATI Radeon X1800,
    ATI Radeon X1800, ATI Radeon X1800, ATI Radeon X1800,
    ATI FireGL V7300, ATI FireGL V7350, ATI Radeon X1600, ATI RV505,
    ATI Radeon X1300/X1550, ATI Radeon X1550, ATI M54-GL,
    ATI Mobility Radeon X1400, ATI Radeon X1300/X1550,
    ATI Radeon X1550 64-bit, ATI Mobility Radeon X1300,
    ATI Mobility Radeon X1300, ATI Mobility Radeon X1300,
    ATI Mobility Radeon X1300, ATI Radeon X1300, ATI Radeon X1300,
    ATI RV505, ATI RV505, ATI FireGL V3300, ATI FireGL V3350,
    ATI Radeon X1300, ATI Radeon X1550 64-bit, ATI Radeon X1300/X1550,
    ATI Radeon X1600, ATI Radeon X1300/X1550, ATI Mobility Radeon X1450,
    ATI Radeon X1300/X1550, ATI Mobility Radeon X2300,
    ATI Mobility Radeon X2300, ATI Mobility Radeon X1350,
    ATI Mobility Radeon X1350, ATI Mobility Radeon X1450,
    ATI Radeon X1300, ATI Radeon X1550, ATI Mobility Radeon X1350,
    ATI FireMV 2250, ATI Radeon X1550 64-bit, ATI Radeon X1600,
    ATI Radeon X1650, ATI Radeon X1600, ATI Radeon X1600,
    ATI Mobility FireGL V5200, ATI Mobility Radeon X1600,
    ATI Radeon X1650, ATI Radeon X1650, ATI Radeon X1600,
    ATI Radeon X1300 XT/X1600 Pro, ATI FireGL V3400,
    ATI Mobility FireGL V5250, ATI Mobility Radeon X1700,
    ATI Mobility Radeon X1700 XT, ATI FireGL V5200,
    ATI Mobility Radeon X1700, ATI Radeon X2300HD,
    ATI Mobility Radeon HD 2300, ATI Mobility Radeon HD 2300,
    ATI Radeon X1950, ATI Radeon X1900, ATI Radeon X1950,
    ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
    ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
    ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
    ATI AMD Stream Processor, ATI Radeon X1900, ATI Radeon X1950,
    ATI RV560, ATI RV560, ATI Mobility Radeon X1900, ATI RV560,
    ATI Radeon X1950 GT, ATI RV570, ATI RV570, ATI FireGL V7400,
    ATI RV560, ATI Radeon X1650, ATI Radeon X1650, ATI RV560,
    ATI Radeon 9100 PRO IGP 7834, ATI Radeon Mobility 9200 IGP 7835,
    ATI Radeon X1200, ATI Radeon X1200, ATI Radeon X1200,
    ATI Radeon X1200, ATI Radeon X1200, ATI RS740, ATI RS740M, ATI RS740,
    ATI RS740M, ATI Radeon HD 2900 XT, ATI Radeon HD 2900 XT,
    ATI Radeon HD 2900 XT, ATI Radeon HD 2900 Pro, ATI Radeon HD 2900 GT,
    ATI FireGL V8650, ATI FireGL V8600, ATI FireGL V7600,
    ATI Radeon 4800 Series, ATI Radeon HD 4870 x2,
    ATI Radeon 4800 Series, ATI Radeon HD 4850 x2,
    ATI FirePro V8750 (FireGL), ATI FirePro V7760 (FireGL),
    ATI Mobility RADEON HD 4850, ATI Mobility RADEON HD 4850 X2,
    ATI Radeon 4800 Series, ATI FirePro RV770, AMD FireStream 9270,
    AMD FireStream 9250, ATI FirePro V8700 (FireGL),
    ATI Mobility RADEON HD 4870, ATI Mobility RADEON M98,
    ATI Mobility RADEON HD 4870, ATI Radeon 4800 Series,
    ATI Radeon 4800 Series, ATI FirePro M7750, ATI M98, ATI M98, ATI M98,
    ATI Mobility Radeon HD 4650, ATI Radeon RV730 (AGP),
    ATI Mobility Radeon HD 4670, ATI FirePro M5750,
    ATI Mobility Radeon HD 4670, ATI Radeon RV730 (AGP),
    ATI RV730XT [Radeon HD 4670], ATI RADEON E4600,
    ATI Radeon HD 4600 Series, ATI RV730 PRO [Radeon HD 4650],
    ATI FirePro V7750 (FireGL), ATI FirePro V5700 (FireGL),
    ATI FirePro V3750 (FireGL), ATI Mobility Radeon HD 4830,
    ATI Mobility Radeon HD 4850, ATI FirePro M7740, ATI RV740,
    ATI Radeon HD 4770, ATI Radeon HD 4700 Series, ATI Radeon HD 4770,
    ATI FirePro M5750, ATI RV610, ATI Radeon HD 2400 XT,
    ATI Radeon HD 2400 Pro, ATI Radeon HD 2400 PRO AGP, ATI FireGL V4000,
    ATI RV610, ATI Radeon HD 2350, ATI Mobility Radeon HD 2400 XT,
    ATI Mobility Radeon HD 2400, ATI RADEON E2400, ATI RV610,
    ATI FireMV 2260, ATI RV670, ATI Radeon HD3870,
    ATI Mobility Radeon HD 3850, ATI Radeon HD3850,
    ATI Mobility Radeon HD 3850 X2, ATI RV670,
    ATI Mobility Radeon HD 3870, ATI Mobility Radeon HD 3870 X2,
    ATI Radeon HD3870 X2, ATI FireGL V7700, ATI Radeon HD3850,
    ATI Radeon HD3690, AMD Firestream 9170, ATI Radeon HD 4550,
    ATI Radeon RV710, ATI Radeon RV710, ATI Radeon RV710,
    ATI Radeon HD 4350, ATI Mobility Radeon 4300 Series,
    ATI Mobility Radeon 4500 Series, ATI Mobility Radeon 4500 Series,
    ATI FirePro RG220, ATI Mobility Radeon 4330, ATI RV630,
    ATI Mobility Radeon HD 2600, ATI Mobility Radeon HD 2600 XT,
    ATI Radeon HD 2600 XT AGP, ATI Radeon HD 2600 Pro AGP,
    ATI Radeon HD 2600 XT, ATI Radeon HD 2600 Pro, ATI Gemini RV630,
    ATI Gemini Mobility Radeon HD 2600 XT, ATI FireGL V5600,
    ATI FireGL V3600, ATI Radeon HD 2600 LE,
    ATI Mobility FireGL Graphics Processor, ATI Radeon HD 3470,
    ATI Mobility Radeon HD 3430, ATI Mobility Radeon HD 3400 Series,
    ATI Radeon HD 3450, ATI Radeon HD 3450, ATI Radeon HD 3430,
    ATI Radeon HD 3450, ATI FirePro V3700, ATI FireMV 2450,
    ATI FireMV 2260, ATI FireMV 2260, ATI Radeon HD 3600 Series,
    ATI Radeon HD 3650 AGP, ATI Radeon HD 3600 PRO,
    ATI Radeon HD 3600 XT, ATI Radeon HD 3600 PRO,
    ATI Mobility Radeon HD 3650, ATI Mobility Radeon HD 3670,
    ATI Mobility FireGL V5700, ATI Mobility FireGL V5725,
    ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
    ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
    ATI Radeon HD 3300 Graphics, ATI Radeon HD 3200 Graphics,
    ATI Radeon 3000 Graphics, SUMO, SUMO, SUMO2, SUMO2, SUMO2, SUMO2,
    SUMO, SUMO, SUMO2, SUMO, SUMO, SUMO, SUMO, SUMO, ATI Radeon HD 4200,
    ATI Radeon 4100, ATI Mobility Radeon HD 4200,
    ATI Mobility Radeon 4100, ATI Radeon HD 4290, ATI Radeon HD 4250,
    AMD Radeon HD 6310 Graphics, AMD Radeon HD 6310 Graphics,
    AMD Radeon HD 6250 Graphics, AMD Radeon HD 6250 Graphics,
    AMD Radeon HD 6300 Series Graphics,
    AMD Radeon HD 6200 Series Graphics, PALM, PALM, PALM, CYPRESS,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter, AMD Firestream 9370,
    AMD Firestream 9350, ATI Radeon HD 5800 Series,
    ATI Radeon HD 5800 Series, ATI Radeon HD 5800 Series,
    ATI Radeon HD 5800 Series, ATI Radeon HD 5900 Series,
    ATI Radeon HD 5900 Series, ATI Mobility Radeon HD 5800 Series,
    ATI Mobility Radeon HD 5800 Series,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI Mobility Radeon HD 5800 Series, ATI Radeon HD 5700 Series,
    ATI Radeon HD 5700 Series, ATI Radeon HD 6700 Series,
    ATI Radeon HD 5700 Series, ATI Radeon HD 6700 Series,
    ATI Mobility Radeon HD 5000 Series,
    ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon HD 5570,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter, ATI Radeon HD 5670,
    ATI Radeon HD 5570, ATI Radeon HD 5500 Series, REDWOOD,
    ATI Mobility Radeon HD 5000 Series,
    ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon Graphics,
    ATI Mobility Radeon Graphics, CEDAR,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter, ATI FirePro 2270, CEDAR,
    ATI Radeon HD 5450, CEDAR, CEDAR, CAYMAN, CAYMAN, CAYMAN, CAYMAN,
    CAYMAN, CAYMAN, CAYMAN, CAYMAN, CAYMAN, CAYMAN,
    AMD Radeon HD 6900 Series, AMD Radeon HD 6900 Series, CAYMAN, CAYMAN,
    CAYMAN, AMD Radeon HD 6900M Series, Mobility Radeon HD 6000 Series,
    BARTS, BARTS, Mobility Radeon HD 6000 Series,
    Mobility Radeon HD 6000 Series, BARTS, BARTS, BARTS, BARTS,
    AMD Radeon HD 6800 Series, AMD Radeon HD 6800 Series,
    AMD Radeon HD 6700 Series, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
    TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
    TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
    CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS,
    CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, ARUBA, ARUBA,
    ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA,
    ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA,
    ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA,
    ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, TAHITI, TAHITI, TAHITI, TAHITI,
    TAHITI, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI,
    TAHITI, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN,
    PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN,
    VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE,
    VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE,
    VERDE, VERDE, VERDE, OLAND, OLAND, OLAND, OLAND, OLAND, OLAND, OLAND,
    OLAND, OLAND, OLAND, OLAND, OLAND, OLAND, HAINAN, HAINAN, HAINAN,
    HAINAN, HAINAN, HAINAN, BONAIRE, BONAIRE, BONAIRE, BONAIRE, BONAIRE,
    BONAIRE, BONAIRE, BONAIRE, KABINI, KABINI, KABINI, KABINI, KABINI,
    KABINI, KABINI, KABINI, KABINI, KABINI, KABINI, KABINI, KABINI,
    KABINI, KABINI, KABINI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI,
    KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI,
    KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI, KAVERI,
    HAWAII, HAWAII, HAWAII, HAWAII, HAWAII, HAWAII, HAWAII, HAWAII,
    HAWAII, HAWAII, HAWAII, HAWAII
[    12.765] (II) NOUVEAU driver Date:   Thu Nov 7 14:56:48 2013 +1000
[    12.765] (II) NOUVEAU driver for NVIDIA chipset families :
[    12.765]     RIVA TNT        (NV04)
[    12.765]     RIVA TNT2       (NV05)
[    12.765]     GeForce 256     (NV10)
[    12.765]     GeForce 2       (NV11, NV15)
[    12.765]     GeForce 4MX     (NV17, NV18)
[    12.765]     GeForce 3       (NV20)
[    12.765]     GeForce 4Ti     (NV25, NV28)
[    12.765]     GeForce FX      (NV3x)
[    12.766]     GeForce 6       (NV4x)
[    12.766]     GeForce 7       (G7x)
[    12.766]     GeForce 8       (G8x)
[    12.766]     GeForce GTX 200 (NVA0)
[    12.766]     GeForce GTX 400 (NVC0)
[    12.766] (II) FBDEV: driver for framebuffer: fbdev
[    12.766] (++) using VT number 7

[    12.766] (II) [KMS] Kernel modesetting enabled.
[    12.766] (EE) [drm] KMS not enabled
[    12.766] (EE) [drm] KMS not enabled
[    12.766] (II) Loading sub module "fbdevhw"
[    12.766] (II) LoadModule: "fbdevhw"
[    12.767] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    12.767] (II) Module fbdevhw: vendor="X.Org Foundation"
[    12.767]     compiled for 1.15.1, module version = 0.0.2
[    12.767]     ABI class: X.Org Video Driver, version 15.0
[    12.767] (**) FBDEV(1): claimed PCI slot 8@1:0:0
[    12.767] (II) FBDEV(1): using default device
[    12.767] (II) RADEON(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    12.767] (==) RADEON(0): Depth 24, (--) framebuffer bpp 32
[    12.767] (II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    12.767] (==) RADEON(0): Default visual is TrueColor
[    12.767] (==) RADEON(0): RGB weight 888
[    12.768] (II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
[    12.768] (--) RADEON(0): Chipset: "ATI RV730 PRO [Radeon HD 4650]" (ChipID = 0x9498)
[    12.768] (II) Loading sub module "dri2"
[    12.768] (II) LoadModule: "dri2"
[    12.768] (II) Module "dri2" already built-in
[    12.768] (II) Loading sub module "exa"
[    12.768] (II) LoadModule: "exa"
[    12.768] (II) Loading /usr/lib/xorg/modules/libexa.so
[    12.768] (II) Module exa: vendor="X.Org Foundation"
[    12.768]     compiled for 1.15.1, module version = 2.6.0
[    12.768]     ABI class: X.Org Video Driver, version 15.0
[    12.768] (II) RADEON(0): KMS Color Tiling: enabled
[    12.768] (II) RADEON(0): KMS Color Tiling 2D: enabled
[    12.768] (II) RADEON(0): KMS Pageflipping: enabled
[    12.768] (II) RADEON(0): SwapBuffers wait for vsync: enabled
[    12.792] (II) RADEON(0): Output VGA-0 has no monitor section
[    12.853] (II) RADEON(0): Output HDMI-0 has no monitor section
[    12.877] (II) RADEON(0): Output DVI-0 has no monitor section
[    12.900] (II) RADEON(0): EDID for output VGA-0
[    12.961] (II) RADEON(0): EDID for output HDMI-0
[    12.961] (II) RADEON(0): Manufacturer: GSM  Model: 5a2a  Serial#: 16843009
[    12.961] (II) RADEON(0): Year: 2013  Week: 1
[    12.961] (II) RADEON(0): EDID Version: 1.3
[    12.961] (II) RADEON(0): Digital Display Input
[    12.961] (II) RADEON(0): Max Image Size [cm]: horiz.: 67  vert.: 28
[    12.961] (II) RADEON(0): Gamma: 2.20
[    12.961] (II) RADEON(0): DPMS capabilities: StandBy Suspend Off
[    12.961] (II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    12.961] (II) RADEON(0): First detailed timing is preferred mode
[    12.961] (II) RADEON(0): redX: 0.651 redY: 0.332   greenX: 0.307 greenY: 0.631
[    12.961] (II) RADEON(0): blueX: 0.150 blueY: 0.060   whiteX: 0.313 whiteY: 0.329
[    12.961] (II) RADEON(0): Supported established timings:
[    12.961] (II) RADEON(0): 720x400@70Hz
[    12.961] (II) RADEON(0): 640x480@60Hz
[    12.961] (II) RADEON(0): 640x480@75Hz
[    12.961] (II) RADEON(0): 800x600@60Hz
[    12.961] (II) RADEON(0): 800x600@75Hz
[    12.961] (II) RADEON(0): 1024x768@60Hz
[    12.961] (II) RADEON(0): 1024x768@75Hz
[    12.961] (II) RADEON(0): 1280x1024@75Hz
[    12.961] (II) RADEON(0): 1152x864@75Hz
[    12.961] (II) RADEON(0): Manufacturer's mask: 0
[    12.961] (II) RADEON(0): Supported standard timings:
[    12.961] (II) RADEON(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[    12.961] (II) RADEON(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    12.961] (II) RADEON(0): #2: hsize: 1280  vsize 720  refresh: 60  vid: 49281
[    12.961] (II) RADEON(0): #3: hsize: 1600  vsize 900  refresh: 60  vid: 49321
[    12.961] (II) RADEON(0): #4: hsize: 1680  vsize 1050  refresh: 60  vid: 179
[    12.961] (II) RADEON(0): Supported detailed timing:
[    12.961] (II) RADEON(0): clock: 185.6 MHz   Image Size:  677 x 290 mm
[    12.961] (II) RADEON(0): h_active: 2560  h_sync: 2624  h_sync_end 2688 h_blank_end 2784 h_border: 0
[    12.961] (II) RADEON(0): v_active: 1080  v_sync: 1083  v_sync_end 1093 v_blanking: 1111 v_border: 0
[    12.961] (II) RADEON(0): Supported detailed timing:
[    12.961] (II) RADEON(0): clock: 148.5 MHz   Image Size:  677 x 290 mm
[    12.961] (II) RADEON(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[    12.961] (II) RADEON(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
[    12.961] (II) RADEON(0): Monitor name: LG ULTRAWIDE
[    12.961] (II) RADEON(0): Ranges: V min: 56 V max: 75 Hz, H min: 30 H max: 90 kHz, PixClock max 245 MHz
[    12.961] (II) RADEON(0): Supported detailed timing:
[    12.962] (II) RADEON(0): clock: 148.5 MHz   Image Size:  598 x 337 mm
[    12.962] (II) RADEON(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[    12.962] (II) RADEON(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
[    12.962] (II) RADEON(0): Supported detailed timing:
[    12.962] (II) RADEON(0): clock: 74.2 MHz   Image Size:  598 x 337 mm
[    12.962] (II) RADEON(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[    12.962] (II) RADEON(0): v_active: 540  v_sync: 542  v_sync_end 547 v_blanking: 562 v_border: 0
[    12.962] (II) RADEON(0): Supported detailed timing:
[    12.962] (II) RADEON(0): clock: 74.2 MHz   Image Size:  598 x 337 mm
[    12.962] (II) RADEON(0): h_active: 1280  h_sync: 1390  h_sync_end 1430 h_blank_end 1650 h_border: 0
[    12.962] (II) RADEON(0): v_active: 720  v_sync: 725  v_sync_end 730 v_blanking: 750 v_border: 0
[    12.962] (II) RADEON(0): Supported detailed timing:
[    12.962] (II) RADEON(0): clock: 27.0 MHz   Image Size:  598 x 337 mm
[    12.962] (II) RADEON(0): h_active: 720  h_sync: 736  h_sync_end 798 h_blank_end 858 h_border: 0
[    12.962] (II) RADEON(0): v_active: 480  v_sync: 489  v_sync_end 495 v_blanking: 525 v_border: 0
[    12.962] (II) RADEON(0): Number of EDID sections to follow: 1
[    12.962] (II) RADEON(0): EDID (in hex):
[    12.962] (II) RADEON(0):     00ffffffffffff001e6d2a5a01010101
[    12.962] (II) RADEON(0):     0117010380431c78eaca95a6554ea126
[    12.962] (II) RADEON(0):     0f5054a54b80714f818081c0a9c0b300
[    12.962] (II) RADEON(0):     0101010101017e4800e0a0381f404040
[    12.962] (II) RADEON(0):     3a00a52221000018023a801871382d40
[    12.962] (II) RADEON(0):     582c4500a5222100001e000000fc004c
[    12.962] (II) RADEON(0):     4720554c545241574944450a000000fd
[    12.962] (II) RADEON(0):     00384b1e5a18000a202020202020014b
[    12.962] (II) RADEON(0):     02031df14a900403221412051f011323
[    12.962] (II) RADEON(0):     0907078301000065030c001000023a80
[    12.962] (II) RADEON(0):     1871382d40582c450056512100001e01
[    12.962] (II) RADEON(0):     1d8018711c1620582c25005651210000
[    12.962] (II) RADEON(0):     9e011d007251d01e206e285500565121
[    12.962] (II) RADEON(0):     00001e8c0ad08a20e02d10103e960056
[    12.962] (II) RADEON(0):     51210000180000000000000000000000
[    12.962] (II) RADEON(0):     00000000000000000000000000000078
[    12.962] (II) RADEON(0): Printing probed modes for output HDMI-0
[    12.962] (II) RADEON(0): Modeline "1920x1080"x60.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz e)
[    12.962] (II) RADEON(0): Modeline "1920x1080"x50.0  148.50  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[    12.962] (II) RADEON(0): Modeline "1920x1080"x59.9  148.35  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.4 kHz e)
[    12.962] (II) RADEON(0): Modeline "1920x1080i"x60.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz e)
[    12.962] (II) RADEON(0): Modeline "1920x1080i"x50.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz e)
[    12.962] (II) RADEON(0): Modeline "1920x1080"x30.0   74.25  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (33.8 kHz e)
[    12.963] (II) RADEON(0): Modeline "1920x1080i"x59.9   74.18  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.7 kHz e)
[    12.963] (II) RADEON(0): Modeline "1920x1080"x30.0   74.18  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (33.7 kHz e)
[    12.963] (II) RADEON(0): Modeline "1680x1050"x59.9  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[    12.963] (II) RADEON(0): Modeline "1600x900"x60.0  118.96  1600 1696 1864 2128  900 901 904 932 -hsync +vsync (55.9 kHz)
[    12.963] (II) RADEON(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    12.963] (II) RADEON(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    12.963] (II) RADEON(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    12.963] (II) RADEON(0): Modeline "1280x720"x60.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[    12.963] (II) RADEON(0): Modeline "1280x720"x50.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz e)
[    12.963] (II) RADEON(0): Modeline "1280x720"x59.9   74.18  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[    12.963] (II) RADEON(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz e)
[    12.963] (II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    12.963] (II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    12.963] (II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    12.963] (II) RADEON(0): Modeline "720x576"x50.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz e)
[    12.963] (II) RADEON(0): Modeline "720x480"x60.0   27.03  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[    12.963] (II) RADEON(0): Modeline "720x480"x59.9   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[    12.963] (II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    12.963] (II) RADEON(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    12.963] (II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    12.963] (II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    12.989] (II) RADEON(0): EDID for output DVI-0
[    12.989] (II) RADEON(0): Output VGA-0 disconnected
[    12.989] (II) RADEON(0): Output HDMI-0 connected
[    12.989] (II) RADEON(0): Output DVI-0 disconnected
[    12.989] (II) RADEON(0): Using exact sizes for initial modes
[    12.989] (II) RADEON(0): Output HDMI-0 using initial mode 1152x864
[    12.989] (II) RADEON(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    12.989] (II) RADEON(0): mem size init: gart size :3fdee000 vram size: s:20000000 visible:1f7d7000
[    12.989] (II) RADEON(0): EXA: Driver will allow EXA pixmaps in VRAM
[    12.989] (==) RADEON(0): DPI set to (96, 96)
[    12.989] (II) Loading sub module "fb"
[    12.989] (II) LoadModule: "fb"
[    12.989] (II) Loading /usr/lib/xorg/modules/libfb.so
[    12.990] (II) Module fb: vendor="X.Org Foundation"
[    12.990]     compiled for 1.15.1, module version = 1.0.0
[    12.990]     ABI class: X.Org ANSI C Emulation, version 0.4
[    12.990] (II) Loading sub module "ramdac"
[    12.990] (II) LoadModule: "ramdac"
[    12.990] (II) Module "ramdac" already built-in
[    12.990] (II) FBDEV(1): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    12.990] (==) FBDEV(1): Depth 24, (==) framebuffer bpp 32
[    12.990] (==) FBDEV(1): RGB weight 888
[    12.990] (==) FBDEV(1): Default visual is TrueColor
[    12.990] (==) FBDEV(1): Using gamma correction (1.0, 1.0, 1.0)
[    12.990] (II) FBDEV(1): hardware: radeondrmfb (video memory: 8100kB)
[    12.990] (II) FBDEV(1): checking modes against framebuffer device...
[    12.990] (II) FBDEV(1): checking modes against monitor...
[    12.990] (--) FBDEV(1): Virtual size is 1920x1080 (pitch 1920)
[    12.990] (**) FBDEV(1):  Built-in mode "current"
[    12.990] (==) FBDEV(1): DPI set to (96, 96)
[    12.990] (II) Loading sub module "fb"
[    12.990] (II) LoadModule: "fb"
[    12.990] (II) Loading /usr/lib/xorg/modules/libfb.so
[    12.990] (II) Module fb: vendor="X.Org Foundation"
[    12.990]     compiled for 1.15.1, module version = 1.0.0
[    12.990]     ABI class: X.Org ANSI C Emulation, version 0.4
[    12.990] (**) FBDEV(1): using shadow framebuffer
[    12.990] (II) Loading sub module "shadow"
[    12.991] (II) LoadModule: "shadow"
[    12.991] (II) Loading /usr/lib/xorg/modules/libshadow.so
[    12.994] (II) Module shadow: vendor="X.Org Foundation"
[    12.995]     compiled for 1.15.1, module version = 1.1.0
[    12.995]     ABI class: X.Org ANSI C Emulation, version 0.4
[    12.995] (--) Depth 24 pixmap format is 32 bpp
[    12.995] (II) RADEON(0): [DRI2] Setup complete
[    12.995] (II) RADEON(0): [DRI2]   DRI driver: r600
[    12.995] (II) RADEON(0): [DRI2]   VDPAU driver: r600
[    12.995] (II) RADEON(0): Front buffer size: 3888K
[    12.995] (II) RADEON(0): VRAM usage limit set to 460810K
[    12.995] (==) RADEON(0): Backing store enabled
[    12.995] (II) RADEON(0): Direct rendering enabled
[    12.995] (II) EXA(0): Driver allocated offscreen pixmaps
[    12.995] (II) EXA(0): Driver registered support for the following operations:
[    12.995] (II)         Solid
[    12.995] (II)         Copy
[    12.995] (II)         Composite (RENDER acceleration)
[    12.995] (II)         UploadToScreen
[    12.996] (II)         DownloadFromScreen
[    12.996] (II) RADEON(0): Acceleration enabled
[    12.996] (==) RADEON(0): DPMS enabled
[    12.996] (==) RADEON(0): Silken mouse enabled
[    12.996] (II) RADEON(0): Set up textured video
[    12.996] (II) RADEON(0): [XvMC] Associated with Radeon Textured Video.
[    12.996] (II) RADEON(0): [XvMC] Extension initialized.
[    12.996] (II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    13.015] (--) RandR disabled
[    13.015] (==) FBDEV(1): Backing store enabled
[    13.015] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.016] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.016] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.016] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.016] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.016] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.016] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.016] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.016] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.016] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.016] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.016] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.016] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.016] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.016] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.016] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.016] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.016] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.016] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.016] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.016] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.016] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.016] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.016] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.016] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.016] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.016] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.016] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.016] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.016] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.016] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.016] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.016] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.016] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.016] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.016] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.016] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.016] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.016] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.016] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.016] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.016] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.016] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.016] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.016] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.016] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.017] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.017] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.017] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.017] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.017] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.017] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.017] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.017] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.017] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.017] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.017] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.017] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.017] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.017] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.017] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.017] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.017] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.017] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.017] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.017] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.017] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.017] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.017] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.017] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.017] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.017] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.017] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.017] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.017] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.017] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.017] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.017] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.017] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.017] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.017] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.017] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.017] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.017] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.017] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.017] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.017] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.017] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.017] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.017] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.017] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.017] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.018] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.018] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.018] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.018] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.018] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.018] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.018] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.018] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.018] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.018] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.018] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.018] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.018] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.018] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.018] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.018] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.018] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.018] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.018] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.018] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.018] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.018] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.018] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.018] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.018] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.018] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.018] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.018] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.018] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.018] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.018] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.018] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.018] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.018] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.018] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.018] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.018] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.018] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.018] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.018] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.018] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.018] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.018] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.018] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.018] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.018] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.018] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.018] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.019] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.019] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.019] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.019] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.019] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.019] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.019] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.019] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.019] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.019] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.019] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.019] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.019] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.019] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.019] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.019] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.019] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.019] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.019] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.019] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.019] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.019] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.019] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.019] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.019] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.019] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.019] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.019] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.019] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.019] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.019] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.019] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.019] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.019] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.019] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.019] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.019] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.019] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.019] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.019] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.019] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.019] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.019] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.019] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.019] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.019] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.019] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.020] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.020] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.020] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.020] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.020] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.020] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.020] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.020] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.020] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.020] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.020] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.020] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.020] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.020] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.020] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.020] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.020] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.020] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.020] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.020] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.020] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.020] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.020] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.020] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.020] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.020] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.020] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.020] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.020] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.020] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.020] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.020] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.020] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.020] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.020] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.020] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.020] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.020] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.020] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.020] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.020] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.020] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.020] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.020] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.020] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.020] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.020] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.021] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.021] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.021] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.021] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.021] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.021] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.021] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.021] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.021] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.021] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.021] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.021] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.021] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.021] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.021] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.021] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.021] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.021] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.021] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.021] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.021] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.021] (EE) FBDEV(1): FBIOPUTCMAP: Device or resource busy
[    13.021] (==) FBDEV(1): DPMS enabled
[    13.021] (--) RandR disabled
[    13.043] (II) SELinux: Disabled on system
[    13.146] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    13.146] (II) AIGLX: enabled GLX_ARB_create_context
[    13.146] (II) AIGLX: enabled GLX_ARB_create_context_profile
[    13.146] (II) AIGLX: enabled GLX_EXT_create_context_es2_profile
[    13.146] (II) AIGLX: enabled GLX_INTEL_swap_event
[    13.146] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    13.146] (II) AIGLX: enabled GLX_EXT_framebuffer_sRGB
[    13.146] (II) AIGLX: enabled GLX_ARB_fbconfig_float
[    13.146] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    13.149] (II) AIGLX: Loaded and initialized r600
[    13.149] (II) GLX: Initialized DRI2 GL provider for screen 0
[    13.149] (II) AIGLX: Screen 1 is not DRI2 capable
[    13.149] (EE) AIGLX: reverting to software rendering
[    13.202] (II) AIGLX: Loaded and initialized swrast
[    13.202] (II) GLX: Initialized DRISWRAST GL provider for screen 1
[    13.265] (II) RADEON(0): Setting screen physical size to 304 x 228
[    13.306] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    13.311] (II) config/udev: Adding drm device (/dev/dri/card0) card0 /sys/devices/pci0000:00/0000:00:0b.0/0000:0a:00.0/drm/card0
[    13.312] (II) config/udev: Ignoring already known drm device (/dev/dri/card0)
[    13.312] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=3 (/dev/input/event5)
[    13.312] (II) No input driver specified, ignoring this device.
[    13.312] (II) This device may have been added with another device file.
[    13.313] (II) config/udev: Adding input device Mitsumi Electric Apple Extended USB Keyboard (/dev/input/event3)
[    13.313] (**) Mitsumi Electric Apple Extended USB Keyboard: Applying InputClass "evdev keyboard catchall"
[    13.313] (II) LoadModule: "evdev"
[    13.314] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    13.315] (II) Module evdev: vendor="X.Org Foundation"
[    13.315]     compiled for 1.15.0, module version = 2.8.2
[    13.315]     Module class: X.Org XInput Driver
[    13.315]     ABI class: X.Org XInput driver, version 20.0
[    13.315] (II) Using input driver 'evdev' for 'Mitsumi Electric Apple Extended USB Keyboard'
[    13.315] (**) Mitsumi Electric Apple Extended USB Keyboard: always reports core events
[    13.315] (**) evdev: Mitsumi Electric Apple Extended USB Keyboard: Device: "/dev/input/event3"
[    13.315] (--) evdev: Mitsumi Electric Apple Extended USB Keyboard: Vendor 0x5ac Product 0x20c
[    13.315] (--) evdev: Mitsumi Electric Apple Extended USB Keyboard: Found keys
[    13.315] (II) evdev: Mitsumi Electric Apple Extended USB Keyboard: Configuring as keyboard
[    13.315] (**) Option "config_info" "udev:/sys/devices/pci0001:00/0001:00:08.0/0001:01:0b.0/usb2/2-1/2-1.3/2-1.3:1.0/input/input3/event3"
[    13.315] (II) XINPUT: Adding extended input device "Mitsumi Electric Apple Extended USB Keyboard" (type: KEYBOARD, id 6)
[    13.315] (**) Option "xkb_rules" "evdev"
[    13.315] (**) Option "xkb_model" "pc105"
[    13.316] (**) Option "xkb_layout" "it"
[    13.327] (II) XKB: reuse xkmfile /var/lib/xkb/server-3781FECB9CB8D26EE03343DB2C93394EA704B98F.xkm
[    13.329] (II) config/udev: Adding input device Mitsumi Electric Apple Extended USB Keyboard (/dev/input/event4)
[    13.329] (**) Mitsumi Electric Apple Extended USB Keyboard: Applying InputClass "evdev keyboard catchall"
[    13.329] (II) Using input driver 'evdev' for 'Mitsumi Electric Apple Extended USB Keyboard'
[    13.329] (**) Mitsumi Electric Apple Extended USB Keyboard: always reports core events
[    13.330] (**) evdev: Mitsumi Electric Apple Extended USB Keyboard: Device: "/dev/input/event4"
[    13.330] (--) evdev: Mitsumi Electric Apple Extended USB Keyboard: Vendor 0x5ac Product 0x20c
[    13.330] (--) evdev: Mitsumi Electric Apple Extended USB Keyboard: Found keys
[    13.330] (II) evdev: Mitsumi Electric Apple Extended USB Keyboard: Configuring as keyboard
[    13.330] (**) Option "config_info" "udev:/sys/devices/pci0001:00/0001:00:08.0/0001:01:0b.0/usb2/2-1/2-1.3/2-1.3:1.1/input/input4/event4"
[    13.330] (II) XINPUT: Adding extended input device "Mitsumi Electric Apple Extended USB Keyboard" (type: KEYBOARD, id 7)
[    13.330] (**) Option "xkb_rules" "evdev"
[    13.330] (**) Option "xkb_model" "pc105"
[    13.330] (**) Option "xkb_layout" "it"
[    13.331] (II) config/udev: Adding input device KOSEL KSL81P304 (/dev/input/event0)
[    13.331] (**) KOSEL KSL81P304: Applying InputClass "evdev pointer catchall"
[    13.331] (II) Using input driver 'evdev' for 'KOSEL KSL81P304'
[    13.331] (**) KOSEL KSL81P304: always reports core events
[    13.331] (**) evdev: KOSEL KSL81P304: Device: "/dev/input/event0"
[    13.331] (--) evdev: KOSEL KSL81P304: Vendor 0x2571 Product 0x4101
[    13.331] (--) evdev: KOSEL KSL81P304: Found 9 mouse buttons
[    13.331] (--) evdev: KOSEL KSL81P304: Found scroll wheel(s)
[    13.331] (--) evdev: KOSEL KSL81P304: Found relative axes
[    13.331] (--) evdev: KOSEL KSL81P304: Found x and y relative axes
[    13.331] (II) evdev: KOSEL KSL81P304: Configuring as mouse
[    13.331] (II) evdev: KOSEL KSL81P304: Adding scrollwheel support
[    13.331] (**) evdev: KOSEL KSL81P304: YAxisMapping: buttons 4 and 5
[    13.331] (**) evdev: KOSEL KSL81P304: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    13.331] (**) Option "config_info" "udev:/sys/devices/pci0001:00/0001:00:08.0/0001:01:0b.0/usb2/2-2/2-2:1.1/input/input0/event0"
[    13.331] (II) XINPUT: Adding extended input device "KOSEL KSL81P304" (type: MOUSE, id 8)
[    13.331] (II) evdev: KOSEL KSL81P304: initialized for relative axes.
[    13.332] (**) KOSEL KSL81P304: (accel) keeping acceleration scheme 1
[    13.332] (**) KOSEL KSL81P304: (accel) acceleration profile 0
[    13.332] (**) KOSEL KSL81P304: (accel) acceleration factor: 2.000
[    13.332] (**) KOSEL KSL81P304: (accel) acceleration threshold: 4
[    13.332] (II) config/udev: Adding input device KOSEL KSL81P304 (/dev/input/mouse0)
[    13.332] (II) No input driver specified, ignoring this device.
[    13.332] (II) This device may have been added with another device file.
[    13.336] (II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/event6)
[    13.336] (**) Macintosh mouse button emulation: Applying InputClass "evdev pointer catchall"
[    13.336] (II) Using input driver 'evdev' for 'Macintosh mouse button emulation'
[    13.336] (**) Macintosh mouse button emulation: always reports core events
[    13.336] (**) evdev: Macintosh mouse button emulation: Device: "/dev/input/event6"
[    13.336] (--) evdev: Macintosh mouse button emulation: Vendor 0x1 Product 0x1
[    13.336] (--) evdev: Macintosh mouse button emulation: Found 3 mouse buttons
[    13.336] (--) evdev: Macintosh mouse button emulation: Found relative axes
[    13.336] (--) evdev: Macintosh mouse button emulation: Found x and y relative axes
[    13.336] (II) evdev: Macintosh mouse button emulation: Configuring as mouse
[    13.336] (**) evdev: Macintosh mouse button emulation: YAxisMapping: buttons 4 and 5
[    13.336] (**) evdev: Macintosh mouse button emulation: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    13.336] (**) Option "config_info" "udev:/sys/devices/virtual/input/input6/event6"
[    13.336] (II) XINPUT: Adding extended input device "Macintosh mouse button emulation" (type: MOUSE, id 9)
[    13.336] (II) evdev: Macintosh mouse button emulation: initialized for relative axes.
[    13.337] (**) Macintosh mouse button emulation: (accel) keeping acceleration scheme 1
[    13.337] (**) Macintosh mouse button emulation: (accel) acceleration profile 0
[    13.337] (**) Macintosh mouse button emulation: (accel) acceleration factor: 2.000
[    13.337] (**) Macintosh mouse button emulation: (accel) acceleration threshold: 4
[    13.337] (II) config/udev: Adding input device Macintosh mouse button emulation (/dev/input/mouse2)
[    13.337] (II) No input driver specified, ignoring this device.
[    13.337] (II) This device may have been added with another device file.
[    28.812] (II) RADEON(0): EDID vendor "GSM", prod id 23082
[    28.812] (II) RADEON(0): Using EDID range info for horizontal sync
[    28.812] (II) RADEON(0): Using EDID range info for vertical refresh
[    28.812] (II) RADEON(0): Printing DDC gathered Modelines:
[    28.812] (II) RADEON(0): Modeline "2560x1080"x0.0  185.58  2560 2624 2688 2784  1080 1083 1093 1111 -hsync -vsync (66.7 kHz eP)
[    28.812] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz e)
[    28.812] (II) RADEON(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz e)
[    28.812] (II) RADEON(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[    28.812] (II) RADEON(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[    28.812] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    28.812] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    28.812] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    28.812] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    28.812] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    28.812] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    28.812] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    28.812] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    28.812] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    28.813] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    28.813] (II) RADEON(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz e)
[    28.813] (II) RADEON(0): Modeline "1600x900"x60.0  119.00  1600 1696 1864 2128  900 901 904 932 -hsync +vsync (55.9 kHz e)
[    28.813] (II) RADEON(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[    28.813] (II) RADEON(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz e)
[    28.813] (II) RADEON(0): Modeline "2880x480"x0.0  108.00  2880 2944 3192 3432  480 489 495 525 -hsync -vsync (31.5 kHz e)
[    28.813] (II) RADEON(0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz e)
[    28.813] (II) RADEON(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz e)
[    28.813] (II) RADEON(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz e)
[    28.813] (II) RADEON(0): Modeline "1920x1080"x0.0   74.25  1920 2558 2602 2750  1080 1084 1089 1125 +hsync +vsync (27.0 kHz e)
[    28.927] (II) RADEON(0): EDID vendor "GSM", prod id 23082
[    28.928] (II) RADEON(0): Using hsync ranges from config file
[    28.928] (II) RADEON(0): Using vrefresh ranges from config file
[    28.928] (II) RADEON(0): Printing DDC gathered Modelines:
[    28.928] (II) RADEON(0): Modeline "2560x1080"x0.0  185.58  2560 2624 2688 2784  1080 1083 1093 1111 -hsync -vsync (66.7 kHz eP)
[    28.928] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz e)
[    28.928] (II) RADEON(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz e)
[    28.928] (II) RADEON(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[    28.928] (II) RADEON(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[    28.928] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    28.928] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    28.928] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    28.928] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    28.928] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    28.928] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    28.928] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    28.928] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    28.928] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    28.928] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    28.928] (II) RADEON(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz e)
[    28.928] (II) RADEON(0): Modeline "1600x900"x60.0  119.00  1600 1696 1864 2128  900 901 904 932 -hsync +vsync (55.9 kHz e)
[    28.928] (II) RADEON(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[    28.928] (II) RADEON(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz e)
[    28.928] (II) RADEON(0): Modeline "2880x480"x0.0  108.00  2880 2944 3192 3432  480 489 495 525 -hsync -vsync (31.5 kHz e)
[    28.928] (II) RADEON(0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz e)
[    28.928] (II) RADEON(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz e)
[    28.928] (II) RADEON(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz e)
[    28.928] (II) RADEON(0): Modeline "1920x1080"x0.0   74.25  1920 2558 2602 2750  1080 1084 1089 1125 +hsync +vsync (27.0 kHz e)
[    29.063] (II) RADEON(0): EDID vendor "GSM", prod id 23082
[    29.063] (II) RADEON(0): Using hsync ranges from config file
[    29.063] (II) RADEON(0): Using vrefresh ranges from config file
[    29.063] (II) RADEON(0): Printing DDC gathered Modelines:
[    29.063] (II) RADEON(0): Modeline "2560x1080"x0.0  185.58  2560 2624 2688 2784  1080 1083 1093 1111 -hsync -vsync (66.7 kHz eP)
[    29.063] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz e)
[    29.063] (II) RADEON(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz e)
[    29.063] (II) RADEON(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[    29.063] (II) RADEON(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[    29.063] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    29.063] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    29.063] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    29.063] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    29.063] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    29.063] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    29.063] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    29.063] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    29.063] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    29.063] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    29.063] (II) RADEON(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz e)
[    29.063] (II) RADEON(0): Modeline "1600x900"x60.0  119.00  1600 1696 1864 2128  900 901 904 932 -hsync +vsync (55.9 kHz e)
[    29.063] (II) RADEON(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[    29.063] (II) RADEON(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz e)
[    29.063] (II) RADEON(0): Modeline "2880x480"x0.0  108.00  2880 2944 3192 3432  480 489 495 525 -hsync -vsync (31.5 kHz e)
[    29.063] (II) RADEON(0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz e)
[    29.063] (II) RADEON(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz e)
[    29.064] (II) RADEON(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz e)
[    29.064] (II) RADEON(0): Modeline "1920x1080"x0.0   74.25  1920 2558 2602 2750  1080 1084 1089 1125 +hsync +vsync (27.0 kHz e)
[    29.116] (II) RADEON(0): Allocate new frame buffer 1920x1088 stride 1920
[    29.116] (II) RADEON(0): VRAM usage limit set to 456966K
[    29.914] (II) RADEON(0): EDID vendor "GSM", prod id 23082
[    29.914] (II) RADEON(0): Using hsync ranges from config file
[    29.914] (II) RADEON(0): Using vrefresh ranges from config file
[    29.914] (II) RADEON(0): Printing DDC gathered Modelines:
[    29.914] (II) RADEON(0): Modeline "2560x1080"x0.0  185.58  2560 2624 2688 2784  1080 1083 1093 1111 -hsync -vsync (66.7 kHz eP)
[    29.914] (II) RADEON(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz e)
[    29.915] (II) RADEON(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz e)
[    29.915] (II) RADEON(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[    29.915] (II) RADEON(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[    29.915] (II) RADEON(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    29.915] (II) RADEON(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    29.915] (II) RADEON(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    29.915] (II) RADEON(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    29.915] (II) RADEON(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[    29.915] (II) RADEON(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    29.915] (II) RADEON(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    29.915] (II) RADEON(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    29.915] (II) RADEON(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[    29.915] (II) RADEON(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    29.915] (II) RADEON(0): Modeline "1280x720"x60.0   74.48  1280 1336 1472 1664  720 721 724 746 -hsync +vsync (44.8 kHz e)
[    29.915] (II) RADEON(0): Modeline "1600x900"x60.0  119.00  1600 1696 1864 2128  900 901 904 932 -hsync +vsync (55.9 kHz e)
[    29.915] (II) RADEON(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[    29.915] (II) RADEON(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz e)
[    29.915] (II) RADEON(0): Modeline "2880x480"x0.0  108.00  2880 2944 3192 3432  480 489 495 525 -hsync -vsync (31.5 kHz e)
[    29.915] (II) RADEON(0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz e)
[    29.915] (II) RADEON(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz e)
[    29.915] (II) RADEON(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz e)
[    29.915] (II) RADEON(0): Modeline "1920x1080"x0.0   74.25  1920 2558 2602 2750  1080 1084 1089 1125 +hsync +vsync (27.0 kHz e)


```

---

### Post by Dukenukemx on 2015-02-06
> **luigiburdo said:**
> 
```
[/FONT][/COLOR][COLOR=#404040][FONT=Roboto]On G5 with radeon try to install with this line
 "live video=radeonfb:off radeon.modeset=1 radeon.agpmode=-1" 
if you have issiues do
[/FONT][/COLOR][COLOR=#404040][FONT=Roboto]"live video=radeonfb:off radeon.modeset=1 radeon.agpmode=-1 video=offb:off"[/FONT][/COLOR][COLOR=#404040][FONT=Roboto]
```

hope it work for you ;)[/FONT][/COLOR]

Tried that and get " Error: couldn't find RGB GLX visual or fbconfig".  BTW I tried on both the G5 and the PowerBook G4 with no success.  The "video=ofonly" does seem to get 3D started but glxgears still freezes the machine.

---

### Post by luigiburdo on 2015-02-07
exactly what video board do you have on g5 ? nvidia or ati?

---

### Post by rsavage on 2015-02-07
Luigiburdo, why do you disable nouveau?  What does the xorg log look like when you remove the nouveau parameters?

---

### Post by luigiburdo on 2015-02-07
if i dont disable the nouveau i dont have video on radeonhd.
and if i use the 7800gtx the graphic is glitched and not usable.
The 7800gtx is only compatible with debian wheezy right now .
i try all the way but the only road is disable nouveau for have mate running on my configuration

---

### Post by rsavage on 2015-02-07
Luigiburdo, what happens if you remove the xserver-xorg-video-fbdev package and reboot?

---

### Post by luigiburdo on 2015-02-07
will check rsavage and report.

Today i found really big updares on sys updater ... a new xorg version. and the performance on radeonhd are much more better... about 4x compared before on fishblow htlm5 browser test. 

There is a big problem with Radeon:kernel and css/js ... system freeze during some procedures of firefox

---

### Post by luigiburdo on 2015-02-07
> **rsavage said:**
> Luigiburdo, what happens if you remove the xserver-xorg-video-fbdev package and reboot?

I think is better dont remove it 

```
  
sudo aptitude remove xserver-xorg-video-fbdev
The following packages will be REMOVED:   
  xserver-xorg-video-fbdev 
0 packages upgraded, 0 newly installed, 1 to remove and 3 not upgraded.
Need to get 0 B of archives. After unpacking 86,0 kB will be freed.
The following packages have unmet dependencies:
 xserver-xorg-video-all : Dipende: xserver-xorg-video-fbdev but it is not going to be installed.
The following actions will resolve these dependencies:

     Remove the following packages:
1)     ubuntu-mate-core            
2)     xserver-xorg-video-all      



Accept this solution? [Y/n/q/?] q
Abandoning all efforts to resolve these dependencies.
Abort.


```

---

### Post by rsavage on 2015-02-07
They're just meta packages and can be safely removed.

---

### Post by luigiburdo on 2015-02-07
ok will try ... lets hope

---

### Post by luigiburdo on 2015-02-07
IT WORK!... Finally yea! guys ... soon i will made a new video: Ubuntu Mate Running on Quad G5 with RadeonHD ! :-)

need only one tips more... i need to upgrade the kernel with 3.18 or up because is my intention try to see if the 6570HD can work in G5 too
I had been try do download it and upgrade like i did dozen of times on debian ... but it failed .
gcc exit with errors ... some tips about?

Edit: i had been found a big issue here with firefox ... it in some situation freeze totally the Os and i have to hard reset the machine.

radeon: The kernel rejected CS, see dmesg for more information.
dmesg | grep radeon 
> [  582.809081] [drm:radeon_cs_ib_chunk] *ERROR* Failed to schedule IB !
[  582.812608] radeon 0001:06:00.0: scheduling IB failed (-2).
[  582.812616] [drm:radeon_cs_ib_chunk] *ERROR* Failed to schedule IB !
[  582.830120] radeon 0001:06:00.0: scheduling IB failed (-2).
[  582.830126] [drm:radeon_cs_ib_chunk] *ERROR* Failed to schedule IB !


---

### Post by luigiburdo on 2015-02-08
Edit  did it ... Thanks to Xeno74 for Ubuntu Tips:) 
... now is time to check for issue :P

[IMG]https://scontent-a-mxp.xx.fbcdn.net/hphotos-xpf1/v/t1.0-9/16823_10203541749565947_7246581259099829186_n.jpg?oh=8df0fc488b68e84ffa4826ea3f216b7c&oe=5568355C[/IMG]

---

### Post by luigiburdo on 2015-02-08
The issue of crashing firefox is been fixed with the new kernel :-)
Now only thing to understand is what i need to enable in kernel of have the audio again on radeonhd working... 
in any way guys check here :)


[IMG]https://fbcdn-sphotos-g-a.akamaihd.net/hphotos-ak-xfp1/v/t1.0-9/10527783_10203541904409818_1528268267978557543_n.jpg?oh=5c9129f7fb1a21a7f664197f04040b81&oe=5567FFEC&__gda__=1431477897_d17bac225d17283757efa9ea100bfadb[/IMG]

---

### Post by luigiburdo on 2015-02-08
i had been test the 6570 and :-( the old issue with fonts found in lubuntu 14.04 is present here too. [http://ubuntuforums.org/showthread.php?t=2221421&page=5](http://ubuntuforums.org/showthread.php?t=2221421&page=5)
I reswap with the 4650.

---

### Post by Dukenukemx on 2015-02-08
> **luigiburdo said:**
> exactly what video board do you have on g5 ? nvidia or ati?

It's a ATI Radeon 9600 I believe.  
> **luigiburdo said:**
> Edit  did it ... Thanks to Xeno74 for Ubuntu Tips:) 
... now is time to check for issue :P

[IMG]https://scontent-a-mxp.xx.fbcdn.net/hphotos-xpf1/v/t1.0-9/16823_10203541749565947_7246581259099829186_n.jpg?oh=8df0fc488b68e84ffa4826ea3f216b7c&oe=5568355C[/IMG]
Can you give me a copy of that kernel?  :)

---

### Post by luigiburdo on 2015-02-08
Here is for who need  ;-)

[https://www.dropbox.com/s/r35bj5j6361wffr/kernel-3.19_rc7_g5.zip?dl=0](https://www.dropbox.com/s/r35bj5j6361wffr/kernel-3.19_rc7_g5.zip?dl=0)

next days i will made a better kernel configuration.
more compatible with radeonhd boards :-)
right now with this one i can say for sure everything in 2D is much much faster compared before and really stable compared the 3.13 with my configuration.

---

### Post by wrenhal on 2015-02-11
Is there a text based way to run the installer on UbuntuMate Live CD??  The graphical install keeps freezing.  Any ideas?

---

### Post by luigiburdo on 2015-02-11
What machine do you have there ? 
can you write your configuration please ... i think will help all us to gave the right tips to you

---

### Post by wrenhal on 2015-02-11
> **luigiburdo said:**
> What machine do you have there ? 
can you write your configuration please ... i think will help all us to gave the right tips to you
I'm the guy from Google+ the other day with the iMac G5 iSight.  Radeon x600 Pro PCIExpress.
I can boot to a 32bit desktop now from the Live CD but the graphical installer freezes.
Here's the yaboot that lets me in
live-powerpc64 nomodeset video=radeonfb:1440x900M-32
I also tried adding radeon.agpmode=-1 to see if that would help the freezing and it didn't.

---

### Post by rican-linux on 2015-02-11
when you try```
 radeon.agpmode=-1
``` also try this ```
video=radeonfb:off
```

---

### Post by luigiburdo on 2015-02-11
Ok wrenhal :P

dont use live-poweroc64 isnt needed ... just live is ok ;)
radeon.agpmode isnt needed because is pcie not pci or agp .

Ok lets work ! ... try it

```

live video=offb:off radeon.modeset=1 video=radeonfb:off 
do not insert 1440x900
radeonfb is for really old cards your is a drm ,glx , dri2 capable  
 
if the first dont work... then try
live video=radeonfb:off radeon.modeset=1

if you see something dont work ... graphic glitched or instability  then put radeon.agpmode=-1 on the two config that i had been write before.
on minig4 it was help system stability


```

---

### Post by wrenhal on 2015-02-11
> **luigiburdo said:**
> Ok wrenhal :P

dont use live-poweroc64 isnt needed ... just live is ok ;)
radeon.agpmode isnt needed because is pcie not pci or agp .

Ok lets work ! ... try it

But mine is a 64-bt processor and I don't think it boots all the way without it.  I haven't tried just live since about 4 days ago... tried a lot of things since then.
The agpmode was something I was trying to stop the freezing because someone else had mentioned random freezing and it fixed it.

> 

```

live video=offb:off radeon.modeset=1 video=radeonfb:off 
do not insert 1440x900
radeonfb is for really old cards your is a drm ,glx , dri2 capable  
 
if the first dont work... then try
live video=radeonfb:off radeon.modeset=1

if you see something dont work ... graphic glitched or instability  then put radeon.agpmode=-1 on the two config that i had been write before.
on minig4 it was help system stability


```
Pretty much if I don't specify the radeonfb:1440x900M-32 I get the 8-bit desktop...  I'll try some of these again. and get back to you.

---

### Post by luigiburdo on 2015-02-12
dont worry about the live it will open the ppc64 kernel without forcing it, i use it alone with my quad without problems.will be really strange if you will not get the video on x800 without the radeonfb it will mean that the kernel on mate will need to upgraded to a newer version from the installation cd

---

### Post by luigiburdo on 2015-02-13
Umm ... i had been build the qemu everything was build right but after run on executable ... i have a core dump with a strange error...
example qemu-system-ppc -to (???) 
i think i will reinstall mate probably some trusty update or gcc 4.8.2 is making this issue on my system

---

### Post by luigiburdo on 2015-02-14
i dont understand i make a clean installation of the system but the error continue be there... 
after doing the build of pakage for the kernel it stop with the ld -T error when arch/powerpc/boot/zImage.pmac start

---

### Post by luigiburdo on 2015-02-14
One picture speak more than 10000 words ;)


[IMG]https://scontent-mxp.xx.fbcdn.net/hphotos-xfp1/v/t1.0-9/11002497_10203582236498095_7117913185123404835_n.jpg?oh=0f391ab0e7b9729699cff98f6cd3e90d&oe=555DABAD[/IMG]

---

### Post by luigiburdo on 2015-02-16
Loose the two last days try to build the 3.19rc7 and 3.19 kernel but nothing to do ... same LD error as before on the Modules of kernel.
I had been try use the standard g5 kernel configuration in kernel pagage /arch but without success ...
I dont know from where this issue come and how to fix it ... 
I had been try to reinstall mate from beginning and nothing 
Change the gcc from the 4.8.2 to 4.6.4 nothing too
i m really lost ... the strange thing is that i was able to build before without problems...


Edit : 
scripts/kconfig/lxdialog/menubox.c: In function ‘dialog_menu’:
scripts/kconfig/lxdialog/menubox.c:184:5: internal compiler error: Errore di segmentazione
 int dialog_menu(const char *title, const char *prompt,
     ^
Please submit a full bug report,
with preprocessed source if appropriate.
See <file:///usr/share/doc/gcc-4.8/README.Bugs> for instructions.
The bug is not reproducible, so it is likely a hardware or OS problem.
make[1]: *** [scripts/kconfig/lxdialog/menubox.o] Errore 1
make: *** [menuconfig] Errore 2

... im sure is not an hardware problem :( :(

---

### Post by eastone on 2015-02-18
Hi there,
I'm trying to install MATE on PM G5 2.3GHz, GF 6600 256MB and 2GB of RAM.
Unfortunately when booting I'm getting picture only on right quarter of the screen. I can get a full screen picture only with nouveau.modeset=0 but with psychedelic colours.
Does anyone have any suggestions?

---

### Post by luigiburdo on 2015-02-18
try 
```

live video=offb:off video=nouveaufb:off nouveau.modeset=1
or

live video=nouveaufb:off nouveau.modeset=1


```

Im try to build a new kernel without success .. the lastest kernel have better Nvidia and RadeonHD support .

---

### Post by eastone on 2015-02-19
@luigi
No luck :( 
Still the same problem.

---

### Post by luigiburdo on 2015-02-19
Umm ... can you try to add nouveau.dpm=1 to the two lines that i had been had on before post...
It is  really strange because the 6600 is really supported ...
ah i forget if you are using the 6600 in agp you need to add the 
nouveau.agpmode= (-1 or 0 or 1 or 2 or 4)
Sorry i have an pcie powermac and can help more than :(

---

### Post by luigiburdo on 2015-02-21
Im running Ubuntu Mate with Kernel 4.00 (3.20) on quad g5 finally.
soon i will share it if some one will need

---

### Post by xeno74 on 2015-02-22
> **luigiburdo said:**
> Im running Ubuntu Mate with Kernel 4.00 (3.20) on quad g5 finally.
soon i will share it if some one will need

This is fantastic!

---

### Post by luigiburdo on 2015-03-07
Some friend ask a small info about the speed of mate on Quad G5 . This is a small video about.
soon i will try to find some free time for make the full desktop video experience... enjoy

[https://www.youtube.com/watch?v=NyShy_ey7Ds&list=UUkb4bw4N19d-x_tn2FXLojQ](https://www.youtube.com/watch?v=NyShy_ey7Ds&list=UUkb4bw4N19d-x_tn2FXLojQ)

---

### Post by luigiburdo on 2015-03-08
Christian this is for you 

Check the kernel :-)

[IMG]http://i1249.photobucket.com/albums/hh511/tlosm/Schermata_zpssuyrkxwp.jpg[/IMG]



Half life is running under Qemu  and i can play :)

[IMG]http://i1249.photobucket.com/albums/hh511/tlosm/Schermata-1_zpsfcsyukwl.png[/IMG]

---

### Post by xeno74 on 2015-03-08
> **luigiburdo said:**
> Christian this is for you 

Check the kernel :-)

[IMG]http://i1249.photobucket.com/albums/hh511/tlosm/Schermata_zpssuyrkxwp.jpg[/IMG]



Half life is running under Qemu  and i can play :)

[IMG]http://i1249.photobucket.com/albums/hh511/tlosm/Schermata-1_zpsfcsyukwl.png[/IMG]

Fantastic! Thank you!

---

### Post by este.el.paz on 2015-03-08
> **luigiburdo said:**
> Some friend ask a small info about the speed of mate on Quad G5 . This is a small video about.
soon i will try to find some free time for make the full desktop video experience... enjoy

[https://www.youtube.com/watch?v=NyShy_ey7Ds&list=UUkb4bw4N19d-x_tn2FXLojQ](https://www.youtube.com/watch?v=NyShy_ey7Ds&list=UUkb4bw4N19d-x_tn2FXLojQ)

@LB:

I watched yr video on my old G4 Sawtoothe in OSX . . . which wasn't exactly smooth on my slow DSL line, so it wasn't clear what you were trying to show . . . but, I think you are on to something with the soundtrack . . . in terms of conveying the "power" and "excitement" of U-MATE . . . .  It would be over the top if you could work that soundtrack into the MATE kernel, so that it would be playing while the users would be doing their mundane computer tasks . . . it would be the new muzak . . . constant background techno-ambient sound which could be programmed to adjust to the activities that were being worked on by the computer!!!!!  : - ))))  I'm now interested in sound, since I finally got the sound working on my iBook running U-MATE . . . new update/upgrade I'm going to be looking for a ppa with your soundtrack . . . help me plz. 

e.e.p.

---

### Post by luigiburdo on 2015-03-09
hi este. 
The video show of much is fast Mate booting on Quad G5 exactly 3x compared Debian and 5x compared OsX Leopard  but the most important think of the video is have the RadeonHD working on Quad without a Apple firmware ;)
About audio do you had been check if the sound drivers are blacklisted in the /etc/modprobe.d/ ?

---

### Post by este.el.paz on 2015-03-09
> **luigiburdo said:**
> hi este. 
The video show of much is fast Mate booting on Quad G5 exactly 3x compared Debian and 5x compared OsX Leopard  but the most important think of the video is have the RadeonHD working on Quad without a Apple firmware ;)
About audio do you had been check if the sound drivers are blacklisted in the /etc/modprobe.d/ ?

Ah, well yeah I've enjoyed MATE in various flavors of LM for quite awhile.  In terms of sound in 14.04 on my G4 iBook, I followed the FAQ, and I guess because of the "hwdetect" bug, the "sound-aoaa"??? mods were indeed blacklisted, so I did what the FAQ suggested and just removed the "blacklist.d" file . . . and then I followed some advice on the "Sound in 14.04" thread to "modprobe the "ibus2" driver????  and that worked.  i did also add the 4 correct drivers into another file, perhaps the /etc/modprobe.d/  file, which seemed to resist my efforts for several attempts--it's all on the FAQ for the most part.  rsavage said my device was one of the easy ones to get fixed, and I didn't need his patch to get it working.

e.e.p.

---

### Post by rican-linux on 2015-03-09
> **luigiburdo said:**
> Some friend ask a small info about the speed of mate on Quad G5 . This is a small video about.
soon i will try to find some free time for make the full desktop video experience... enjoy

[https://www.youtube.com/watch?v=NyShy_ey7Ds&list=UUkb4bw4N19d-x_tn2FXLojQ](https://www.youtube.com/watch?v=NyShy_ey7Ds&list=UUkb4bw4N19d-x_tn2FXLojQ)

I cannot wait till see the full desktop experience! Thanks!

---

### Post by luigiburdo on 2015-03-09
Hi Rican, 
Im recording my desktop but i can say for sure the desktop programs recording are not the best here!

---

### Post by rican-linux on 2015-03-09
> **luigiburdo said:**
> Hi Rican, 
Im recording my desktop but i can say for sure the desktop programs recording are not the best here!

I know I tried using recordmydesktop but I could never get the settings right.

---

### Post by luigiburdo on 2015-03-09
yes i had been used it and really worst result not the best for show the quality and speed of the system... i will try to make something different or will buy a camcoder i think it is the best solution

---

### Post by rican-linux on 2015-03-09
I thought about trying to use my iPhone to capture the video.

---

### Post by luigiburdo on 2015-03-10
Mate with virtualized Debian with kvm :) Thanks to Mate 
and i can play video good on youtube like as native on Iceweasel 
Quad G5 rulez




[IMG]https://fbcdn-sphotos-f-a.akamaihd.net/hphotos-ak-xtp1/t31.0-8/10258398_10203723199622085_1572444393507823755_o.jpg[/IMG]

---

### Post by rican-linux on 2015-03-10
What are you using for youtube video playback? Gnash?

---

### Post by luigiburdo on 2015-03-10
Rican if installed as native gnash work on iceweasel but on  Kvm the video was played by html5 player and the incredible thinks is they are showed good by kvm.
Now im building kernel4 in Kvm debian with all kvm speed video options ;-)

---

### Post by rican-linux on 2015-03-10
> **luigiburdo said:**
> Rican if installed as native gnash work on iceweasel but on  Kvm the video was played by html5 player and the incredible thinks is they are showed good by kvm.
Now im building kernel4 in Kvm debian with all kvm speed video options ;-)

The html5 player is very choppy and consumes CPU cycles on both my iBook and PowerBook. Also in MATE 15.04 on my iBook gnash and light spark are crashing.

---

### Post by luigiburdo on 2015-03-10
> **rican-linux said:**
> The html5 player is very choppy and consumes CPU cycles on both my iBook and PowerBook. Also in MATE 15.04 on my iBook gnash and light spark are crashing.

yes they crash on Mate ... i dont know why but on debian everything working right. i dont know what not is working right on mate ... i have some problems like crash with some build application that use pixman

---

### Post by rican-linux on 2015-03-10
> **luigiburdo said:**
> yes they crash on Mate ... i dont know why but on debian everything working right. i dont know what not is working right on mate ... i have some problems like crash with some build application that use pixman

I have the same resource issues on Debian. html5, gnash, and lightspark all are slow, choppy and cpu intensive on my PowerBook G4.

---

### Post by dr.david.maloney on 2015-03-11
> **rican-linux said:**
> I have the same resource issues on Debian. html5, gnash, and lightspark all are slow, choppy and cpu intensive on my PowerBook G4.

In Iceweasel have you tried Greasemonkey, install viewtube, then try VLC mozilla plugin or Totem or geckomediaplayer? My last Powermac running Debian bit the dust recently but that worked for me in late 2014....

---

### Post by rican-linux on 2015-03-11
I have tried those on Debian and they work great. I was hoping for something more native to the browser like html5 or gnash to work as well.

---

### Post by luigiburdo on 2015-03-11
I have the feeling that everything is related Xorg or Video board drivers. On debian im using Nvidia 7800gtx and 3d mesa an gallium are running good.
on Mate i use Radeonhd where the Xeno Patch is needed and work but i  see there are many Dri issues that made the kernel crash with machine freeze . 
The freeze and crash stop after upgrade to kernel 4.00 but radeonhd continue gave not right colors (Xorg radeon bug) i hope in future the xorg radeon bug will be fixed .

---

### Post by rican-linux on 2015-03-11
It would if the mesa developer upstream would get that fixed, but since our hardware is old I do not know if that is likely. Thankfully there guys in the community who help where they can. This is why there is a 14.04 mesa patch that fixes r300 driver issue.

---

### Post by luigiburdo on 2015-03-11
The problem is here i have an R600 board Radeon HD 4650 and 6570 ... 
I'm courious recan if you run a webgl site the colours are right or wrong with patch ?

Here is Kernel 4 on Mate with firefox webgl working ... but where shaders is used wrong color issue come

[IMG]http://i1249.photobucket.com/albums/hh511/tlosm/BenchmarkG5/Schermata_zpsikeiq70e.png[/IMG]

---

### Post by rican-linux on 2015-03-11
I am having browser issues on Ubuntu PPC. There are sites that do not load and plugins cause firefox to crash. I am seeing it both on MATE and Lubuntu. When I get home I will check the site out.

---

### Post by este.el.paz on 2015-03-11
> **rican-linux said:**
> I am having browser issues on Ubuntu PPC. There are sites that do not load and plugins cause firefox to crash. I am seeing it both on MATE and Lubuntu. When I get home I will check the site out.

This could be an FF thing, with recent upgrades I've also seen some problems with function . . . .  I guess the test would be if you have a system with an older FF version and see if the problems happen . . . .

---

### Post by rican-linux on 2015-03-12
> **luigiburdo said:**
> The problem is here i have an R600 board Radeon HD 4650 and 6570 ... 
I'm courious recan if you run a webgl site the colours are right or wrong with patch ?

Here is Kernel 4 on Mate with firefox webgl working ... but where shaders is used wrong color issue come

[IMG]http://i1249.photobucket.com/albums/hh511/tlosm/BenchmarkG5/Schermata_zpsikeiq70e.png[/IMG]

This is what I am seeing.

---

### Post by luigiburdo on 2015-03-12
rican upgrade the kernel, after upgrade to a new kernel firefox dont crash any more.
in my case im using kernel 4 ... the problem of kernel 3.13 is in a dri2 bug.

---

### Post by rican-linux on 2015-03-12
Where do I get kernel 4 for PowerPC? I only see armh, amd64 and i386 [here]("http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.0-rc3-vivid/").

---

### Post by luigiburdo on 2015-03-12
here rican 
[https://www.kernel.org/pub/linux/kernel/v4.x/testing/linux-4.0-rc3.tar.xz](https://www.kernel.org/pub/linux/kernel/v4.x/testing/linux-4.0-rc3.tar.xz)

but you need to build it .
This is my G5 and RadeonHD build 
[https://www.dropbox.com/s/optp7z3liuh6y3d/Kernel4.tar.gz?dl=0](https://www.dropbox.com/s/optp7z3liuh6y3d/Kernel4.tar.gz?dl=0)

---

### Post by rican-linux on 2015-03-12
get to compile my first kernel. This will be fun!

---

### Post by luigiburdo on 2015-03-12
is better you find a good guide about :)

---

### Post by rican-linux on 2015-03-12
I am using the Ubuntu guide

[http://help.ubuntu.com/community/Kernel/Compile](http://help.ubuntu.com/community/Kernel/Compile)

---

### Post by luigiburdo on 2015-03-12
hope you luck rican. because i fail with mate to build kenrel and i build it in debian (kvm ;-) ) and after install on mate :P

---

### Post by rican-linux on 2015-03-12
This is not my main machine. I bought it so I can test things like this. ;)

---

### Post by rican-linux on 2015-03-13
I successfully installed kernel 4.0.0-rc3 on my iBook G4! It over 13 hrs to compile, but the browser video playback has improved.

[ATTACH=CONFIG]260602[/ATTACH]

---

### Post by luigiburdo on 2015-03-13
Share it for who have g4 machine ;)
yes kernel 4 make better video playback ad made firefox dont crash the system any more :)

---

### Post by rican-linux on 2015-03-13
I made a customization to it. I turned off multiprocessor cause it said it would improve single processor machines. So if you have dual core G4 tower I do not think it will work.

---

### Post by luigiburdo on 2015-03-13
But who have macmini g4 or powerbook will enjoy ;-)

---

### Post by rican-linux on 2015-03-13
You can get them [here]("https://drive.google.com/folderview?id=0ByNWUTbPhemsMUxYSnJ2WXpxcFE&usp=sharing"). I make no promises if it is any good. Use at your own risk...remember to back up!

---

### Post by luigiburdo on 2015-03-14
Good Job Rican ;)

---

### Post by rican-linux on 2015-03-14
I got Ubuntu-MATE 14.04 installed on my iBook G4 with the patch mesa drivers so I have 3D acceleration but sadly compiz was a bust (@rsavage you were right). I am using compton for some compisiting and I also have the 4.0.0-rc3 kernel installed and running.


[ATTACH=CONFIG]260621[/ATTACH]

---

### Post by flaymond on 2015-03-14
Is Ubuntu mate lighter than Ubuntu or Kubuntu?

---

### Post by rican-linux on 2015-03-14
Yes the MATE desktop is fork of GNOME 2 which is lighter than Unity and KDE.

---

### Post by este.el.paz on 2015-03-17
Folks:

Slight change of flavor, but as I am the OP I give myself permission to talk about trying to get U-MATE running on a recently revived *****G4 Sawtooth Powermac.******  Right now I've got Xu 12.04 installed and it's running fine, and the installation was trouble free, no xorg.conf file, etc.  But, I keep getting the "Don't you want to update to 14.04 LTS?" messages from the Software Updater . . . so far I am able to resist the siren call.  I failed to rsist the beautiful singing on my iMac (now more or less deceased) and I used the Updater method, thinking I wouldn't have to reload wifi or bookmarks . . . but, it took something 4 hours or so to accomplish on my "3MB/sec" DSL . . . and then there was other stuff to fix, needed the xorg.conf file . . . i.e., it wasn't "trouble free" . . . .

But, at some point I guess 12.04 will be "unsupported" and I've got U-MATE for PPC installed on my iBook, which I like; however, the Powermac optical drive right now only boots CDs, no DVDs . . . so, my test question, is there a way to do "alternate installer" for the U-MATE spin for PPC?  Or would that be like installing a generic PPC edition base Ubuntu 14 system, and then possibly at the end it would list some DE options, which might include MATE?  Or, going that route I'd have to add the MATE PPA after installing the Alt install base, and then I could add MATE?  I'm sure it could be done "manually" like that . . . but I'm just wondering if there is a smaller CD size file with the U-MATE PPC edition all ready to install?  I'm pretty sure the '00 era Powermacs will not boot USB drive, so far my iBook would not with some effort put into it . . . I've got the U-MATE iso "burned" to USB . . . just collecting dust . . . but the G4 drive only boots CD.

e.e.p.

---

### Post by rican-linux on 2015-03-18
e.e.p,

I have an iBook G4 that the CD Rom is at times flaky and I have booted from USB. Although I have not tried from a G4 tower.

---

### Post by este.el.paz on 2015-03-18
> **rican-linux said:**
> e.e.p,

I have an iBook G4 that the CD Rom is at times flaky and I have booted from USB. Although I have not tried from a G4 tower.

r-l:

Thanks for the reply, from the Lubuntu list people it seemed like there was a time when that capacity was added, possibly in '04? but from the FAQ it seems there might be a "doughnut" when it could be done and then not.  My iBook is 933 MHz, it looks like yours is a newer . . . faster model; I tried the different methods described there on the iBook . . . haven't tried on the tower, but since it's an '00 or so, not thinking that it would work.  Of course nothing ventured . . . but still looking for some insight into whether  there is an "alt install for U-MATE PPC" already spun up?

e.e.p.

---

### Post by rican-linux on 2015-03-18
> **este.el.paz said:**
> r-l:

Thanks for the reply, from the Lubuntu list people it seemed like there was a time when that capacity was added, possibly in '04? but from the FAQ it seems there might be a "doughnut" when it could be done and then not.  My iBook is 933 MHz, it looks like yours is a newer . . . faster model; I tried the different methods described there on the iBook . . . haven't tried on the tower, but since it's an '00 or so, not thinking that it would work.  Of course nothing ventured . . . but still looking for some insight into whether  there is an "alt install for U-MATE PPC" already spun up?

e.e.p.

Lubuntu yes MATE no see [here]("http://iso.qa.ubuntu.com/qatracker/milestones/326/builds").

---

### Post by este.el.paz on 2015-03-18
r-l:

Thanks for the link, yes, it does look like Lu is the only offering for Alt install on the Tracker . . . nothing wrong with going that way.  It might be possible to find something else over on the "dailies" . . . right now it's not at the top of the to-do list . . . .  Like, now they are saying "Core" on the Tracker, didn't see if that was explained, would that be like the old "mini" install?  Or, is that the "base" for example Ubuntu system, and might be CD sized?  I didn't spend too much time there?  But, might be installing "Core" Ubuntu and then adding MATE would offer me a way to get there?

e...

---

### Post by rican-linux on 2015-03-18
[Here]("https://wiki.ubuntu.com/Core") is a an explanation of Ubuntu Core. If what you are wanting to do a [netboot install]("http://iso.qa.ubuntu.com/qatracker/milestones/326/builds/90441/testcases") would probably be best.

---

### Post by rican-linux on 2015-03-18
BTW the links I sent are all for 15.04 dev releases.

---

### Post by este.el.paz on 2015-03-18
> **rican-linux said:**
> BTW the links I sent are all for 15.04 dev releases.


r-l:

Appreciate the link on the "Core" . . . .  Saw the "vivid" somewhere in there, which was a wtf moment . . . as this is a "14.04" thread . . . but, I got the idea, and all is forgiven . . . but if the ISO Tracker link was also for vivid then maybe the 14.04 options would be different . . . .  Anyway, if and when I get ready to make a move I'll look through the various places to see what's up; but in a G4 I'm not thinking about going beyond 14.04, or in any event a LTS.  Too much time goes into getting the system set up to go through each iteration on PPC equipment. 

e...

---

### Post by rican-linux on 2015-03-18
[Here]("http://cdimage.ubuntu.com/netboot/trusty/") is the 14.04 netboot location

---

### Post by rican-linux on 2015-03-18
Now I remember why I recommended the 15.04 link. MATE 14.04 is not an official release. So I do not think you can install it without a ppa.

---

### Post by este.el.paz on 2015-03-18
> **rican-linux said:**
> Now I remember why I recommended the 15.04 link. MATE 14.04 is not an official release. So I do not think you can install it without a ppa.


r-l:

Ah, right, it definitely was a post 14.04 development . . . but, thanks for the netboot link . . . .  Just realized that perhaps I could scavenge the iMac for optical drive and possibly the faster processor . . . not sure if that can be done on either front, but it has the super-drive and then I'd be home free on the DVD boot U-MATE I have already . . . .

e....

---

### Post by rsavage on 2015-03-19
> **este.el.paz said:**
> 
I'm pretty sure the '00 era Powermacs will not boot USB drive, so far my iBook would not with some effort put into it . . . I've got the U-MATE iso "burned" to USB . . . just collecting dust . . . but the G4 drive only boots CD.

e.e.p.

The g4 sawtooth's can boot from USB (it was a feature that was added to that model).  The mate 14.04 ISO has grub so that no 'burning' is actually necessary, but of course you can do it the 'normal' way with dd.

I've found that some drives are slow to get recognised by openfirmare.  If that is the case then I've used the command probe-usb on my iBook.  Is detailed in the FAQ as always.

1000 posts for me - so sad.

---

### Post by este.el.paz on 2015-03-19
> **rsavage said:**
> The g4 sawtooth's can boot from USB (it was a feature that was added to that model).  The mate 14.04 ISO has grub so that no 'burning' is actually necessary, but of course you can do it the 'normal' way with dd.

I've found that some drives are slow to get recognised by openfirmare.  If that is the case then I've used the command probe-usb on my iBook.  Is detailed in the FAQ as always.

1000 posts for me - so sad.

@r:

Thanks for the info, much appreciated . . . this Sawtooth is a new machine for me so I'm not well versed in what it can & can't do.  So, I'll have to try the FAQ again, the GRUB thingie didn't seem to appear when booting the DVD that I used to install on the iBook.  Over on my MBPro it's GRUB powered booting, on the iBook it's still Yaboot menu--but I'm not staying up late into the wee hours to get this stuff done, it's just a hobby.  In the meantime from when I posted here I ordered a DVD op drive from eBay, and I'll also try the USB boot and see how that works.  I did try all the various openfirmware commands on the iBook, don't recall seeing anything about "probe-usb" . . . no worries I'll look again, if the USB boot doesn't work, the used optical drive will be here in a few days . . . .

But, I do appreciate the "1000 posts" . . . it's probably sadder than that if you add in the Mintppc posts . . . possibly others . . . doesn't take too much to add up . . . but, thanks.

e...

[edit1]:  Tried to use option key with usb MATE . . . did not work. although the drive mounted on the desktop, didn't show in bootloader.  Guess it would be through openfirmware . . . or actually reading FAQ . . . .  "I'm late, I'm late . . . late for a very important date . . . ."

---

### Post by luigiburdo on 2015-03-22
Bad news today.
I had been made a clean installation on my Quad G5 with Mate 14.04 and everything goes right like the usual ....
after install i upgrade the system using the system update in mate .... it start install about 200 updates ...
after this i have not a working desktop envoiment .... no icons , no pannels ... only the mate background and mouse pointer... 
Mate become unusable.

Edit : found how to turn round this issue.... newer do "make partial update"

---

### Post by este.el.paz on 2015-03-22
> **luigiburdo said:**
> Bad news today.
I had been made a clean installation on my Quad G5 with Mate 14.04 and everything goes right like the usual ....
after install i upgrade the system using the system update in mate .... it start install about 200 updates ...
after this i have not a working desktop envoiment .... no icons , no pannels ... only the mate background and mouse pointer... 
Mate become unusable.

Edit : found how to turn round this issue.... newer do "make partial update"

LB:

"neVer do "make partial update""?????  Seems like the general wisdom over the last couple of years is to use the console to do update/upgrades . . . with aptitude . . . as there seems to have been issues with software update at times????  Terminal has been considered more reliable . . . .

BTW, got a used DVD optical drive and put it into my G4Sawtooth and was able to boot the U-MATE DVD without any boot params . . . seemed to be fine, only problem was loss of correct time . . . so at some point I'll probably try the install out of my beloved Xu 12.04 . . . : - (

e...

---

### Post by saltycat77 on 2015-03-22
I scavanged a DVD drive from a G4 for my Sawtooth, how did installing in yours go? I have an eMac that runs the Ubuntu Live CD without issues, seriously considering installing Ubuntu Mate on that. Will post here when I do.

---

### Post by este.el.paz on 2015-03-22
> **saltycat77 said:**
> I scavanged a DVD drive from a G4 for my Sawtooth, how did installing in yours go? I have an eMac that runs the Ubuntu Live CD without issues, seriously considering installing Ubuntu Mate on that. Will post here when I do.

@saltycat:

Welcome to the Apple Hardware User . . . subforum . . . nice to hear from you again.  I posted some of the details on the xymer thread . . . watching some videos I guess got me in the ballpark, but was different than my Sawtooth . . . .  Of course the replacement needs to be "IDE" & "PATA" . . . right?  I think one video showed that the optical drive and the zip drive come out together, so both have to be disconnected.  And the plastic door covers for both get released from the inside, by the two tabs that would be closest to you with the system door open . . . which is key point that in my case exposed two screws from the ***front*** (in the videos the 4 screws are all on the inside to release the op drive tray) . . . and then the other two were on the side of the tray.  Nothing along the back wall as was shown in some of the videos.  And the combi op drive/zip drive tray slides out through the front, rather than from inside as shown on some of the videos . . . .  

So it took some time to just kind of figure out how to do it, rather than the actual doing of it . . . but relatively simple, although not without some head scratching moments.  Had to get a tweezers to get the "jumper" up and out of the "csel" position and over to "master" since it was pushed down too far to get by finger.  And, this optical drive I guess only burns DVD+RW . . . but reads both . . . I'm down to my last few DVD-RW, so if I want to burn I'll have to buy some + types.

And, like I mentioned I was then able to boot the U-MATE DVD without boot params . . . whereas trying to boot the Lu 15.04 "Vivid" PPC DVD same default "live" params . . . got me to a desktop image, but then the system and screen "went to sleep" . . . ????  So, rebooted the MATE DVD and played around with it, found a better desktop image than that goofy green/black cloud image . . . I'll probably do the install sometime after "tax time" when I have a spare moment.  While I was in the "bay" I also maxed the RAM out with 4 512MB PC133 dealies for the max rated 2GB ponies . . . does make a noticeable difference in terms of being able to do stuff on the web more or less "normally" . . . as clicking on stuff . . . it happens; rather than with the 1 GB . . . spinning beachball . . . and long pauses before stuff might happen . . . or not.  450 MHz processor is a bit of a slow poke no matter how you spin it.

e...

---

### Post by saltycat77 on 2015-03-25
Good to know there's some video out there, I'll give it shot this  weekend. I tried Ubuntu Mate 14.04 on the eMac, which has a faster  (1Ghz) G4. It went well except for one thing-video. Video drivers are  broken. Here's a picture .


[ATTACH=CONFIG]260896[/ATTACH]

---

### Post by este.el.paz on 2015-03-25
> **saltycat77 said:**
> Good to know there's some video out there, I'll give it shot this  weekend. I tried Ubuntu Mate 14.04 on the eMac, which has a faster  (1Ghz) G4. It went well except for one thing-video. Video drivers are  broken. 

I can see the toolbars, so possibly that's just the "background" image that has been selected by default?  : - ))

I don't know where the eMac falls in terms of video cards, I believe on my iBook I had to use the "agpmode=-1" boot params . . . because it has an AGP bus???  But, if you can see the "additional drivers" launcher from the drop down toolbar menu, you might be able to add the right driver via the GUI . . . in my MBPro I use the "recommended" NVidia driver.  Have to be connected to the net of course.  

If that doesn't work you might have to search Google to find the boot params needed for your eMac . . . or checking through the PowerPCFAQ and see what turns up there for eMac video . . . .

e...

---

### Post by luigiburdo on 2015-03-25
Salty try this

```

live video=offb:off video=radeonfb:off radeon.agpmode=-1 


```

I had the same issue on macmini g4 and with that line i had been fixed

---

### Post by saltycat77 on 2015-03-25
OK thanks, will do later today and check back in-I wish  running Ubuntu & deritatives on PPC were as easy as they are on PCs-even graphics issues on P3s were far easier to deal with

---

### Post by este.el.paz on 2015-03-27
> **saltycat77 said:**
> OK thanks, will do later today and check back in-I wish  running Ubuntu & deritatives on PPC were as easy as they are on PCs-even graphics issues on P3s were far easier to deal with

@sc77:

Right, does take a bit of doing in PPC, that's why the LTS choices are perhaps a better way to go.  But, if LG's boot params work, then you probably need to set up an "xorg.conf" file to select those video drivers, as well as adding them to the yaboot.conf file . . . it's all in the PPCFAQ . . . not too difficult actually in the grand scheme of linux . . . .

e...

---

### Post by saltycat77 on 2015-03-27
While booting with that line had no effect, the system itself is usable & responsive with the exception of Synaptic-Firefox ran and the other other utilities ran but for some reason Synaptic is affected by the video bug and didn't render at all. I'll try some of the other suggestions in the PPCFAQS.If I can fix the video issue I'd use it more than OS X on the eMac.

---

### Post by luigiburdo on 2015-03-28
Check if with this you will fix everything 


```
[COLOR=#404040][FONT=Roboto]live video=radeonfb:off radeon.modeset=1 radeon.agpmode=-1 video=offb:off[/FONT][/COLOR]
```

---

### Post by este.el.paz on 2015-03-28
> **saltycat77 said:**
> While booting with that line had no effect, the system itself is usable & responsive with the exception of Synaptic-Firefox ran and the other other utilities ran but for some reason Synaptic is affected by the video bug and didn't render at all. I'll try some of the other suggestions in the PPCFAQS.If I can fix the video issue I'd use it more than OS X on the eMac.


@sc77:

Try these different boot params that LG is suggesting, as well as checking what is listed if you hit the "tab" key at the second Yaboot window, I've had to add in specific reference to "powerpc" in some of my boot params, a list of different terms will show up with Tab.

Also, what you are describing with intermittent applications rendering has happened for me, and is ****"easily"**** solved with a proper xorg.conf file.  You can compile one following the PPCFAQ, or try the "linuxjemac" site that has a bunch of them posted for download . . . can be done through the console.

Other suggestion, try another flavor of 14.04, or even 12.04 . . . to test out whether one of them works out of the box.  You could always add MATE DE to it . . . .  But, try the xorg.conf file, pretty sure that will get it right . . . happy trails . . . .

e....

---

### Post by rican-linux on 2015-03-30
Compiz is a little buggy but here is some 3D cube awesomeness!


[ATTACH=CONFIG]260986[/ATTACH]

---

### Post by este.el.paz on 2015-03-31
@r-l:

Cute . . . very 3D . . . very awesome . . . .

e...

---

### Post by este.el.paz on 2015-04-03
Hey guyz . . . guyz????? . . . is anybody out there???  This is freakin' serious; I think I saw over on the Lubuntu users list that some of the gents were having some busted system problems after doing an update/upgrade . . . and that might have happened to my iBook MATE 14 edition.  I did a kernel upgrade and a bunch of other stuff last weekend, through the terminal, and saw a bunch of stuff to be removed, "marco" "mate-screensaver" . . . and a kernel upgrade, and I clicked "yes" . . . ran thru that, and then can't remember if I rebooted to check the system or just went to OSX (for the "suspend" that 14.04 PPC doesn't have).

Today, restarted, got to the MATE log in window, logged in . . . and only MATE desktop image is working, no toolbars, nothing else, nada . . . .  Jumped to a TTY and ran the update/upgrade and again 80MB worth of stuff, FF, TBird . . . few other things . . . screen went black . . . waited until the machine stopped making noise, rebooted . . . this time hit the "tab" key and booted "Linux old" . . . same thing, logged into the desktop image . . . only . . . .

Wha happen, man?  This is first time in recent or distant memory that an ubuntu upgrade has busted the system in a fairly substantial way . . . .  Obviously I can access the CLI, but, no GUI . . . help . . . help meeeeee . . . . . ):P

e...

---

### Post by rican-linux on 2015-04-03
I have not run into that issue. I will check when I get back home.

---

### Post by este.el.paz on 2015-04-03
@r-l:

Appreciate the reply . . . it's certainly not something to look forward to . . . but, you are in 15.04??  Might make a difference?  Watching the Lu users list, it does seem like some significant changes are being made "under the hood" for various reasons . . . might be creating "dependency" issues???

e...

---

### Post by rican-linux on 2015-04-03
I moved back to 14.04 and using the live CD for 15.04 testing.

---

### Post by luigiburdo on 2015-04-03
yes system upgrade make issue on Mate i was report this some days ago

---

### Post by este.el.paz on 2015-04-03
> **luigiburdo said:**
> Bad news today.
I had been made a clean installation on my Quad G5 with Mate 14.04 and everything goes right like the usual ....
after install i upgrade the system using the system update in mate .... it start install about 200 updates ...
after this i have not a working desktop envoiment .... no icons , no pannels ... only the mate background and mouse pointer... 
Mate become unusable.

Edit : found how to turn round this issue.... newer do "make partial update"

> **luigiburdo said:**
> yes system upgrade make issue on Mate i was report this some days ago

@LB:

OK, I thought I had read it somewhere it says that post was "two weeks ago" but seems like no one else has hit this snag here?  But . . . even at that time I wondered what does "newer do 'make partial update'" mean exactly?  I used the Terminal as per most of the expert recommendations with aptitude . . . so it should be showing all needed upgrades . . . but, in terms of "never do partial update" then, how are you getting around that to get a "full update"?  I ran "sudo apt-get dist-upgrade" because it showed there were some packages "held back" . . . and even "dist-upgrade" didn't get those few items . . . problem was not alleviated.

But indeed, as you reported so diligently two weeks ago . . . no icons, no panels . . . only stock MATE background and mouse pointer . . . MATE via GUI has become "unusable" . . . except via TTY . . . .

e...

[edit:  Over on my MBPro running in third partition, LM 17.1 MATE I held my breath and ran the update/upgrade in the Terminal, even after Software Manager said "system up to date" . . . in aptitude a number of upgrades were shown; no kernel upgrades were listed . . . but some with "libwebkit2gtk-1 x x x"  names like that, were there, and I think it's this transition from "webkit" to "gtk" that is causing some "problems" . . . .  Ran through the list and rebooted, and, all is "OK" in LM MATE.  So, either LM has done something to handle it, OR . . . possibly whatever is needed has not been done for PPC????.]
[edit2:  LP Bug report filed:  [https://bugs.launchpad.net/ubuntu-mate/+bug/1440266](https://bugs.launchpad.net/ubuntu-mate/+bug/1440266)

---

### Post by rican-linux on 2015-04-04
I just did an apt-get update && apt-get upgrade and my system is still up and wokring.

---

### Post by este.el.paz on 2015-04-04
> **rican-linux said:**
> I just did an apt-get update && apt-get upgrade and my system is still up and wokring.

Wokring?  Some special extra-terrestrial state?  : - ))  But, "interesting" I guess is all we can say . . . only difference so far is I run a-g update separately and then a-g upgrade . . . .  I personally don't have enough command line skills to know what to check that might show why one system is fine and a couple others are not.

I'll have to see if I can find time to try adding another DE on top of the situation and see if I can log into it for comparison, etc . . . otherwise, no ideas.  Waiting to hear back from the LP peeps . . . .

e..

---

### Post by luigiburdo on 2015-04-06
one guy write me from my youtube channel he his in trouble with mate 14.04.1 . 
he burn the iso dvd of mate on his [COLOR=#333333][FONT=arial]Quicksilver G4 nov.2003, cpu G4 n°3 da 1.25 Ghz, RAM 1 GB , HD  80 GB IBM Ati Radeon 9000pro,  usb 1.1
but the disk is showed well on OsX but dont run if the c key is pressed when him turn on his machine or when the "alt" key is pressed on his machine power on

Some one face this guy problem? will be possibile help him in some way ?[/FONT][/COLOR]

---

### Post by este.el.paz on 2015-04-06
> **este.el.paz said:**
> @LB:

OK, I thought I had read it somewhere it says that post was "two weeks ago" but seems like no one else has hit this snag here?  But . . . even at that time I wondered what does "newer do 'make partial update'" mean exactly?  I used the Terminal as per most of the expert recommendations with aptitude . . . so it should be showing all needed upgrades . . . but, in terms of "never do partial update" then, how are you getting around that to get a "full update"?  I ran "sudo apt-get dist-upgrade" because it showed there were some packages "held back" . . . and even "dist-upgrade" didn't get those few items . . . problem was not alleviated.
But indeed, as you reported so diligently two weeks ago . . . no icons, no panels . . . only stock MATE background and mouse pointer . . . MATE via GUI has become "unusable" . . . except via TTY . . . .

e...

[edit2:  LP Bug report filed:  [https://bugs.launchpad.net/ubuntu-mate/+bug/1440266](https://bugs.launchpad.net/ubuntu-mate/+bug/1440266)

> **luigiburdo said:**
> one guy write me from my youtube channel he his in trouble with mate 14.04.1 . 
he burn the iso dvd of mate on his [COLOR=#333333][FONT=arial]Quicksilver G4 nov.2003, cpu G4 n°3 da 1.25 Ghz, RAM 1 GB , HD  80 GB IBM Ati Radeon 9000pro,  usb 1.1
but the disk is showed well on OsX but dont run if the c key is pressed when him turn on his machine or when the "alt" key is pressed on his machine power on

Some one face this guy problem? will be possibile help him in some way ?[/FONT][/COLOR]

@luigiburdo:  Did this guy check the md5sum number before he burned the DVD?  And, then did he select "burn at slowest speed" option, rather than "fastest"?

Also, since you experienced the same issues with update/upgrade breaking the GUI, could you add your name to my bug #1440266?  Also, it seems like you fixed your problem?  Re-install?  My workaround was to add the XFCE4 DE . . . and that got my GUI back . . . set to "MATE theme" . . . but MATE DE session logs into now a black screen with white mouse pointer . . . .

e...

---

### Post by luigiburdo on 2015-04-06
Thanks e ... i will ask him if he do what you been write .
will report soon as possible

---

### Post by este.el.paz on 2015-04-06
Other question is did he try to boot another DVD using "c" key or option key?  And, it is only this MATE 14 DVD that isn't booting?

---

### Post by luigiburdo on 2015-04-07
i had been say the same to him ... but the c key the cdrom dont boot and with Alt the icons isnt show on boot menu

---

### Post by este.el.paz on 2015-04-07
> But, spent some time trying to get synaptic to do its thing, like I  said, I have to "su" in Terminal to open synaptic, otherwise it says I  have "no admin privileges" . . . but, I'm just in another session,  logged in as me . . . so there is some significant "corruption" and also  FF doesn't remember "previous sessions" . . . .  Anyway, I came up with  the idea to use synaptic to "remove all MATE" things . . . but as I was  scrolling through the list of MATE stuff the two mate terminal apps?   mate-terminal & mate-terminal-common . . . both had exclamation  points in front of them, so then I decided to try to just remove them  and see if that "fixed" the problem, but, couldn't remove one of them  because it was "broken" . . . so I fixed it, and then removed them and  also apport (which I just recently had to install to try to report to  Bug reports) was removed, also "libtve9"??? was removed today.  Then  when I tried to "install" mate-terminal-common" it said "failure due to  dependency, need libtve9, but we aren't going to install it" . . . . so,  I think I just installed mate-terminal via synaptic . . . rebooted,  tried to log in via MATE, back to the black screen . . . .  So, point  being that until today when I ran "dist-upgrade" "two packages have been  held back" . . . the libtve-common and the mate-terminal . . . and I  was pursuing this idea that one of those packages was "corrupted" . . . .   BUt, then it was odd that now libtve9 is "needed" but, was just  removed via aptitude . . . .  I'm away from the unit now for a few  hours, don't know if anything is going to appear in a flash . . . or, I  just have to decide which system I will "nuke and pave into" . . . .  I  guess if I could find a U-MATE 14.04.2 PPC iso it might be worth trying .  . . .  System is sort of OK using XFCE, except that I don't seem to be  "admin" & FF doesn't remember where its been . . . .

Posted this on LP Bug Reports:[https://bugs.launchpad.net/ubuntu-mate/+bug/1440266?comments=all](https://bugs.launchpad.net/ubuntu-mate/+bug/1440266?comments=all)

e...

---

### Post by este.el.paz on 2015-04-07
> **luigiburdo said:**
> i had been say the same to him ... but the c key the cdrom dont boot and with Alt the icons isnt show on boot menu

From the Ubuntu MATE "Useful Information about 14.04" wiki:

> [h=2]EFI and UEFI systems[/h]  The Ubuntu MATE amd64 .iso image can boot EFI capable  computers from USB and DVD, with or without SecureBoot enabled. However,  if you encounter any difficulties booting EFI hardware then try:
  
[LIST]
[*]Disabling SecureBoot.
[*]Enabling Legacy BIOS or BIOS emulation mode.
[*]Try the amd64+mac .iso image.
[/LIST]
  Even though Macs use a variant of EFI (an earlier version of what's  now called UEFI), they apparently can't cope with multi-catalog CDs, and  simply refuse to boot them. Therefore the amd64+mac images are available,  which are exactly the same as the amd64 images except that they only support BIOS booting. Macs are happy to boot these in their BIOS emulation mode.
  The name amd64+mac is a slight misnomer, because it turns out that some systems other than Macs suffer from a similar problem and using the amd64+mac image on some EFI capable PC hardware will work.



---

### Post by este.el.paz on 2015-04-08
> **este.el.paz said:**
> Posted this on LP Bug Reports:[https://bugs.launchpad.net/ubuntu-mate/+bug/1440266?comments=all](https://bugs.launchpad.net/ubuntu-mate/+bug/1440266?comments=all)

e...

Still looking for anyone, like uh, Luigi, to add their name to my bugz report . . . .  Latest update, MATE is still "lunched" . . . .

> I did check the disk and SMARTReporter in OSX says disk is OK.   Hopefully you understand that this appears to be a software side  problem?  I tried again to "re-install" mate-desktop-environment in  synaptic, after running "dist-upgrade -f" a little earlier.  After the  "dist-upgrade" there were 15 packages to download, and 3 to remove,  noticed that one of the ones to be removed was "libvte-common" . . .  which was just iinstalled yesterday?  Also, in synaptic, although I believe I just tried to remove and  reinstall "mate-terminal" which showed an exclamation point, today,  "mate-desktop-environment" showed as "not installed" . . . when I  checked it for install there was also an exclamation . . . just like  yesterday when I clicked "repair broken packages" there is an error . . .  due to "dependencies" . . . yesterday it was "no libvte9"????  Today I  checked in synaptic and 'libvte9" is available to install . . . but  didn't seem to show up when checking "mate-desktop-environment" . . . .   
  Ah, yeah, after doing the dist-upgrade I tried to log into the MATE  session, the background image was back again, yesterday it was just  blackness . . . no toolbar, etc.  Might make "sense" knowing that there  is apparently now, no "mate-desktop-environment" installed.  Also  looking thru the "properties" on the error install of mate-desktop under  "versions"??  it showed two, one was a something1.8.0 +9 (trusty1) and  the other was an earlier 1.8.0+8~ppal Trusty1(127.0.0.1) . . . which may  explain that (127.0.0.1) "failed to connect"???  As it is an earlier  version???  The numerous problems continue with needing to "su" in  Terminal to open synaptic, and FF not remembering passwords or history .  . . in the XFCE session, etc.



PS: Checking in Benchmark does show that this is in 14.04.2 Ubuntu-MATE . . . now running XFCE session . . . with a number of weird problems . . . .

e.e.p.

---

### Post by luigiburdo on 2015-04-08
my friend i had abbandon mate ... because when i swap with 6570 hd the system become imcompatible with it ... when and if will be released mate 14.04.02 dev probably i will return on it.
right now im using Lubuntu 14.04.2 really faster and stable on my G5 quad and the 6570 hd pcie 2gb of vram :-)

---

### Post by este.el.paz on 2015-04-08
> **luigiburdo said:**
> my friend i had abbandon mate ... because when i swap with 6570 hd the system become imcompatible with it ... when and if will be released mate 14.04.02 dev probably i will return on it.
right now im using Lubuntu 14.04.2 really faster and stable on my G5 quad and the 6570 hd pcie 2gb of vram :-)

@LB:

Thanks for the reply . . . I'm also on the line of "abandoning mate" . . . but, you could possibly still add your name to the bug report, because it obviously did affect you . . . causing you to leave it . . . ???  

BTW, my system is now 14.04.2 U-MATE . . . probably last weekend the kernel upgraded, and that possibly caused some dependency issues . . . but, it doesn't seem to be available as an iso . . . that still shows 14.04.1 . . . in PPC.  Other option possibly would be "ubuntu core" install and then see if MATE DE could be added . . . .  But, got it on the speed of Lubuntu 14.04 . . . it is sort of the only "whole system" left for PPC users in LTS . . . I like LXDE . . . I've had numerous installs running XFCE & LXDE . . . sort of lean to XFCE; but, somewhere in this recent install is something that is messing basic stuff up . . . now even in XFCE it seems to be deteriorating . . . PITA . . . .  Synaptic shows "no broken packages" . . . except when I try to add stuff . . . .

e...

---

### Post by luigiburdo on 2015-04-08
este i had been write on mate g+ group about my problems and incompatibility ... some one reply me there isnt the 14.04.2 and probably there isnt the intention to release it on ppc(?) all the mate group is now concetrate in 15.04 ... but for my machine 15.04 is the not valicable wall... black screen ,xorg crash and problems on problems . The strange for me is have a really perfoming machine with good gpu and good ram ... and face
 for have linux problems on problems (fbdev bug on 14.04) mesa color errors (Tnx Chrisitan for the patch) , Firefox wrong colors more in webgl ... i dont understand why we have to put our heads in a wall for have an Os running ... I was able to have Apus on amiga 4000 and was more simple (and wasnt) .... good old time

---

### Post by rican-linux on 2015-04-08
my opinion I do not think upstream likes powerpc

---

### Post by este.el.paz on 2015-04-08
> **luigiburdo said:**
> este i had been write on mate g+ group about my problems and incompatibility ... some one reply me there isnt the 14.04.2 and probably there isnt the intention to release it on ppc(?) all the mate group is now concetrate in 15.04 ... but for my machine 15.04 is the not valicable wall... black screen ,xorg crash and problems on problems . The strange for me is have a really perfoming machine with good gpu and good ram ... and face
 for have linux problems on problems (fbdev bug on 14.04) mesa color errors (Tnx Chrisitan for the patch) , Firefox wrong colors more in webgl ... i dont understand why we have to put our heads in a wall for have an Os running ... I was able to have Apus on amiga 4000 and was more simple (and wasnt) .... good old time

@LB:  Right, I also had issues trying to get the live DVD of 15.04 to try to run on both of my PPC computers . . . I'm thinking 15 is "a bridge too far" for PPC.  And, agreed, it should be "easier" to get stuff running on PPC than it has been lately . . . as it is more or less "stationary" in terms of hardware, like it hasn't changed too much in the last few years or longer . . . .  And, they did "have it" more or less dialed with 12.04 . . . .

> **rican-linux said:**
> my opinion I do not think upstream likes powerpc

@r-l:  That would indicate that they have "feelings" about PPC . . . I think it's more like benign neglect . . . not even on the radar screen, ignore them &  eventually they will go away . . . .

e...

---

### Post by rican-linux on 2015-04-08
> **este.el.paz said:**
> @LB:  Right, I also had issues trying to get the live DVD of 15.04 to try to run on both of my PPC computers . . . I'm thinking 15 is "a bridge too far" for PPC.  And, agreed, it should be "easier" to get stuff running on PPC than it has been lately . . . as it is more or less "stationary" in terms of hardware, like it hasn't changed too much in the last few years or longer . . . .  And, they did "have it" more or less dialed with 12.04 . . . .



@r-l:  That would indicate that they have "feelings" about PPC . . . I think it's more like benign neglect . . . not even on the radar screen, ignore them &  eventually they will go away . . . .

e...

I am not going away!!! Hahaha

---

### Post by este.el.paz on 2015-04-08
> **rican-linux said:**
> I am not going away!!! Hahaha

Cool.  I guess it will become clear whether that helps get PPC back on the devs radar . . . or whether it remains a faint speck on that huge screen of linux-dom . . . .

e....

---


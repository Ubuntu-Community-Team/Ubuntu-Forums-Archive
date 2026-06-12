---
title: "No icons in launcher on PPC install"
date: 2012-03-08
forum: Apple Hardware Users
---

### Post by mikedaub on 2012-03-08
Howdy all, 
While there is a lot I do understand about Ubuntu and Linux (currently have it running on 3 of 4 computers), I am still not 100% on the command line things.  I can easily cut and paste, but sometimes finding everything to cut and paste is difficult. 

With that in mind, I recently installed Ubuntu 12.04LTS that I got from the PPC page on an older generation Powerbook G4.  I got a bunch of things working right, but the one thing that doesn't seem to work is the icons in the launcher.  They just aren't there.  When I hover over them, I can see what the icons open up (Dash Home, Home Folder, Firefox, etc) but I can't actually see the icons.  As you can imagine, its rather annoying. 

I checked out the PPC Wiki ([https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ)) and I don't think any of the problems (black screen, blurry images, that sort of thing, are my problem.  They just aren't there.

Doing some Googling, I came across this ([http://ubuntuforums.org/showthread.php?t=1763927](http://ubuntuforums.org/showthread.php?t=1763927)).  Different version of the OS, but same problem.  

Any thoughts on correcting this?

Thanks...

---

### Post by linuxopjemac on 2012-03-12
I guess you have a PowerBook with an nVidia card in it. I run MintPPC 11 and a recent update in xserver-xorg made my G5 iMac with a GeForce FX 5200 Ultra card behave the same way as you describe here in this post. I think that when you downgrade that package, it will work as usual. I haven't had the time to experiment. If I find some directions I will let you know.

---

### Post by linuxopjemac on 2012-03-12
I could not get nouveau repaired. What I did was revert to nv. I even got it working for the iMac G5 20, which suffers from the 2 pixel screen shift. I made a patched version of the nv package specifically for this machine. It works flawlessly now.

---

### Post by mikedaub on 2012-03-23
Thanks for the update on it, and you are right, that is probably my problem, the graphic card.  

Honestly, I have been to busy to mess around with it at all, but I will try a little Googling and see what I can come up with.  Maybe the laptop is just bound to be retired and get something that plays nicer with things..

---

### Post by derxen on 2012-04-22
I have the exact same problem, with 12.04 on a Powermac G5 with GeForce FX 5200 Ultra. I worked around it by using ubuntu 2d. However, I also have a problem with the rendering of web pages (both firefox and epiphany): some blocks of text will be missing on each page, just a few lines of frame left over. Pictures are rendered fine. Is this a related problem, and will it be solved by switching to nv?

derxen

---

### Post by linuxopjemac on 2012-04-22
I reverted to nv in the end but there is a solution for your card and nouveau as driver. This xorg.conf file will work:

```
##only difference is Virtual entry in this one is square "Virtual 1680 1680" instead of display actual size 1680 1050

Section "Device"
    Identifier    "FX5200"
    BusID        "PCI:240:16:0"
    Driver          "nouveau"
    Option   "Monitor-VGA-1" "VGA_Port"
    Option   "Monitor-DVI-D-1" "DVI_Port"
    Option   "Monitor-TV-1" "TV_Port"
EndSection

Section "Monitor"
    Identifier    "DVI_Port"
EndSection

Section "Monitor"
    Identifier   "VGA_Port"
    Option   "Ignore" "true"
EndSection

Section "Monitor"
    Identifier    "TV_Port"
    Option   "Ignore" "true"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "FX5200"
        DefaultDepth    24
           SubSection       "Display"
             Depth            24
        Virtual 1680 1680
           EndSubSection
EndSection

Section "ServerLayout"
   Identifier   "Default Layout"
   Screen      "Default Screen"
EndSection
```


reference: [http://mac.linux.be/xorgconf-imac-g5-20](http://mac.linux.be/xorgconf-imac-g5-20)

for a normal Desktop G5, see this thread:
[http://www.mintppc.org/forums/viewtopic.php?f=15&t=810](http://www.mintppc.org/forums/viewtopic.php?f=15&t=810)

bug report:
[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=668828](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=668828)

---

### Post by derxen on 2012-04-22
Thanks linuxopjemac. I tried that xorg.conf earlier today, but X didn't start. I'll try again and check the log to see what goes wrong (should have done that straightaway of course). It'll take a few days (work and so on) but I'll let you know how it works out.

---

### Post by linuxopjemac on 2012-04-22
this is the xorg.conf you need:

```
Section "Device"
    Identifier    "FX5200"
    BusID        "PCI:240:16:0"
    Driver          "nouveau"
    Option    "Monitor-DVI-I-1" "ADC_Port"
    Option    "Monitor-DVI-I-2" "DVI_Port"
    Option    "Monitor-TV-1" "TV_Port"
EndSection

Section "Monitor"
    Identifier    "DVI_Port"
EndSection

Section "Monitor"
    Identifier    "ADC_Port"
    Option    "Ignore" "true"
EndSection

Section "Monitor"
    Identifier    "TV_Port"
    Option    "Ignore" "true"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "FX5200"
        DefaultDepth    24
           SubSection       "Display"
             Depth            24
         Virtual 1280 1280
           EndSubSection
EndSection

Section "ServerLayout"
    Identifier    "Default Layout"
    Screen        "Default Screen"
EndSection
```

together with these yaboot kernel arugments:
```
boot: Linux video=DVI-I-1:d video=DVI-I-2:1280x1024-24@75 video=TV-1:d
```

If you have 1280x1024 as your resolution...

---

### Post by derxen on 2012-04-22
Okay, I'll use that xorg.conf (with my BusId) with those kernel arguments. My resolution is 1680x1050, so I'll use that in the kernel argument, and make Virtual 1680 1680. I'll let you know.

---

### Post by derxen on 2012-04-23
No luck yet. With kernel arguments and xorg.conf I get a black screen, with just the xorg.conf I get a fallback screen that suggests reconfiguring xorg. The xorg log says 'no device found', but I'm pretty sure the BusId is correct. I used lspci | grep VGA to find it.

---

### Post by derxen on 2012-04-23
Checked the xorg log again, and my monitor is connected to DVI-I-1 rather than DVI-I-2. I'll change the xorg.conf and kernel arguments accordingly and try again tomorrow.

---

### Post by linuxopjemac on 2012-04-24
all G5's have the BusID as I gave you in the xorg.conf file

---

### Post by derxen on 2012-04-24
Wonderful, now it works perfectly. What's more, it works without passing the kernel arguments, just with the xorg.conf. So, two questions, just out of curiosity (always eager to learn more about linux): why are the kernel arguments needed, and why did lspci | grep VGA give me the wrong BusId?

In any case, you were a great help. Thanks a lot.

---

### Post by linuxopjemac on 2012-04-24
I don't know why it gives the wrong BusID, I only know it does.

---

### Post by rsavage on 2012-04-24
Virtual is defined as
```

**Virtual**  _xdim_ _ydim_
```So shouldn't you use:

Virtual 1680 1050

If this is a well used workaround then I'll add it to the FAQ, but Virtual 1680 1680 doesn't seem right to me.

---

### Post by derxen on 2012-04-24
But the point of setting the virtual dimensions like that, AFAIK, is to work around the corruption in the bottom half of the screen. Increasing the virtual screen size moves that problem off the real screen.

---

### Post by linuxopjemac on 2012-04-24
> But the point of setting the virtual dimensions like that, AFAIK, is to work around the corruption in the bottom half of the screen. Increasing the virtual screen size moves that problem off the real screen. 

exactly

---

### Post by rsavage on 2012-04-24
Oh I see what you mean now.  It was because you were using the same numbers for xdim and ydim that was confusing me.  Can we test if that is really significant?
 
If you've got corruption on say half the screen then that is  525 pixels (half of 1050).  So a ydim of 1575 (= 1050 + 525) should be sufficient.  You may have to add:
 
Viewport x0 y0 
 
for this to work with a smaller ydim.
 
Is all the disabling ports necessary too?  If I remember correctly, the original MintPPC poster suffered from phantom outputs and these alterations to the xorg.conf were necessary to overcome his problem with this.  If your ports are detected correctly then is just addding the Virtual/Viewport lines sufficient?

---

### Post by derxen on 2012-04-26
I'll do some testing later today. What I found out already is that this xorg.conf does not solve the problems with the missing icons for me. Ubuntu 2d works fine, but ubuntu shows no icons and no background (just white).

---

### Post by derxen on 2012-04-26
You were right, rsavage: to solve the problem of the corruption in the lower half of the screen, it suffices to set the dimensions of Virtual at 1680x1575. There is no need to disable the other ports. So my xorg.conf now looks like this:
```
Section "Device"
    Identifier    "FX5200"
    BusID        "PCI:240:16:0"
    Driver          "nouveau"
    Option    "Monitor-DVI-I-1" "ADC_Port"
    Option    "Monitor-DVI-I-2" "DVI_Port"
    Option    "Monitor-TV-1" "TV_Port"
EndSection

Section "Monitor"
    Identifier    "ADC_Port"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "FX5200"
        DefaultDepth    24
           SubSection       "Display"
             Depth            24
         Virtual 1680 1575
           EndSubSection
EndSection

```I still have the problem with the missing icons and white background in Ubuntu3d however.

---

### Post by canhoto on 2012-05-02
[IMG]https://picasaweb.google.com/lh/photo/ZXaB9b9gVFu2Fp3IkyYTsdMTjNZETYmyPJy0liipFm0?feat=directlink[/IMG][IMG]https://picasaweb.google.com/106709782110412977030/Adhoc?authuser=0&feat=directlink[/IMG]> **derxen said:**
>  still have the problem with the missing icons and white background in Ubuntu3d however.

I also have this problem with unity, and I have to use unity-2d, which is great, but misses some features of the regular unity. The only difference is that I have the backgrounds.

When you speak about "corruption" of the screen, does it have anything to do with what I have in the picture I attach? It happens everytime I try to change the screen resolution to 1440x900, which should be the right one for the screen I have.


My card is a NVIDIA Geforce 6200.

[IMG]https://lh5.googleusercontent.com/-8xRZqym7cFo/T6HqdLtHWUI/AAAAAAAAAa8/Z6p8blJekAY/s640/DSC_0136.JPG[/IMG]

[IMG]https://picasaweb.google.com/lh/photo/ZXaB9b9gVFu2Fp3IkyYTsdMTjNZETYmyPJy0liipFm0?feat=directlink[/IMG]

[IMG]https://picasaweb.google.com/106709782110412977030/Adhoc?authuser=0&feat=directlink[/IMG]

---

### Post by derxen on 2012-05-03
I can't really see it in the picture, but what happens is that blocks of text will be missing. Have you tried changing the virtual screen size?

---

### Post by canhoto on 2012-05-03
> **derxen said:**
> I can't really see it in the picture, but what happens is that blocks of text will be missing.

Yes, that's because the screen is black and the image that covers one third oof it is a black background. What happens is that the desktop is shifted to the left, and to upper right and right edges of the screen are just a black background, trimming a good part of the  desktop.

> **derxen said:**
> Have you tried changing the virtual screen  size?

Actually, no. How do I do that?

---

### Post by derxen on 2012-05-03
That does sound different from what I experienced. You can try that xorg.conf that I posted a few messages ago. It goes in /etc/X11/xorg.conf 
But if your corruption is not in the bottom half, it won't help. I don't know whether you can change the virtual dimensions so that it is covered, I'm not an X expert.

---

### Post by guiguima on 2012-11-08
I'm experiencing the same corruption issue on my PowerBook G4 running ubuntu 12.04
I'd like to have some more informations about how to modify the Xorg.conf file provied in this topic for my computer. Where do i need to start ?

Thank you in advance.

---


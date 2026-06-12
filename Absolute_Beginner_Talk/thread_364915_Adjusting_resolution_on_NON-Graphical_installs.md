---
title: "Adjusting resolution on NON-Graphical installs"
date: 2007-02-18
forum: Absolute Beginner Talk
---

### Post by Betard on 2007-02-18
Hello,

I installed "ubuntu-6.06.1-server-i386.iso" on a dedicated (no dual boot) machine a couple of days and I am NOT using any kind of graphical interface like gnome, etc...

the box is essentially made up of some spare parts kicking around the house with the exception of a video card. So after some reading it seems that nvidia was a preferred brand for linux installs and so I purchased a "GeForce 6200 XfX" agp card.

my Display is a Dell 24" WS LCD, and naturally the text is HUGE because the resolution seems to be set to 640x480 by default on the install.

Is there any way for me to change this? again this is NOT for a graphical install such as gnome. All I got is a black screen with white text. (sorry for over explaining it, but everytime I try to ask someone they start teling me about shift+ctrl or editing some xorg.conf file that I dont have.)

maybe its a driver issue? or some kind of setup I need to do?

Any help on this would be greatly appreciated, also if someone can simply tell me the proper terminology for my type of install then maybe I would be able to do smarter searches. So far "changing screen resolution" or "CLI resolution" is turning up tons of posts for situations other than mine.

Thanks.  :)

---

### Post by reacocard on 2007-02-18
yes, you need to add vga=791 to your kernel's boot parameters. That's scale the text for 1024x768 instead of the default 640x480. You do this after it is installed, AFAIK, the installer always runs at the default.

---

### Post by Betard on 2007-02-18
> **reacocard said:**
> yes, you need to add vga=791 to your kernel's boot parameters. That's scale the text for 1024x768 instead of the default 640x480. You do this after it is installed, AFAIK, the installer always runs at the default.

sorry if this is a silly question but how do I do that?  and can I set it for bigger
than 1024x 768??  my native resolution for this monitor is 1920x1200, probably
don't need it that big, but I'll take what I can get.

---

### Post by reacocard on 2007-02-18
> **Betard said:**
> sorry if this is a silly question but how do I do that?  and can I set it for bigger
than 1024x 768??  my native resolution for this monitor is 1920x1200, probably
don't need it that big, but I'll take what I can get.

Maybe, if your card supports it. To find out the modes your card supports, we'll need hwinfo (you need to have the universe repository enabled for this):
```
sudo apt-get install hwinfo
```
then do 
```
sudo hwinfo --framebuffer
```
You'll get a bunch of lines like this:
```
  Mode 0x0360: 1280x800 (+1280), 8 bits
  Mode 0x0361: 1280x800 (+2560), 16 bits
  Mode 0x0362: 1280x800 (+5120), 24 bits
  Mode 0x0305: 1024x768 (+1024), 8 bits
  Mode 0x0317: 1024x768 (+2048), 16 bits
  Mode 0x0318: 1024x768 (+4096), 24 bits

```
Find the line with the resolution and bit depth you want, and use its mode number instead of 791. So from the example above, if you wanted 1280x800 with 8-bit usecolor depth, you would add vga=0x0360 to your kernel parameters.

To add it to your kernel parameters, do a 
```
 sudo nano /boot/grub/menu.lst 
```
find the line like this
```
 # defoptions=quiet splash 
```
and add it like this
```
 # defoptions=quiet splash vga=791 
```
Save the file (CTRL+O) and exit (CTRL+X), then do
```
 sudo update-grub 
```

---

### Post by Betard on 2007-02-18
perfect I will give that a shot, as a side note setting an alternate resolution for display wont harm the lcd or the system itself will it?

I read a couple of posts saying to "be careful" when changing the resolution since it might damage the display... although I dont see/understand how it could.

Thanks

---

### Post by CattyKid on 2007-02-19
Hello.  I have a similar question, if I may.  Today I purchased a GeForce FX 5500 card as well as a new 19 inch monitor which operates at 1440*900.  I followed the steps listed to get this output:
```
eric@eric-desktop:~$ sudo hwinfo --framebuffer
02: None 00.0: 11001 VESA Framebuffer                           
  [Created at bios.440]
  Unique ID: rdCR.xJo0qtMPBs8
  Hardware Class: framebuffer
  Model: "NVIDIA NV34 Board - p162-11n"
  Vendor: "NVIDIA Corporation"
  Device: "NV34 Board - p162-11n"
  SubVendor: "NVIDIA"
  SubDevice: 
  Revision: "Chip Rev"
  Memory Size: 256 MB
  Memory Range: 0xd0000000-0xdfffffff (rw)
  Mode 0x0300: 640x400 (+640), 8 bits
  Mode 0x0301: 640x480 (+640), 8 bits
  Mode 0x0303: 800x600 (+800), 8 bits
  Mode 0x0305: 1024x768 (+1024), 8 bits
  Mode 0x0307: 1280x1024 (+1280), 8 bits
  Mode 0x030e: 320x200 (+640), 16 bits
  Mode 0x030f: 320x200 (+1280), 24 bits
  Mode 0x0311: 640x480 (+1280), 16 bits
  Mode 0x0312: 640x480 (+2560), 24 bits
  Mode 0x0314: 800x600 (+1600), 16 bits
  Mode 0x0315: 800x600 (+3200), 24 bits
  Mode 0x0317: 1024x768 (+2048), 16 bits
  Mode 0x0318: 1024x768 (+4096), 24 bits
  Mode 0x031a: 1280x1024 (+2560), 16 bits
  Mode 0x031b: 1280x1024 (+5120), 24 bits
  Mode 0x0330: 320x200 (+320), 8 bits
  Mode 0x0331: 320x400 (+320), 8 bits
  Mode 0x0332: 320x400 (+640), 16 bits
  Mode 0x0333: 320x400 (+1280), 24 bits
  Mode 0x0334: 320x240 (+320), 8 bits
  Mode 0x0335: 320x240 (+640), 16 bits
  Mode 0x0336: 320x240 (+1280), 24 bits
  Mode 0x033d: 640x400 (+1280), 16 bits
  Mode 0x033e: 640x400 (+2560), 24 bits
  Mode 0x0345: 1600x1200 (+1600), 8 bits
  Mode 0x0346: 1600x1200 (+3200), 16 bits
  Mode 0x0347: 1400x1050 (+1400), 8 bits
  Mode 0x0348: 1400x1050 (+2800), 16 bits
  Mode 0x0352: 2048x1536 (+8192), 24 bits
  Config Status: cfg=new, avail=yes, need=no, active=unknown

```
My resolution is not listed there.  However, under Windows XP, I DO get this resolution.  So, do you know of any reason why I could not achieve this resolution under Linux?  My monitor looks great under Windows and I would like it to look great under Ubuntu as well.

Thanks

---

### Post by Penguin Power on 2007-02-19
> **Betard said:**
> perfect I will give that a shot, as a side note setting an alternate resolution for display wont harm the lcd or the system itself will it?

I read a couple of posts saying to "be careful" when changing the resolution since it might damage the display... although I dont see/understand how it could.

Thanks
Changing the resolution on a CRT to one higher than it is capable of can damage the monitor but afaik that doesn't apply to LCDs (and i assume your lovely 24" dell is the same as my lovely 24" dell = an lcd :) )
> **CattyKid said:**
> Hello.  I have a similar question, if I may.  Today I purchased a GeForce FX 5500 card as well as a new 19 inch monitor which operates at 1440*900.  I followed the steps listed to get this output:
My resolution is not listed there.  However, under Windows XP, I DO get this resolution.  So, do you know of any reason why I could not achieve this resolution under Linux?  My monitor looks great under Windows and I would like it to look great under Ubuntu as well.

Thanks

Both of you should try 
sudo dpkg-reconfigure xserver-xorg
in the terminal and fill in all the settings for graphics - it works for me - only way i can get 1920x1200 on my lovely lovely 24" dell as well ;) 
Although, i'm using GNOME so i don't know if the same solution will apply to you Betard :confused:

---

### Post by mcduck on 2007-02-19
> **Betard said:**
> perfect I will give that a shot, as a side note setting an alternate resolution for display wont harm the lcd or the system itself will it?

I read a couple of posts saying to "be careful" when changing the resolution since it might damage the display... although I dont see/understand how it could.

Thanks
It could, because that will list the resolutions your graphics card is capable, which doesn't meant that your display could handle them all. And trying to feed a display a picture with much bigger resolution or refresh rate than what is supported _can_ damage the display. But as long as you remember your display's limits there's no problem :)

---

### Post by reacocard on 2007-02-19
> **Penguin Power said:**
> Both of you should try 
sudo dpkg-reconfigure xserver-xorg
in the terminal and fill in all the settings for graphics - it works for me - only way i can get 1920x1200 on my lovely lovely 24" dell as well ;) 
Although, i'm using GNOME so i don't know if the same solution will apply to you Betard :confused:

This is irrelevant for Betard, as he is not using an xserver, but would probably help cattykid if he is.  Also, cattykid, hwinfo gives you the modes your card is capable of, not the monitor. Pick the one closest to what you want, which looks like 0x0318. If you have an xserver (GUI), the above tip from Penguin Power should help.

---

### Post by CattyKid on 2007-02-19
> **reacocard said:**
> This is irrelevant for Betard, as he is not using an xserver, but would probably help cattykid if he is.  Also, cattykid, hwinfo gives you the modes your card is capable of, not the monitor. Pick the one closest to what you want, which looks like 0x0318. If you have an xserver (GUI), the above tip from Penguin Power should help.

Oddly enough, I tried that before.  I was given the chance to set the resolution 1440*900 and went through all the steps, typed "startx" and there was no change in the resolution.  I also restarted my manager with "sudo /etc/init.d/dgm start" and it booted fine, but the resolution did not change at all.

---

### Post by reacocard on 2007-02-19
> **CattyKid said:**
> Oddly enough, I tried that before.  I was given the chance to set the resolution 1440*900 and went through all the steps, typed "startx" and there was no change in the resolution.  I also restarted my manager with "sudo /etc/init.d/dgm start" and it booted fine, but the resolution did not change at all.

Odd. Could you please post the contents of your /etc/X11/xorg.conf file after running that command and enabling 1440x900?

---

### Post by Betard on 2007-02-19
Thanks reacocard, Penguin Power & mcduck!!   \\:D/ 

everything described worked perfectly and its nice to not have to stare at giant blocky letters on my display now.

Someone should make this thread, or make a new thread and "sticky it" since it seems there are a TON of people asking about changing resolution.

In my case I was unable to find any information on changing the resolution for non-graphical installs.  But then again it may be my lack of terminology that prevented me from getting the proper search results.

Thanks again, and good luck CattyKid

---

### Post by lukem on 2007-03-04
I'm having a problem very similar to CattyKid.  Same Card FX5500 and a new 1440X900 lcd.  Graphics look fine, but all text is very poor.  It's hard to describe but vertical portions of the text seem to be faded out.  For instance in the word ball you may be able to see one "l" and not the next one.

I have tried sudo dpkg-reconfigure xserver-xorg and managed to get the resolution to 1440 X 900 but still have not been able to cure this text only problem.  

Thanks for any help.

---

### Post by Aliarse on 2007-03-04
For those having problems getting 1440x900, try this thread. :)

[http://www.ubuntuforums.org/showthread.php?t=370204](http://www.ubuntuforums.org/showthread.php?t=370204)

---

### Post by lukem on 2007-03-08
bought a new card and still had problems until I read this

[Https://help.ubuntu.com/community/Fi...esolutionHowto](Https://help.ubuntu.com/community/Fi...esolutionHowto)

It finally explained what all those "Display...Depth....Modes" sections were all about in the xorg.conf and how to fix my final problem.

Thanks to all.

---


---
title: "Questions &amp; Problems"
date: 2013-01-15
forum: Any Other OS
---

### Post by Lightning Dragon on 2013-01-15
Hello,

I have recently installed Linux Mint Nadia on a spare HDD beside my Ubuntu 12.04 install and have liked the simpler menu and easy to find customizations. However, I was looking for a distro that would allow me to  install my graphics card driver ([here]("http://www.nvidia.com/object/unix.html")) and have the OpenGL function work, and a whole bunch of other things.

I managed to install my driver and have gotten [this nice little menu app added]("http://postimage.org/image/xwos8eaqb/")_ (< clickable),_ but whenever I attempt anything that requires OpenGL, it gives me strange errors. I know the card supports it because on Windows it works fine.

Is there anyway I can fix this on this distro, or is there a distro that I can do this on (like Ubuntu?)?

System info;
**Kernel: **Linux 3.5.0-17-generic (i686) 
**Operating System:** Linux Mint 14 Nadia
**Processor:** 2x AMD Athlon(tm) II X2 240 Processor
**Memory:** 3103MB (1527MB used)
**Resolution: **1440x900 pixels
**OpenGL Renderer:** GeForce 6600 LE/PCIe/SSE2/3DNOW! (Legacy Card)
**X11 Vendor:** The X.Org Foundation

Not only am I having the OpenGL problems, but I have problems on boot up that request me to manually recover or skip with "s", and then when I log in a lot of the things in the Software Package Manager does not work [freezes], and .deb files send me around in circles like 1 wants 2 but 2 wants 1 to install etc etc no matter what I do. Also, some WINE options simply won't open.

I use Ubuntu 12.04 for my work and student needs, and would like to get another HDD/Distro for gaming and graphicing for myself and my lil' bro, that's why OpenGL is so important. 

Any and all help would be greatly appreciated.  ):P

Thanks!

[SIZE=1](Also, if you saw my other thread on running RPG Game M[SIZE=1]aker XP[/SIZE], I'd like to update everything that I can emulate it 100% through WINE, only doesn't play MIDI files. Cur[SIZE=1]rently VX Ace is impossible to get work because of [SIZE=1]Internet[/SIZE] connection denials. [/SIZE])[/SIZE]

---

### Post by eenofonn on 2013-01-16
> **Lightning Dragon said:**
> Hello,

I have recently installed Linux Mint Nadia on a spare HDD beside my Ubuntu 12.04 install and have liked the simpler menu and easy to find customizations. However, I was looking for a distro that would allow me to  install my graphics card driver ([here]("http://www.nvidia.com/object/unix.html")) and have the OpenGL function work, and a whole bunch of other things.

I managed to install my driver and have gotten [this nice little menu app added]("http://postimage.org/image/xwos8eaqb/")_ (< clickable),_ but whenever I attempt anything that requires OpenGL, it gives me strange errors. I know the card supports it because on Windows it works fine.

Is there anyway I can fix this on this distro, or is there a distro that I can do this on (like Ubuntu?)?

System info;
**Kernel: **Linux 3.5.0-17-generic (i686) 
**Operating System:** Linux Mint 14 Nadia
**Processor:** 2x AMD Athlon(tm) II X2 240 Processor
**Memory:** 3103MB (1527MB used)
**Resolution: **1440x900 pixels
**OpenGL Renderer:** GeForce 6600 LE/PCIe/SSE2/3DNOW! (Legacy Card)
**X11 Vendor:** The X.Org Foundation

Not only am I having the OpenGL problems, but I have problems on boot up that request me to manually recover or skip with "s", and then when I log in a lot of the things in the Software Package Manager does not work [freezes], and .deb files send me around in circles like 1 wants 2 but 2 wants 1 to install etc etc no matter what I do. Also, some WINE options simply won't open.

I use Ubuntu 12.04 for my work and student needs, and would like to get another HDD/Distro for gaming and graphicing for myself and my lil' bro, that's why OpenGL is so important. 

Any and all help would be greatly appreciated.  ):P

Thanks!

[SIZE=1](Also, if you saw my other thread on running RPG Game M[SIZE=1]aker XP[/SIZE], I'd like to update everything that I can emulate it 100% through WINE, only doesn't play MIDI files. Cur[SIZE=1]rently VX Ace is impossible to get work because of [SIZE=1]Internet[/SIZE] connection denials. [/SIZE])[/SIZE]
Are you using the driver from the link you posted or did you just attempt to install it and are having problems loading it and having to failback to a different driver at boot.  It's been a while since I've had to deal with graphics issues on Linux since I don't really run a desktop on any of my Linux machines anymore.

---

### Post by Lightning Dragon on 2013-01-16
Hello and thanks for the reply,

I installed [this]("http://www.nvidia.com/object/linux-display-ia32-304.64-driver.html") driver for my LE card (the "this" is clickable) and it worked fine (also won't accept any other driver). At first I tried another way before this attempt and it resulted in just "failures", but didn't do anything to the computer. But then I was redirected to Nvidia's official page, grabbed the file and then installed it and it went very smoothly.

The graphics card is installed, I think, and that's why I can view the nvidia X-settings, however it doesn't let OpenGL work or recognize it. I'm not sure what the problem is, but here is an example of one of the OpenGL problems;

If I run some Photoshop CS filters, I get errors concerning glColorMaskIndexedEXT or that my card may not support OpenGL and If my brother attempts to run his games, he gets the same things.

As far as I can see, the boot menu is not asking me to fall back to any previous drivers or anything, and loads into Mint fine afterwards. I just get that error on boot and when the system turns off. Also, cli's menu (I believe that is the name of it) resolution has become zoomed in as well.

---

### Post by eenofonn on 2013-01-16
what's the output of glxinfo in a terminal

---

### Post by Lightning Dragon on 2013-01-16
Hello,

The output is very big, so here is a link to a place called pastebin so the page doesn't stretch. :)

[http://pastebin.com/0C0iSWxX](http://pastebin.com/0C0iSWxX)

---

### Post by eenofonn on 2013-01-16
hmmm it looks like glx is working what about glxgears does that work?

---

### Post by Lightning Dragon on 2013-01-16
Hello,

Yes, the spinning wheels appear and an output like this is given;

> Running synchronized to the vertical refresh.  The framerate should be
approximately the same as the monitor refresh rate.

300 frames in 5.0 seconds = 59.873 FPS
298 frames in 5.0 seconds = 59.554 FPS
299 frames in 5.0 seconds = 59.743 FPS

That continues to develop new frames that stay around 280-300 frames.

---

### Post by eenofonn on 2013-01-16
hmmm... sounds to me like opengl is running fine... you mentioned photoshop are you running that in wine?

---

### Post by Lightning Dragon on 2013-01-16
Hello,

On Linux Mint, I had it installed through wine, yes. I uninstalled it this morning (to get the key unregistered, which took me hours of aid from adobe) when I did a fresh install of Mint. On Ubuntu, which I have not y et attempted to install drivers for the lack of knowledge, I just installed the exe following a tutorial on the Internet.

---

### Post by eenofonn on 2013-01-16
ok... sounds like opengl is working fine for linux... not for wine though... that's a whole different story

---

### Post by Lightning Dragon on 2013-01-16
Hello,

Here is an update. Although the OpenGL still has issues in Photoshop and other places, my brother installed his game through PlayOnLinux (called Team Fortress) and through PlayOnLinux it got past his OpenGL errors. But, if he tries to launch the game without PlayOnLinux, he can click the game but is given the error.

This is strange. Could it be that outside of Wine or PlayOnLinux permissions to the nvidia folder is sealed off or something?

---

### Post by eenofonn on 2013-01-16
I believe PlayOnLinux uses their own custom wine system so it could still be a wine issue... here's a though if you don't mind downloading another game urban terror or xonotic should play natively on mint if they run fine then it's a wine related problem for sure

---

### Post by Lightning Dragon on 2013-01-16
Hello,

I will certainly give it a shot. If it fixes me not having to use POL to get OpenGL support, then I will do it. Just to be sure, I download these games in POL, right?

---

### Post by eenofonn on 2013-01-16
no download them directly to the linux mint install

---

### Post by Lightning Dragon on 2013-01-16
Hello,

Alright, I downloaded Urban Terror and will update this post/thread when it is done because it is going to take a while to download and install.

EDIT:

It is installed, but it only has an option to open the game under WINE or POL.

EDIT 2:

Had to reboot, set as executable and then ran it native to Linux. It runs *perfectly* fine. Should I test the other game too?

---

### Post by Lightning Dragon on 2013-01-17
Hello,

Since I got Urban Terror to run, I thought I should just go ahead and try xonotic. It seems to be running fine, too. But I still do not have OpenGL support outside of WINE or PlayOnLinux.

---

### Post by eenofonn on 2013-01-17
> **Lightning Dragon said:**
> Hello,

Since I got Urban Terror to run, I thought I should just go ahead and try xonotic. It seems to be running fine, too. But I still do not have OpenGL support outside of WINE or PlayOnLinux.
Correction,

You've got OpenGL working fine OUTSIDE of wine/POL but you need it working INSIDE wine/POL

I'd suggest looking at this site (I do not run Wine or PlayOnLinux so from here out I'm not much help) :(

[WineHQ - OpenGL]("http://www.winehq.org/docs/winedev-guide/opengl")

---

### Post by Lightning Dragon on 2013-01-17
Hello,

Well, it seems to work fine *in* wine and POL, but if I attempt any of the OpenGL needs outside of it, I get OpenGL issues such as 'glColorMaskIndexedEXT'.

---

### Post by eenofonn on 2013-01-17
> **Lightning Dragon said:**
> Hello,

Well, it seems to work fine *in* wine and POL, but if I attempt any of the OpenGL needs outside of it, I get OpenGL issues such as 'glColorMaskIndexedEXT'.
What are you trying to do that is giving you the problem? If UrbanTerror plays fine natively in linux they you are in fact using OpenGL outside of wine or POL.  What application or command is giving you the error

---

### Post by Lightning Dragon on 2013-01-17
Hello,

A lot of things. Photoshop, some native made games (RM and Game Maker that had costume scripts in them), some online games and Steam for my lil' bro.

Running the command glxgears results in a box appearing with spinning gears, but I get this error;

> 
Running synchronized to the vertical refresh.  The framerate should be approximately the same as the monitor refresh rate.
XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0" after 47 requests (47 known processed) with 0 events remaining.


---

### Post by Lightning Dragon on 2013-01-20
Hello,

Slowly my install of Mint seemed to be breaking over the course of this horrendous problem. Last night it started asking me to configure my graphical interface on boot before I got MDM to run again, nothing seems to fix this. So I turned the system off, removed my external GPU and am now using my integrated GPU (NVIDIA GeForce 6150SE nForce 430) and it booted into Linux Mint perfect (minus the no OpenGL support and a worse graphical support now).  It is weird because the integrated GPU uses the same driver as the external GPU, and has no problems. So I'm guessing it is the GPU itself that is having problems with the driver?

Does anyone know a way around it? If not, how can I get OpenGL support through my on board graphics?

Thanks,

---


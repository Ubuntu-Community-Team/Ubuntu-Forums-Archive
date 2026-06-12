---
title: "Open Ati Drivers on PowerPC"
date: 2006-11-20
forum: Apple PPC Users
---

### Post by applemacmad on 2006-11-20
I was wondering what is currently possible with the open Ati drivers on PowerPC. I have heard of people running XGL etc on their PPC hardware and In assume you need 3D acceleration for that.
I have a mobility Radeon 9700, which according to their website, is one of the working cards

Thanks for any help!

---

### Post by bogoliubov on 2006-11-20
> **applemacmad said:**
> I was wondering what is currently possible with the open Ati drivers on PowerPC. I have heard of people running XGL etc on their PPC hardware and In assume you need 3D acceleration for that.
I have a mobility Radeon 9700, which according to their website, is one of the working cards

Thanks for any help!

I run AIGLX (included in Edgy) on my iBook G4. Sometimes it's buggy and it could be a little bit faster, but it works ok. I mainly use it for switching programs and such (like in OS X).


You can check the manpage for the radeon driver to see how to set up xorg.conf (just type man radeon). There might be some template files for your machine, google or search these forums.

Good luck!

---

### Post by ssam on 2006-11-20
run
```
glxinfo
```
in a terminal

look for the line 
```
direct rendering: Yes
```
if it yes then you have 3d accelleration

aiglx is enabled be default in edgy, so all you need to do is install compiz, and set it up to start automatically.

also there is a bug in the edgy xorg, see [https://launchpad.net/distros/ubuntu/+source/compiz/+bug/58373](https://launchpad.net/distros/ubuntu/+source/compiz/+bug/58373)

---

### Post by applemacmad on 2006-11-21
Ok, it says I have direct rendering.
How would I go about installing Compiz? Could you point me towards a guide?
Thanks

---

### Post by bogoliubov on 2006-11-21
> **applemacmad said:**
> Ok, it says I have direct rendering.
How would I go about installing Compiz? Could you point me towards a guide?
Thanks

You're probably better of with Beryl than Compiz. There should be several guides available on this forum; have a search at it. I'm not sure exactly what steps one needs to do to get it working.

Make sure that your xorg.conf is well optimized for your graphics chip; this will make a big difference, even with the Opensource driver "radeon". 
Also, if AIGLX/Beryl feels slow, I recommend turning of some of the bells and whistles. I only use a few features and it's much faster.

---

### Post by macintux on 2006-11-22
I have a Radeon 9600 on my iMac G5(Rev.B), I ran this command:
sudo dpkg-reconfigure xserver-xorg
Then I have selected ati as driver and 1440x900 as maximum resolution and 24 bit as color depth. However it still seems to be 16bit and moving a window can cause the cpu usage to 100%!
Are these problems normal with PowerPC drivers?
Sorry fo my bad English.

---

### Post by APU on 2006-11-22
Read this post for enjoying "real" 24 bit colors

[http://www.ubuntuforums.org/showthread.php?t=303366](http://www.ubuntuforums.org/showthread.php?t=303366)

Although there are only Nvidia cards mentioned there i think that it is not really about the graphics card but rather about Apple using cheaper Laptop style Displays in the iMacs. Many of these displays offer only 6 bit of native color resolution compared to 8 bit which are needed for real 24 bit colors (8 for each: red, green and blue)

The FBDither Option takes care of the necessary color correction! Just remove the option again if the colors look even worse afterwards. By the way, you have to restart X11 to activate this hange (or the computer if you dont know hot to restart X11).

---

### Post by macintux on 2006-11-22
Thanks a lot for your reply.
It seems that ATi Radeon driver has a similiar option:
[quote="radeon manpage"]Option "Dac6Bit" "boolean" 
Enables or disables the use of 6 bits per color component when in 8 bpp mode (emulates VGA mode). By default, all 8 bits per color component are used. 
The default is off.[/quote]
However I cant see any difference, before and after adding:
Option "Dac6bit" "true"
But I can see a little quality difference between 16bit and 24bit regardless of adding or removing that "Dac6bit"... line.
--
I think Dac6bit Option does not work as it should be on my iMac G5, maybe due to a bug.
BTW, I took a Screenshot from my Ubuntu Desktop and Mac OS X Tiger's Preview.app can show the screenshot/image with correct colors!

---


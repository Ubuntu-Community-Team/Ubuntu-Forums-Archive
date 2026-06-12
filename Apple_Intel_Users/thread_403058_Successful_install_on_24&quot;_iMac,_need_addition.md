---
title: "Successful install on 24&quot; iMac, need additional help."
date: 2007-04-06
forum: Apple Intel Users
---

### Post by nateDEEZY on 2007-04-06
Well I've got a 24" iMac with the standard Nvidia 7300gt. My only problem right now is the max resolution, it's stuck at 1024x768. As far as I know I need to get the drivers for the graphics card and probably for the display, but I don't know where to even begin.

After searching most of the installs I've seen have been on Core Duo iMac's with Ati graphics cards and on MacBooks and MBP's with the integrated Intel graphics cards and the Ati graphics cards.

Also, the only other problem I've experienced was when I tried to enable desktop effects, the screen just went white for a minute or so then returned back to normal. I'm assuming it's because of the lack of proper drivers for the graphics card/display.

I was glad to see the apple keyboard works, in regards to volume +/- and eject xD

Any help would be greatly appreciated!

---

### Post by cyberdork33 on 2007-04-06
Follow instructions to install nvidia drivers as can be found in several places.

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia?highlight=%28Nvidia%29](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia?highlight=%28Nvidia%29)
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28NVIDIA.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28NVIDIA.29)

---

### Post by nateDEEZY on 2007-04-06
> **cyberdork33 said:**
> Follow instructions to install nvidia drivers as can be found in several places.

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia?highlight=%28Nvidia%29](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia?highlight=%28Nvidia%29)
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28NVIDIA.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Graphics_Driver_.28NVIDIA.29)

I forgot to mention that I'm also using Ubuntu Feisty Fawn. So I was wondering if this will all work on it.l

---

### Post by cyberdork33 on 2007-04-06
If not very similar... Doesn't really change. 

Feisty has a new "Restricted Drivers" thing in it for this purpose though

---

### Post by nateDEEZY on 2007-04-07
Well, this morning I had to reinstall ubuntu for a dumb mistake I made last night. :p I tried some ati drivers for whatever reason I thought it might work and it end up destroyinig the gui. 

Well I got it reinstalled again, working fine... Just now I lost sound =/ Well I followed your advice and installed the nvidea drivers, now I get a nice nvidea splash screen right before booting into ubuntu. That's just about it, I'm still suck at 1024x768.

Anyone else have any suggestions?

Update: after opening the xorg.conf file i see that it knows what type of graphics card i have. That's progress I suppose.. I guess I may need drivers for my monitor?

---

### Post by Starchild on 2007-04-08
sudo dpkg-reconfigure xserver-xorg

---

### Post by cyberdork33 on 2007-04-09
> **Starchild said:**
> sudo dpkg-reconfigure xserver-xorg

Yep, and if that doesn't do it, you can add the resolutions to the xorg.conf manually.

---


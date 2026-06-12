---
title: "New Install"
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by nightowl512 on 2007-02-25
I am getting ready to install ubuntu, does anyone know if the nvidia drivers work with a G force 6100 onboard video?

Also, I have 2 HD's one for XP, and the other one is going to be for ubuntu.  I was thinking about formatting 2 or 3 gigs on the Linux hd as fat32 so that I could easily swap file back and forth between Linux and xp.  Is this a good idea and will it work like I think it will?

---

### Post by Mornedhel on 2007-02-25
The files on your common vfat partition will indeed be readable/writable safely by either OS. You might get some errors now and then when writing with Ubuntu, because Linux tries to use the file permissions as it would on an ext* filesystem, but nothing to worry about.

As for the NVidia, I have no idea. I believe some compatible cards are listed in the nvidia driver package, check it out in Synaptic.

---

### Post by Maestro23 on 2007-02-25
> **nightowl512 said:**
> I am getting ready to install ubuntu, does anyone know if the nvidia drivers work with a G force 6100 onboard video?

Also, I have 2 HD's one for XP, and the other one is going to be for ubuntu.  I was thinking about formatting 2 or 3 gigs on the Linux hd as fat32 so that I could easily swap file back and forth between Linux and xp.  Is this a good idea and will it work like I think it will?

This might be the driver for your card: [http://www.nvidia.com/object/linux_display_ia32_1.0-9746.html](http://www.nvidia.com/object/linux_display_ia32_1.0-9746.html)
*Check for yourself at the site, just to make sure.

If you are not good with command line, there is a script called Envy that will install the driver for you.  Can get it here: [http://lunapark6.com/?p=2717](http://lunapark6.com/?p=2717)

Just follow his directions.  Good luck.

---


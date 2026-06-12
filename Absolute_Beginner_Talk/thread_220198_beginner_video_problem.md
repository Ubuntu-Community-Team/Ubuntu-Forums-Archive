---
title: "beginner video problem"
date: 2006-07-21
forum: Absolute Beginner Talk
---

### Post by danne on 2006-07-21
hi!
I recently installed ubuntu 6.06 and it's great. Only 1 problem though...
My video card..
I tried to reconfigure xorg (dpkg-reconfigure xserver-xorg) and he automatically pointed out my card (ati mobility x600) but I still can't go for a resolution higher than 1024*768 and those VGA settings are shite](*,) 
I would like to see that fixed (with direct3D working:cool: )

thx!!

---

### Post by bigken on 2006-07-21
When you run sudo dpkg-reconfigure xserver-xorg did you use the space to select your resolution ;)

---

### Post by lzfy on 2006-07-21
In xorg.conf change your "vesa" driver to "ati", next add your desired resolutions to the same file. This works but it won't give you 3D.

---

### Post by nalmeth on 2006-07-21
Didn't you add the resolutions you wanted?

Does your card support 3D? I don't know much about ATI cards, here's a howto if you can do 3D:

[http://wiki.serios.net/wiki/Ubuntu_ATI_proprietary_display_driver_installation](http://wiki.serios.net/wiki/Ubuntu_ATI_proprietary_display_driver_installation)

---

### Post by adam.tropics on 2006-07-21
The above wiki link is ok, but not quite complete at the moment...may I reccomend method 1 in [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

that should give you the 3d, and at least your cards/monitors default resolution.

---


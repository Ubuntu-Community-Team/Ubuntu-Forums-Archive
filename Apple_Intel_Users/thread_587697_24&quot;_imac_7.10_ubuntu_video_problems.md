---
title: "24&quot; imac 7.10 ubuntu video problems"
date: 2007-10-23
forum: Apple Intel Users
---

### Post by darksquirrel on 2007-10-23
Alright i've been going through forums all night and have yet to properly activate my video card to enable the nice graphical features. I'm fearing maybe the reason is my lack of knowledge with linux, i've been able to follow tutorials only so much then i get strange errors or results. I've installed fglrx...i think, i've pretty much haphazardly thrown lots of commands into terminal that i've gotten from other forums pages and i think i've ended up downloading multiple updates because of that (a new advanced option of desktop video settings opened up, but i still can't seem to enable said effects.)

I downloaded ati's driver file (it's the .run one for linux) given my limited knowledge with linux i just double clicked and got errors. Next i changed the directory and tried the particular terminal command the install guide gave me ```
 sudo bash ati-driver-installer-8.41.7-x86.x86_64.run --buildpkg Ubuntu/feisty
```

it seems to unpackage the file (or whatever it's trying) but, then gives an error and quits whatever it was doing.

Is there anything that could be done to help a less experienced linux user properly enable his graphics card on his 24" imac (newest model, lower end of the 2 24" options).

Thanks in advance to anyone that can help me i've been trying to enable these effects for hours.

---

### Post by clayboy on 2007-10-23
you have to package it yourself if you need help just aim me its clayboidaplyboi
:)

---

### Post by darksquirrel on 2007-10-23
you don't seem to be online. How exactly do you package something? Then will i only have to install it?

---

### Post by darksquirrel on 2007-10-23
Any ideas yet? I think i've advanced a bit farther. I turned that .run file into packages and i think i installed those/ But i still can't access the restricted drivers management options, it just says i don't need any restricted drivers. Can anyone help?

I still can't enable the advanced desktop effects and by what i can tell it's possible on my 24" mac. I've been trying for hours does anyone have any advice?

---

### Post by cyberdork33 on 2007-10-23
Using the downloaded ATI drivers will not show in restricted drivers manager. I am assuming you are on an Aluminum iMac.

This should help too:
```
sudo bash ati-driver-installer-8.41.7-x86.x86_64.run --buildpkg Ubuntu/**gutsy**
```

For full steps to install these drivers MANUALLY... (which is what you need) check out the following:
This is for Gutsy (7.10), but has a different driver version be sure you type the commands with your newer driver version:
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_8.40.4_Driver_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_8.40.4_Driver_Manually)

This is the right driver version, but for Feisty. These two should give you enough information:
[http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide#Method_2:_Install_the_8.41.7_Driver_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide#Method_2:_Install_the_8.41.7_Driver_Manually)

---

### Post by darksquirrel on 2007-10-23
Yes I'm using a newer aluminum Imac. I re-installed Ubuntu to give things a fresh start and now i'm getting an error during installation that i didn't get previously. It happens when i attempt to install (or package) the ati drivers.

```
sudo bash ati-driver-installer-8.41.7-x86.x86_64.run --buildpkg Ubuntu/gutsy
```

I recieve the following error

```

 ATI Technologies Linux Driver Installer/Packager 
==================================================
Generating package: Ubuntu/gutsy
./packages/Ubuntu/ati-packager.sh: 175: dpkg-architecture: not found
**Error: unsupported architecture:** 
Removing temporary directory: fglrx-install.h14066

```

also what steps do i take after installing the drivers to then enable advanced visual features in ubuntu?

Currently it states that it's unsupported and my graphics card is listed as 
"VESA-generic Vesa-complient card"

when it's in fact the hd2600 ati.
Thanks in advance you've all been very helpful so far.

---

### Post by nelq on 2007-10-23
1) If you're using Gutsy, you will have to wait for the support of the 2.6.23 kernel in the driver (support for 2.6.23 is coming  in the 8.43 driver). Just to inform you, it was not added because of some problems on the x86_64 arch.

More infos at [http://www.phoronix.com]("http://www.phoronix.com")

2) The workaround is to downgrade the kernel to 2.6.22 (more complete procedure in the phoronix forums)

On another note, iirc, once you install manually the Ati driver, you should not attempt to use(enable) the restricted drivers module.

I am glad Ati/AMD finally released the new updated opengl drivers for linux.

---

### Post by cyberdork33 on 2007-10-23
ok before going too much farther, there were new ATI drivers just released (8.42) get those first. follow the same procedure in my linked how to.

Gutsy does not use linux 2.6.23 (yet), so that is not an issue. (unless you get your kernel from some other source).

---


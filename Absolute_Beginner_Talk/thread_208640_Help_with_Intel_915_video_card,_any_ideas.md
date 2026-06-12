---
title: "Help with Intel 915 video card, any ideas??"
date: 2006-07-03
forum: Absolute Beginner Talk
---

### Post by chonzy on 2006-07-03
I have an Intel 915 video card in my laptop a Dell Inspiron 1300, so i installed Steam (Counter Strike, Half Life) and executed counter strike, and i realised that i dont have 3D support, I mean, when i used to have windows, in this same laptop, everithing worked fine, the FPS where over 60, and now im getting something like 20 fps or less.

I tried downloading the lastest drivers at Intel's website, but they come in a .tar.gz package with no readme and with an .sh installer that wont execute when i try "sudo sh intaller.sh"...

Any ideas???:confused: :confused: :confused: :confused:

---

### Post by chonzy on 2006-07-03
**Bump**

---

### Post by chonzy on 2006-07-04
**Bump**

---

### Post by MarkSheely on 2006-07-04
Chonzy, Look here:

[http://ubuntuforums.org/showthread.php?t=147915&highlight=intel+915+drivers](http://ubuntuforums.org/showthread.php?t=147915&highlight=intel+915+drivers)

If, after changing "vesa" to "i810" things don't improve, post back again, and we'll try something else.

--Mark

---

### Post by chonzy on 2006-07-05
> Section "Device"
	Identifier	"Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"

It was already changed when I cheked, and still no improvement...

Any other ideas???

---

### Post by xrchris on 2006-07-05
Have you installed the 915resolution package from the repositories and followed the instructions on the enclosed 'Read Me' file?

---

### Post by chonzy on 2006-07-05
I did install the 915resolution pack, but I've never read the readme, how can i open it?? The only thing I've done with 915resolutions is to follow a tutroial on how to get 1280x800 resolution in my laptop, which worked great.

This is the tutorial I followed:

> Most likely you will only be able to select 1024×768 (which isn't a widescreen resolution, so things get all distorted) from the Gnome screen resolution utility. Here is what I did to enable the native resolution 1280×800:

Download and install 915resolution, which is a hack to the Intel graphics chip driver that enables widescreen support:

wget [http://ftp.de.debian.org/debian/pool/main/9/915resolution/915resolution_0.5-1_i386.deb](http://ftp.de.debian.org/debian/pool/main/9/915resolution/915resolution_0.5-1_i386.deb)
dpkg -i 915resolution_0.5-1_i386.deb

Add the following line to /etc/init.d/bootmisc.sh:

915resolution 58 1280 800

Edit /etc/default/915resolution and set MODE=58, XRESO=1280 and YRESO=800. Reboot the system and the correct resolution should be enabled (if not, you should be able to select it from the Gnome utility).

If it still doesn't work, check that in the Section "Screen" in /etc/X11/xorg.conf, for every SubSection "Display", the only mentioned resolution is "1280x800". For some reason it didn't work here with other resolutions mentioned.

---

### Post by Jagot on 2006-07-05
This is in the wiki:

[https://help.ubuntu.com/community/i915Driver](https://help.ubuntu.com/community/i915Driver)

Don't know if that would be of any more help.

---

### Post by chonzy on 2006-07-05
> This is in the wiki:

[https://help.ubuntu.com/community/i915Driver](https://help.ubuntu.com/community/i915Driver)

Don't know if that would be of any more help.

This is similar to what i did, thx anyways ;)

---

### Post by chonzy on 2006-07-05
**Bump**

---

### Post by xrchris on 2006-07-09
You need to follow the instructions given in the following post making changes only for your own resolution settings. 

[https://help.ubuntu.com/community/i915Driver#head-6fcd801a3621b9769f7bf9f48fa4e3ad6e256654](https://help.ubuntu.com/community/i915Driver#head-6fcd801a3621b9769f7bf9f48fa4e3ad6e256654)

Further advice for this can also be sought at [http://www.geocities.com/stomljen/](http://www.geocities.com/stomljen/)  and the README is also listed on that page.

---


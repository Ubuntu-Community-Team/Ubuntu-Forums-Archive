---
title: "Dell Inspiron B130 Brightness"
date: 2007-08-10
forum: Absolute Beginner Talk
---

### Post by speaker219 on 2007-08-10
I have a Dell Inspiron B130. There was a tool on Windows called something like the Intel Graphics Manager that allowed me to adjust the brightness/contrast of the screen via a control panel. I know the Fn keys control brightness, but in this control panel, I had alot more control and was able to get alot larger brightness differences by using the control panel.
Is there any way to get something like this on Ubuntu?

Thanks

---

### Post by speaker219 on 2007-08-10
Just to clarify, the brightness is way too bright. It burns my eyeballs out and even the lowest setting does not help. I'm really missing this control panel. I attached a screenshot of the control panel on windows.

---

### Post by Hospadar on 2007-08-10
Have you looked into proprietary drivers for the intel hardware managing the graphics?  I can't say I know that much about intel graphics hardware as I've always used nvidia, but I know with nvidia, the proprietary drivers give a lot more control over that sort of thing.

There might also be something you can change in the /etc/X11/xorg.conf file to lower the brightness.

Also try the brightness applet which can be added to you panel by right-clicking on the top panel and going to "add to panel"

---

### Post by speaker219 on 2007-08-10
Brightness panel applet doesn't work.

---

### Post by speaker219 on 2007-08-10
Where could i find a propitery driver? btw, my graphics chipset is the Intel 845 integrated

---

### Post by Hospadar on 2007-08-10
I believe [this]("http://downloadcenter.intel.com/Detail_Desc.aspx?agr=Y&ProductID=865&DwnldID=12300&strOSs=39&OSFullName=Linux*&lang=eng") is what you want.  give it a try

---

### Post by speaker219 on 2007-08-10
Thanks. I downloaded it, but its an exe file, do i unzip it, or run it through wine or something? can you help me get this to work correctly on ubuntu? i'm on 7.04 fesity.

---

### Post by speaker219 on 2007-08-10
Bump

---

### Post by Jamie Jackson on 2007-08-10
**Edit: I just realized that you've got the 845 and I have the 945. The following thread is probably useless for you.**

I'm not sure this is applicable, and I haven't done this myself, but I got this from [this Perl script]("http://sourceforge.net/project/showfiles.php?group_id=191254").
```

sudo aptitude install alien
wget -nc http://downloadmirror.intel.com/df-support/9726/eng/dri-Intel-3.4.3006-20051209.i386.rpm
sudo alien dri-Intel-3.4.3006-20051209.i386.rpm
sudo dpkg -i dri-intel_3.4.3006-20051210_i386.deb
# replace /etc/X11/xorg.conf's 
#Section "Device"
#    Identifier     "Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller"
#    ....
#EndSection
#...with
Section "Device"
	Identifier	"Intel Corporation Mobile Integrated Graphics Controller"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	VideoRam	229376
	Option  "XAANoOffscreenPixmaps"
EndSection
```

For my own reference, here's [my thread]("http://ubuntuforums.org/showthread.php?t=517754") asking the same thing that you did.

---

### Post by speaker219 on 2007-08-11
Thanks, i do have the 945, i made a typo. trying it now, thanks ALOT!

---

### Post by speaker219 on 2007-08-11
OK, i just did it, and it's exactly the same :( am i supposed to go somewhere to control brightness?

---

### Post by speaker219 on 2007-08-11
*bump*
giggity

---

### Post by Jamie Jackson on 2007-08-11
Unfortunately, I don't know. The nvidia one puts its applet in System > Preferences, I believe, but I don't know about the Intel version. I'm hoping someone jumps in and gives more information.

---

### Post by speaker219 on 2007-08-12
OK

/discrete way of bumping thread

---

### Post by speaker219 on 2007-08-12
I FIXED IT!!! ;) Pardon me, i'm very excited ;)

Anyway, here's how i fixed it. I was googling and found this program:
[http://www.softpedia.com/get/Tweak/Video-Tweak/Gamma-Panel.shtml](http://www.softpedia.com/get/Tweak/Video-Tweak/Gamma-Panel.shtml)

It was a windows app, so last resort i figured, hey, i might as well sudo apt-get wine and try this out.

To my surprise, IT WORKED! I was able to control brightness, contrast, AND GAMMA!

GO WINE! (AND THE GUY THAT WROTE THE PROGRAM)
Hope this helps anybody with the same problem

---

### Post by Jamie Jackson on 2007-08-13
I wish it were pure Linux, but that's a great (and simple) app, and an excellent workaround.

Thanks!!

---


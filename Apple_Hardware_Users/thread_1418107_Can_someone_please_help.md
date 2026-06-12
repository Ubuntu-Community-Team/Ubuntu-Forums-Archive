---
title: "Can someone please help????"
date: 2010-02-28
forum: Apple Hardware Users
---

### Post by jazzlukejosh on 2010-02-28
I have an iMac G3 PowerPC I've installed Ubuntu 9.10 and the computer works better and faster but can't get true colour display. I assume that Xorg on boot up isn't locating the ATI r128 driver and just defaulting to the standard veso driver.

I manually entered five sections in nano xorg.conf ( device, monitor, Screen, Module and Server Layout ) 
 
and pressed control x and y to save but no difference when I rebooted.

The settings I got off the internet were very specific and had spacing and indents which I didn't worry about the indents. But everything was spelt right and quotation marks were made.

When I tried to change the display settings in desktop properties I got the message: 
"the composite extension is not available". 
 
Also can't install flash player or understand how to install any third party software but that's another thread.

---

### Post by byStanderone on 2010-02-28
...is this package installed in your karmic? :
[http://packages.ubuntu.com/karmic/xserver-xorg-video-r128-dbg](http://packages.ubuntu.com/karmic/xserver-xorg-video-r128-dbg)

---

### Post by amrypma on 2010-02-28
check that in...

System -> Administration -> Synaptic Package Manager

if it isn't...
Right click, install, ok and apply.

---

### Post by qwerty2009 on 2010-02-28
as for your flash problem install ubuntu restricted extras

---

### Post by jazzlukejosh on 2010-02-28
thanks I've installed ubuntu restricted extras, now what will that enable me to do, Should I just go ahead and install my flash player, is it going to ask me what to open it with and if it does what should I use?

---

### Post by thatguruguy on 2010-02-28
Unfortunately, flash doesn't work on powerpc macs using ubuntu.

If it's an issue with youtube, there is a work-around.

---

### Post by jazzlukejosh on 2010-02-28
Unfortunately, flash doesn't work on powerpc macs using ubuntu.

If it's an issue with youtube, there is a work-around.



Ok thanks, how do I work around?

---

### Post by jazzlukejosh on 2010-02-28
> **byStanderone said:**
> ...is this package installed in your karmic? :
[http://packages.ubuntu.com/karmic/xserver-xorg-video-r128-dbg](http://packages.ubuntu.com/karmic/xserver-xorg-video-r128-dbg)



I don't know, how can I find out? and what should I do

Sorry I'm a newbie

---

### Post by jazzlukejosh on 2010-02-28
Still getting this damm message where I try to change my screen resoluton in desktop background/appearence preferences/visual effects

"The Composite extension is not available"

can any one tell how to get this composite extention?

---

### Post by linuxopjemac on 2010-02-28
Long story short, there is no good 3D-acceleration with open source ATI driver to enable compiz. I came across [this post]("http://ubuntuforums.org/showthread.php?t=764633&highlight=compiz+fglrx+ati") to help you further.

there is no xserver-xgl for powerpc, otherwise it would be much easier.

---

### Post by byStanderone on 2010-02-28
sudo apt-get install flashplugin-installer

---

### Post by linuxopjemac on 2010-03-01
forget flash. There is no flash for ppc.
[http://mac.linux.be/content/watching-youtube-and-lack-flash](http://mac.linux.be/content/watching-youtube-and-lack-flash)

---

### Post by jazzlukejosh on 2010-03-02
Section "InputDevice"
   Identifier   "Generic Keyboard"
   Driver      "kbd"
   Option      "XkbRules"   "xorg"
   Option      "XkbModel"   "pc104"
   Option      "XkbLayout"   "us"
EndSection
Section "InputDevice"
   Identifier   "Configured Mouse"
   Driver      "mouse"
EndSection
Section "Device"
   Identifier   "ATI Technologies Inc Rage 128 Pro Ultra TR"
   Driver      "r128"
#   Option      "BusID"      "PCI:0000:00:10.0"
#   Option      "Screen"   "0"
#   Option      "VideoRam"   "128000"
#   Option      "MemBase"   ""
#   Option      "IOBase"   ""
#   Option      "ChipID"   ""
#   Option      "SWcursor"   "on"
   Option      "NoAccel"   "on"
#   Option      "Dac6Bit"   "off"
#   Option      "VideoKey"   ""
#   Option      "Display"   "CRT"
   Option      "UseFBDev"   "on"
#   Option      "VGAAccess"   "off"            
EndSection
Section "Monitor"
   Identifier   "Generic Monitor"
   Option      "DPMS"
   HorizSync   59-61
   VertRefresh   75-117
EndSection
Section "Screen"
   Identifier   "Default Screen"
   Device      "ATI Technologies Inc Rage 128 Pro Ultra TR"
   Monitor      "Generic Monitor"
   DefaultDepth   16
   SubSection "Display"
      Depth      1
      Modes      "1024x768"  "800x600"
   EndSubSection
   SubSection "Display"
      Depth      4
      Modes      "1024x768"  "800x600"
   EndSubSection
   SubSection "Display"
      Depth      8
      Modes      "1024x768"  "800x600"
   EndSubSection
   SubSection "Display"
      Depth      15
      Modes      "1024x768"  "800x600"
   EndSubSection
   SubSection "Display"
      Depth      16
      Modes      "1024x768"  "800x600"
   EndSubSection
   SubSection "Display"
      Depth      24
      Modes      "1024x768"  "800x600"
   EndSubSection
EndSection

---

### Post by linuxopjemac on 2010-03-02
so? Did you manage to get Compiz running or not ?

---

### Post by B_Free on 2010-03-03
How the heck did you install 9.10 on your iMac G3? For me, after the progress screen, the screen is black.

---


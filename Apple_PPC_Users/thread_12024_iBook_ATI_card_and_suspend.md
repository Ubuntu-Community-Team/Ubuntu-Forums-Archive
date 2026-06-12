---
title: "iBook ATI card and suspend"
date: 2005-01-21
forum: Apple PPC Users
---

### Post by rvdb on 2005-01-21
Dear All

i installed Ubuntu on my iBook (dual USB) nd it works ! (even sound and suspend).

Alas no hardware acceleration on the graphics ATI card. I have a XF86config file that works (from a gentoo installation). Replacing the XF86config file with the new one indeed shows me great speed with glxgears. But then suspend doesn't work anymore.

I then also see an error message at bootup telling me that the ROM number of aty128fb is not correct (i dont remember seeing that in the first place)

Changing back to the original XF86config file gets rid of the acceleration BUT SUSPEND STILL DOESN'T WORK.

What happened?? 

I would ideally like:

- suspend capability

- hardware opengl

- external VGA screen working....


Can this be done? If not i would sacifice the hardware acceleration first because i DO need the other two.

Any suggestions are welcomed.

Regards
Rein

---

### Post by albersag on 2005-01-21
Which Ati card do you have?

Have you tested propietary drivers from ati website?

---

### Post by stereo on 2005-01-21
is it an ibook g3 or g4 ?

---

### Post by rvdb on 2005-01-21
- i dont think that ATI has drivers for linux ppc (do they??)

- i have a ibook g3 500 MB dual usb, with ATI Rage 128 Mobility M3

Rein

---

### Post by Castaa on 2005-01-21
[QUOTE=rvdb]Dear All
  
  i installed Ubuntu on my iBook (dual USB) nd it works ! (even sound and suspend).
  
 Alas no hardware acceleration on the graphics ATI card. I have a XF86config file that works (from a gentoo installation). Replacing the XF86config file with the new one indeed shows me great speed with glxgears. But then suspend doesn't work anymore.
  
 I then also see an error message at bootup telling me that the ROM number of aty128fb is not correct (i dont remember seeing that in the first place)
  
  Changing back to the original XF86config file gets rid of the acceleration BUT SUSPEND STILL DOESN'T WORK.
  
  What happened?? 
  
  I would ideally like:
  
  - suspend capability
  
  - hardware opengl
  
  - external VGA screen working....
  
  
  Can this be done? If not i would sacifice the hardware acceleration first because i DO need the other two.
  
  Any suggestions are welcomed.
  
  Regards
  Rein[/QUOTE]
  
  
 To get 3D acceleration working with that hardware you need to set your desktop color depth to 16-bit.  I have almost the iBook as you and this worked for me.
  
  Here is a thread on how to do this:
  [http://ubuntuforums.org/showthread.php?t=3723]("http://ubuntuforums.org/showthread.php?t=3723")

---

### Post by chascon on 2005-02-16
no there are no ati drivers for ppc.  Never been, and we've been waiting for a few yrs on that, not that I'd want to use them personally as I have decent support with the generic free drivers.
you might want to try adapting this:
Section "Device"
       	    Identifier	  "Radeon Mobility 9600/9700 M10/M11 (RV350 NP)" 
 		Driver		 "radeon"	 #depending on your card!
       		BusID		   "PCI:0:16:0"
       		VideoRam		65536
 	 Option		 "UseFBDev"			 "true"
       		Option		  "AGPMode" "4"
   		Option		 "AGPFastWrite" "true"
  		Option		 "EnablePageFlip" "true"
 		Option		 "backingstore" "true"	  #this is the interesting part!
       EndSection
and 
Section "Extensions"
       	Option "Composite" "Enable"
  	Option "RENDER" "true"			 
  	Option "DAMAGE" "true"			 
       EndSection

from:
[http://www.ubuntuforums.org/showthread.php?p=71717&posted=1#post71717](http://www.ubuntuforums.org/showthread.php?p=71717&posted=1#post71717)
read the link for the rest of the info.

---

### Post by stereo on 2005-02-16
there's a neat trick to enable the external vga...

turn on your ibook and directly after close the lid during the "booong"

that enables the ext-vga.... afterwards you can open the lid.. it shows white or some  other strange things. the output will be on the vga-out

i had working mirroring on my ibook g3 800 (radeon M7) with linux 2.4.x

anybody with a better solution?

---


---
title: "better grafic-performance on powerbook"
date: 2005-02-07
forum: Apple PPC Users
---

### Post by t.rei on 2005-02-07
Now I know that there are no 3d accelerated drivers available for a powerbook. However me and a friend of mine just experimented a bit with the settings and found the following: (running hoary & xorg)
        
        Modfiying the device section (* /etc/X11/xorg.conf* ):
        
         ```
Section "Device"
       	    Identifier	  "Radeon Mobility 9600/9700 M10/M11 (RV350 NP)" 
 		Driver		 "radeon"	 **#depending on your card!**
       		BusID		   "PCI:0:16:0"
       		VideoRam		65536
 	 Option		 "UseFBDev"			 "true"
       		Option		  "AGPMode" "4"
   		Option		 "AGPFastWrite" "true"
  		Option		 "EnablePageFlip" "true"
 		Option		 "backingstore" "true"	 ** #this is the interesting part!**
       EndSection
``` 
        
        and the extensions section in the same file:
         ```
Section "Extensions"
       	Option "Composite" "Enable"
  	Option "RENDER" "true"			 
  	Option "DAMAGE" "true"			 
       EndSection
``` 
        
        and then restarting xorg by logging out and back in, you get the following:
 Usually when redrawing windows the redraw events tend to be lagging behind. With only this set up - you will not see much of a difference. However after turning on **xcompmgr  **(without parameters) you will notice an impressive increase in the redraw.
        
        Only drawback I found so far: applications like **glxgears** might not be backgrounded. But for the usual daily work this is definately something to enjoy.
        
 Suspend/Resume keeps on working for me right now (running 2.6.9-sleep7) - thats a 2.6.9 with Benjamin Herrenschmidts sleep patch he posted while ago on debian-powerpc mailing list.
        
        To run xcompmgr do this in a terminal:
         ```

      $ > xcompmgr &
      $ > disown
``` 
        
        I hope this might help someone else. :)
        
   edit:
   I tried the some on an 386. same effect - nice fast redraws. :)

---

### Post by chascon on 2005-02-16
would adding in the two darkened options help even on a radeon 9200 or a rage 128?  Both with video accel?

---

### Post by chascon on 2005-02-16
would adding in the two darkened options help even on a radeon 9200 or a rage 128?  Both with video accel?
Or without accel?

---

### Post by chascon on 2005-02-22
Section "Extensions"
       	Option "Composite" "Enable"
  	Option "RENDER" "true"			 
  	Option "DAMAGE" "true"			 
       EndSection

does not work with the nvidia processor GeForce4 MX
(iLamp 17" 800mhz)

nor does it like
Option		 "UseFBDev"			 "true"

nor does the
      $ > xcompmgr &
      $ > disown
do anything as the sytem asks for dri and nv does not work with dri
but the rest seems to mildly perk the system up.

---

### Post by ssam on 2005-02-23
wow, that works pretty well for me on a ti powerbook G4 1GHz, with an ati Radeon Mobility 9000 M9 (according to my xorg.conf).

only problem is that the panel no longer stays ontop of everything.

i had to install xcompmgr from synaptic.

whats the best way to xcompmgr started with X?

ssam

---

### Post by gmc on 2005-02-23
[QUOTE=chascon]Section "Extensions"
       	Option "Composite" "Enable"
  	[B]Option "RENDER" "true"			 
  	Option "DAMAGE" "true"[/B]			 
       EndSection
[/QUOTE]

Tip: The above (bold) options appear to be case sensitive. However on my Nvidia GeForce FX 5200, they certainly do speed up the composite features here. (YMMV).  :-P 

Gord

---

### Post by ssam on 2005-02-23
xcompmgr seems to get slow after a while

---


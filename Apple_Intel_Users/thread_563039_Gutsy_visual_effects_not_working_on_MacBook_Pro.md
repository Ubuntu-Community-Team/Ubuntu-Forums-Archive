---
title: "Gutsy visual effects not working on MacBook Pro"
date: 2007-09-29
forum: Apple Intel Users
---

### Post by xelapond on 2007-09-29
I just installed Gutsy Gibbon(the beta) on my macbook pro, hoping for the by defualt desktop effects.  Where can i find them?  When I go under appearance>>Visual Effects and set Extra(My Macbook Pro can handle that, right?) It says

"The composite extension is not available"

Any idea how I get the visual effects working?  I have a first gen 2.0Ghz Core Duo with 1 gig of ram and 128 Video Ram ATI X1600.

---

### Post by cyberdork33 on 2007-09-30
> **xelapond said:**
> I just installed Gutsy Gibbon(the beta) on my macbook pro, hoping for the by defualt desktop effects.  Where can i find them?  When I go under appearance>>Visual Effects and set Extra(My Macbook Pro can handle that, right?) It says

"The composite extension is not available"

Any idea how I get the visual effects working?  I have a first gen 2.0Ghz Core Duo with 1 gig of ram and 128 Video Ram ATI X1600.

You must get the propietary fglrx driver installed and working. ATI requires XGL to do the compositing, so you have to install that before the effects work.

---

### Post by bcr88 on 2007-09-30
> **cyberdork33 said:**
> You must get the propietary fglrx driver installed and working. ATI requires XGL to do the compositing, so you have to install that before the effects work.

I have a MacBook Pro 2.33 GHz with an ATI X1600. I installed the fglrx drivers and I still get the message: "The Composite extension is not available." when I try to turn on effects.

---

### Post by thully on 2007-09-30
With an ATI card, you have to install the xserver-xgl package (I believe that's what it's called) - or else the 3D effects won't work

---

### Post by cyberdork33 on 2007-09-30
> **thully said:**
> With an ATI card, you have to install the xserver-xgl package (I believe that's what it's called) - or else the 3D effects won't work
Yes, as I stated, you have to use XGL to do the compositing for ATI cards. THe nice thing is that in gutsy you just have to install it, no startup scripts are needed.

---

### Post by xelapond on 2007-10-01
so all I have to do is 

sudo apt-get install xserver-xgl?

That seams too simple:)

---

### Post by cyberdork33 on 2007-10-01
> **xelapond said:**
> so all I have to do is 

sudo apt-get install xserver-xgl?

That seams too simple:)

As long as you have fglrx installed and direct rendering is working, yes! They made it much easier for us in gutsy.

Oh, and restart xorg.

---

### Post by cabomix on 2007-10-29
Hello everyone!
If you installed the ati 8.42.3 Driver or newer,  all you have to do is edit you xorg.conf file to change the "Composite" "0" to "Composite" "1" and you are good to go.

**sudo gedit /etc/X11/xorg.config**
Scroll down to 
[B]Section "Extensions"
	Option		"Composite"	"0"
EndSection[/B]

Change it to

Section "Extensions"
	Option		"Composite"	"1"
EndSection

Save the file 
activate restricted drivers under System>Administration>Restricted Drivers Manager
Reboot
and restart. that is it

**Remember this is for those of you how did your home work and finished installing the latest ATI driver manually and didn't use Envy**

---

### Post by arkizzle on 2007-11-05
Hi gang, I'm in the same situation as Xelapond.

I have everything (ati drivers etc) installed (manually) and xorg.conf modified.

When i choose the effects option with composite option set to 0 i get: "The composite extension is not available".

When i enable the composite option i get: "Desktop Effects could not be enabled."

When i go to the "restricted drivers manager" i'm told "your hardware does not need any restricted drivers".

I'm stuck in a pickle guys, what next?

thanks for any help :D


**edit**  
PS: MacBook Pro, ATI Radeon X1600

---

### Post by cyberdork33 on 2007-11-05
> **arkizzle said:**
> I have everything (ati drivers etc) installed (manually) and xorg.conf modified.
Which version.

---

### Post by maluka on 2007-11-05
for me this is what worked:

System >Administration > Restricted Drivers Manager and enable the ATI accelerated graphics driver

---

### Post by arkizzle on 2007-11-06
@cyberdork33:  

Version 8.42.3 
fresh from horse's udder :D

---

### Post by cyberdork33 on 2007-11-06
> **arkizzle said:**
> @cyberdork33:  

Version 8.42.3 
fresh from horse's udder :D

I would immediately jump to one of two things.

1. you do not have the line enabling composite (and line for AIGLX) in your Xorg.conf (can you post your xorg.conf?)

2. you are still actually using the older version of fglrx (what does fglrxinfo produce?)

It could also be that XGL is still installed and giving you issues as well.

---


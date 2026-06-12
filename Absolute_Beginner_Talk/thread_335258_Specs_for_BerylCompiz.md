---
title: "Specs for Beryl/Compiz?"
date: 2007-01-10
forum: Absolute Beginner Talk
---

### Post by darweth on 2007-01-10
What are the min specs needed to run these comfortably?

I have a pretty crappy video card (Geforce 4MX which is equivalent to only a Geforce 2) and just 512mb ram.  Would it be a drag on my system?  Would something like Evolution be better for eyecandy?  I know Evolution runs on much lower systems.

---

### Post by yager on 2007-01-11
I am running on a p4 2.4GHz with an NVidia Ti4200 w/ 128M video ram.  I have no issues.  Beryl is cool and runs just fine on this.  I do have 1G of memory but my understanding is that the graphic memory is more important as you are really taking advantage the graphic processor.

---

### Post by xolot1 on 2007-01-11
i run beryl on my HP DV8000 laptop (1.8ghz, 512ram, xpress200) and it runs well. 

i also have a second box set up back at college - i use it as a second screen for research and stuff. i got compiz working on that. specs are much lower though, but the eyecandy still works pretty well.  has, i think, 1.0ghz 256ram ati 32agp(aka decade old graphics card, doesnt get too much older).

i suspect that given a processor greater than like 1ghz you should be fine, assuming you can get AIGLX or XGL working.

just my experiences...

---

### Post by Atomic Dog on 2007-01-11
I have it running on a 1.5Ghz celeron laptop with Intel integrated graphics.  Cube rotation is fairly smooth shockingly enough.

---

### Post by Rodneyck on 2007-01-12
> **yager said:**
> I am running on a p4 2.4GHz with an NVidia Ti4200 w/ 128M video ram.  I have no issues.  Beryl is cool and runs just fine on this.  I do have 1G of memory but my understanding is that the graphic memory is more important as you are really taking advantage the graphic processor.

I have a ti4200 w/128M ram on my second computer and can not for the life of me find a nvidia driver that works with it and edgy so I can install Beryl. Currently I am using the .7184 drivers which do not work under beryl.  

Can you tell me what driver version you are using and how you got them installed, a guide, anything...?  

Thanks

---

### Post by darweth on 2007-01-12
[http://doc.gwos.org/index.php/BerylOnEdgy](http://doc.gwos.org/index.php/BerylOnEdgy)

---

### Post by yager on 2007-01-13
I am doing nothing special on the Nvidia driver.  It is the Nvidia-glx driver straight out of the repositiories.  Here is the description straight from the package manager.

> NVIDIA binary XFree86 4.x/X.Org driver
These XFree86 4.x/X.Org binary drivers provide optimized hardware acceleration
of OpenGL applications via a direct-rendering X Server and support the newer
GeForce, nForce and Quadro families of NVIDIA chipsets.  AGP, TV-out and
flat panel displays are also supported.

If you have a TNT, TNT2, or older GeForce, you may need the nvidia-glx-legacy
package instead of this one.

To enable the driver, run "sudo nvidia-glx-config enable".

The version installed is 1.0.8776+2.6.17.7-10.1 (edgy-security)

The device manager reports the card as: NV25 [GeForce4 Ti 4200]

I used to use Automatix to install the graphics driver, but it has gotten much easier so I don't do that anymore.  In the past, everytime the kernel changed, I was having to mess with the xorg.conf file to get everything working again.

I wish it were more complicated, but I have no idea how to make this sound more sexy.

Go to System>Administration>Synaptic Package Manager.
Search for nvidia-glx
Select install

---

### Post by TheMono on 2007-01-13
Crappy dell, integrated Intel Graphics, 512MB Ram, 2.5Ghz celeron (non-mobile), circa two years ago.

Runs like a dream with Beryl.

---

### Post by CroEragon on 2007-01-14
I run Beryl on P4 3.0, 512mb RAM, ATI Radeon XPress 200 integrated graphic card that shares memory with RAM and Beryl is working like charm.
I think Beryl is not so hard for graphic card, you just need to get 3D Rendering, and you can run it.

---

### Post by jordanmthomas on 2007-01-14
Just for the record, Evolution is a mail suite -- not any sort of window manager or desktop environment.

---


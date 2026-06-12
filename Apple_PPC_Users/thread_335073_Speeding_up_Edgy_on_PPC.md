---
title: "Speeding up Edgy on PPC"
date: 2007-01-09
forum: Apple PPC Users
---

### Post by ufugu on 2007-01-09
Hi all,

I've just started posting but I've been using Ubuntu full time (except for a few minutes here and there in MoL) for about six months and want to say thanks to this little Mac corner of the forums and all the great info to be found here.

My only big problem with Ubuntu so far has been performance.  Window dragging is slow and stuttering.  Opening applications takes 10-15 seconds, sometimes longer.  Ripping a CD goes at 2x speed instead of the 7x I get in OSX.  System Monitor is showing no obvious resource hogs.

I've seen the various tips in the forums including [these]("http://ubuntuforums.org/showthread.php?t=189192") but I am wary of trying them on PPC if they are meant for x86.  I'm not afraid to dive in but I really don't want to hose my install for no good reason.

So: what have you all done successfully to speed up your Macs running Ubuntu?

I'm on an iMac G4, 768MB, 800mhz, GeForce2 MX.

Thanks!

---

### Post by 3rdalbum on 2007-01-09
4, 5, 7, 9, and 10 are safe for you to perform on your Mac.

---

### Post by ssam on 2007-01-10
the  Speed up Firefox one should work.

ignore any init-ng stuff, as edgy already has a fancy init replacement called upstart (though it probably wont be until feisty that it really starts to improve boot time.)

you might also want to look at using lighter applications than the defaults. if you dont need all the fancy features of open office, then abiword might suit you. maybe replace nautilus with thunar. i find epiphany faster than firefox.

in system -> administration -> services there are a few things that can be turned off. eg i dont need bluetooth, braille, hp printer support, raid, etc. be carefull turning things off if you dont know what they are.

if you have less that 265mb of ram you will probably see improvements from an upgrade. linux is good a caching disk reads if you have spare ram, so that the second time you access a file it does not have to wait 10ms for the hard disk.

---

### Post by oswaldkelso on 2007-01-10
As ssam says Epiphany is  faster.  Nicer you use IMHO but I need firefox for some plugins 

On my emac g4 I run osx, edgy and debian etch, etch is quite a bit quicker probably as less "stuff" is loaded by default.??

But for real speed Fluxbox!!! and rox-filer.  :)

---

### Post by bogoliubov on 2007-01-12
> **ufugu said:**
> 
My only big problem with Ubuntu so far has been performance.  Window dragging is slow and stuttering.  

How well optimized is your xorg.conf? I don't know how well the PPC drivers for nvidia are doing, but my iBook with Ati card really benefited from optimizing xorg.conf.

---

### Post by ufugu on 2007-01-20
Thanks all for the suggestions.  I thought I should report back.  I spent a lot of time on this and tried just about all of them.

Changing to Fluxbox or changing browsers were not big gains for me.  The things that were slow (see my initial post) were still slow. 

3rdalbum, I tried the fixes on that page that were appropriate.  Prelink helped opening of some apps, tweaking the ext3 file system also helped but it was just barely noticeable.  I couldn't figure out the hdparm/DMA thing at all, so my CD ripping is still crazy slow.  The others didn't do much (I don't have much in the way to clean up on this hard drive, Firefox works fine for me and doesn't seem to matter to other apps if it is active or not, and I had disabled some of the startup services already).  So overall I don't feel like I'm having much success.

bogoliubov, I don't think there's anything I can do with my xorg.conf.  From everything I have read, there are no Nvidia drivers I can use on PPC.  Is that not correct? I have a feeling that is a big source of my slow-woes.  

Even slow though, I love Ubuntu.  I'm thinking since I may not be going back to the Mac OS at all (tough I've been using it since System 6) and there are things for Ubuntu I just can't get working on PPC anyway (Flash, Google Earth, etc etc) that it may be time for me to go x86 anyway. 

Thanks again all for the responses.

---

### Post by ssam on 2007-01-21
> **ufugu said:**
> 
 I couldn't figure out the hdparm/DMA thing at all, so my CD ripping is still crazy slow. 


dma should be turned on automatically these days if your hardware can manage it.

you could try using grip for ripping. it has control for scratch detection, which slow ripping quite a lot

> **ufugu said:**
> 
bogoliubov, I don't think there's anything I can do with my xorg.conf.  From everything I have read, there are no Nvidia drivers I can use on PPC.  Is that not correct? I have a feeling that is a big source of my slow-woes.  

there are not proprietary drivers for nvidia (or ati) for powerpc linux. so you use the open source nv (or radeon for ati) driver.

the nv driver is quite limited, and had no 3d acceleration. hopefully soon the [nouveau driver]("http://nouveau.freedesktop.org/wiki/") will solve these problems.

---

### Post by 3rdalbum on 2007-01-22
> **ufugu said:**
> ...and there are things for Ubuntu I just can't get working on PPC anyway (Flash, Google Earth, etc etc) that it may be time for me to go x86 anyway.

You know, that's what I did. PCs aren't so bad when you run Linux on them. I still campaign for PowerPC versions of binary programs though :-)

---

### Post by ricflomag on 2007-01-29
> **ufugu said:**
> my CD ripping is still crazy slow.

Have you changed /apps/sound-juicer/paranoia to 0 (default value is 8 ) ? You can do it using Gnome Conf Editor. This will speed up CD ripping dramatically.

---


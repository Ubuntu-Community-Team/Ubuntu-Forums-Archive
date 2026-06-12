---
title: "New X-Fi drivers from Creative?"
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by Alastair6 on 2007-10-25
I see that Creative has put up a set of drivers for X-Fi cards for  Linux OS's. 
1. Will they work with Ubuntu 7.10? 
2. How do I install them?
I have downloaded them and tried to install them and I can't seem to figure it out. I'm brand new to Ububntu.
Thanks for any help.

---

### Post by OpposingForce on 2007-10-25
I just DL'ed the drivers as well.  I'm wondering how to install them because the readme install guide is very unclear.  Any help would be appreciated because I refuse to use ubuntu unless I have sound.

---

### Post by MegaJim on 2007-10-25
How about giving us a few clues, like where you got the driver (link to site), which x-fi card you have and any readme/install instructions that came with the download

So looking into this a bit more closely, it seems only 64-bit drivers have been released at this stage - so if you arent running a 64-bit distro you will run into problems ;)

[http://connect.creativelabs.com/linux/Lists/Driver%20Issues/AllItems.aspx](http://connect.creativelabs.com/linux/Lists/Driver%20Issues/AllItems.aspx)

---

### Post by OpposingForce on 2007-10-25
Drivers from here

[http://opensource.creative.com/](http://opensource.creative.com/)

Readme:

> 
================================================== =================


"Sound Blaster X-Fi Linux x86_64 Beta Driver Readme File


September 2007


================================================== ==================


The purpose of this document is to describe how the X-Fi Linux device

driver is built, packaged, and released.



Quick install


=============


1) You must have the fully configured source for the Linux kernel and

ALSA which you
want to use for this device driver. Partial installed

kernels (e.g. From distribution makers) may be unusable for this

action.


2) Run one of the following commands as root in the terminal:

./installer OR


./installer --with-alsainc=<ALSA_include_directory>

* ALSA Source Tree


On 2.6 kernels, the location of the ALSA source include directory


is parsed automatically from the running kernel.


If it is not in the standard place, specify the path via


--with-alsainc=<ALSA_include_directory>.



On 2.4 kernels, the location of the ALSA source include directory


must be specified via --with-alsainc=<ALSA_include_directory>.


* Note

If integrated ALSA is to be used to build, --with-alsainc option


must not be specified."

And I don't have a 64-bit distro...guess no ubuntu for me until it's addressed :(

---

### Post by MegaJim on 2007-10-25
If you're running the 2.6 kernel, extract the archive to a directory, drop into a command and cd into the new directory, then try

```
./installer --with-alsainc
```

and see what happens :-)

---

### Post by Trebaruna on 2007-10-25
Not only do you need a 64 bit distro, you'll also need to patch the installer in a few unofficial ways, because by default there is a bug in the script, and you need a pretty ancient compiler to get it to work.

I've tried it for a bit, but it wasn't worth it for me. Never got it to work. I'll try and see if I can find the page with instructions, but I can already point you to the Gentoo forums, where people were busy getting this code to run.

Edit: first Google thing I notice, is [this thread]("http://ubuntuforums.org/showthread.php?t=571656") on these very forums. Haven't actually looked at it closely, but give it a shot :)

Edit2: Okay, looked at it slightly better: it is a lot of work. A cursory glance reveals you'll need to compile a vanilla kernel, and basically go through a whole mess of hoops. I'd say do not do this unless you know what you are doing, OR are really interested to learn (and not afraid to hose your system once or twice) OR for some reason are really, _really_ desperate for these drivers.

---

### Post by Maestro23 on 2007-10-25
> **Trebaruna said:**
> Not only do you need a 64 bit distro, you'll also need to patch the installer in a few unofficial ways, because by default there is a bug in the script, and you need a pretty ancient compiler to get it to work.

I've tried it for a bit, but it wasn't worth it for me. Never got it to work. I'll try and see if I can find the page with instructions, but I can already point you to the Gentoo forums, where people were busy getting this code to run.

Yeah, I have read some "horror" stories with this driver already.  Anytime you see BETA...

---

### Post by OpposingForce on 2007-10-25
> **Trebaruna said:**
> Not only do you need a 64 bit distro, you'll also need to patch the installer in a few unofficial ways, because by default there is a bug in the script, and you need a pretty ancient compiler to get it to work.

I've tried it for a bit, but it wasn't worth it for me. Never got it to work. I'll try and see if I can find the page with instructions, but I can already point you to the Gentoo forums, where people were busy getting this code to run.

Edit: first Google thing I notice, is [this thread]("http://ubuntuforums.org/showthread.php?t=571656") on these very forums. Haven't actually looked at it closely, but give it a shot :)

Edit2: Okay, looked at it slightly better: it is a lot of work. A cursory glance reveals you'll need to compile a vanilla kernel, and basically go through a whole mess of hoops. I'd say do not do this unless you know what you are doing, OR are really interested to learn (and not afraid to hose your system once or twice) OR for some reason are really, _really_ desperate for these drivers.

Unfortunately I'm not willing to go through that much trouble.  I guess I'll have to sit around until creative releases a 32 bit working driver for the x-fi.

---

### Post by Alastair6 on 2007-10-26
Well, this is not good. The X-Fi series is one of the more popular sound cards out there and I imagine I'm not the only one in this situation. I am not about to buy another card or use the sound from my motherboard. So, does the fault lie with Creative or the folks who brought us Ububntu? I can't use an O/S that has no sound. I guess my only choice is to wait for someone to make it possible for me to have sound. Too bad, I was looking forward to getting into Linux. :(

---

### Post by OpposingForce on 2007-10-29
It's creative's fault, and there's pretty much nothing ubuntu can do about it.  So looks like it's back to windows xp again sadly..I wanted to get into linux but no sound = not acceptable

---

### Post by radamo on 2008-01-08
Yeah, I totally agree.  I just built a new PC with all current components and have Vista 64 running.  I had planned to dual boot to Ubuntu.  But without sound I can't see the need. 

Hopefully Creative will deal with this issue but I am sure it is not one of their top priorities...
RA

---

### Post by NullHead on 2008-01-08
I recommend you stick with windows if you want pain free sound, but Feisty is a whole lot easier to make work with an x-fi. You simple follow the guide from the install of the driver wile skipping he kernel part. Either way it does work quite well in linux with Wolfc's patch, but getting it configured is another story ;)

---


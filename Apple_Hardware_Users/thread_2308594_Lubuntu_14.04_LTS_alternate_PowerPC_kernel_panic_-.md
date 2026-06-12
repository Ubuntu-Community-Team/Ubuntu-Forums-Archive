---
title: "Lubuntu 14.04 LTS alternate PowerPC: kernel panic - init not tainted"
date: 2016-01-04
forum: Apple Hardware Users
---

### Post by Felix_B. on 2016-01-04
Hi there,

I am currently trying to install "Lubuntu 14.04 LTS alternate PowerPC" on an older PowerPC G4 eMac with 800 MHz and 128 MB SDRAM.

During boot from CD-ROM I get the error message: "Kernel panic - not syncing - Attempted to kill init - init not tainted".

What does this mean? Is there still a chance to get Lubuntu running (eventually with more RAM)?

I appreciate your help!

-- 

Thanks a lot,
Felix

---

### Post by este.el.paz on 2016-01-04
That's not a whole lot of RAM, even for Lu . . . you might try ToriOS and see if that works . . . it's based on ubuntu 12.04 for low spec hardware.

But, for Lu, did you check the md5sum number?  Or, you might need to use some boot params to get 14 going, search around to see what video card you have, if it's "radeon" then radeon I believe has been blacklisted in 14.04 so you need the radeonfb boot params . . .  I used 

```
live-nosplash-powerpc video=radeonfb: 1024x768-32@60
```   on my Powermac 3,1 and it gets me into a GUI desktop, but then things don't work too well . . . and that has 2GB RAM . . . I used some other boot params for my iBook . . .  similar, but, not handy right now.  You should be able to find them either searching, or "rican-linux" . . . or mine . . . try some stuff out, but possibly if you check the Lu requirements there might not be enough RAM?????

e...

---

### Post by aperez-6 on 2016-01-04
I also doubt very much that you're going to have any success on a machine with that little RAM. I would strongly urge you to try a much older version of Ubuntu on it.

---

### Post by Felix_B. on 2016-01-04
Thanks for your response! I will expand the RAM to 1GB. Currently I am running MintPPC 11. At least I have got a Windows-desktop-environment running now (LXDE). But it is very slow and there is no WLAN available yet.

---

### Post by este.el.paz on 2016-01-04
Cool.  1GB RAM should speed things up . . . substantially . . . .  Wifi has to be added . . .   It should be findable looking for "b43" . . . should give you some hints . . . .

---

### Post by rsavage on 2016-01-04
> **este.el.paz said:**
> . . . should be in "Additional Drivers" tab of Software Updater???  It should be findable looking for "b43" . . . should give you some hints . . . .  But, could be done in GUI with Additional Drivers . . . and pick the "broadcom" selection . . . should install it . . . .

wrong.

> 
[COLOR=#000000]You should be able to find them either searching "rsavage"'s posts

Please stop name checking me.  Searching posts would be the biggest waste of time.[/COLOR][COLOR=#000000]
[/COLOR]

---

### Post by este.el.paz on 2016-01-04
> **rsavage said:**
> wrong.


Please stop name checking me.  Searching posts would be the biggest waste of time.[/COLOR][COLOR=#000000]
[/COLOR]


Done.

---

### Post by este.el.paz on 2016-01-05
> **rsavage said:**
> wrong.
[COLOR=#000000]
[/COLOR]

OK, booted up my Xu 14.04 iBook . . . and, yes, I was "wrong" about the wifi set up; I was basing what I said on Linux Mint 17 (which is built on 14.04).  There IS "additional drivers" . . . but loading it did not bring anything about wifi, as it does in LM.

So, I launched "Synaptic Package Manager" and searched it with "b43" . . . and that showed the two packages that I installed to get wifi going.  Of course I could be wrong about "b43" being appropriate for the eMac . . . so I'm including a link to the handy FAQ.  Sorry for posting erroneous data . . . best of luck.
[https://wiki.ubuntu.com/PowerPCFAQ#Will_my_wireless_work.3F](https://wiki.ubuntu.com/PowerPCFAQ#Will_my_wireless_work.3F)

---

### Post by Felix_B. on 2016-01-08
The tip with the B43 firmware is not bad! But I did not get it working yet nevertheless...

---

### Post by este.el.paz on 2016-01-08
> **Felix_B. said:**
> The tip with the B43 firmware is not bad! But I did not get it working yet nevertheless...

So, you used synaptic and searching b43 did not show any packages to install?  Or it did show a couple, you installed them, but still no wifi?  If the latter, is there an airport applet that you can right-click on and you can see "enable networking" and "enable wifi"????

---

### Post by Felix_B. on 2016-01-13
I finally got my WLAN working with the B43 **legacy** firmware-installer. Thanks for your help so far. 

So do you still see any chance to get *Lubuntu 14.04 LTS alternate PowerPC* working as initially posted? I have just upgraded my RAM to 1GB.

---

### Post by este.el.paz on 2016-01-13
> **Felix_B. said:**
> I finally got my WLAN working with the B43 **legacy** firmware-installer. Thanks for your help so far. 

So do you still see any chance to get *Lubuntu 14.04 LTS alternate PowerPC* working as initially posted? I have just upgraded my RAM to 1GB.

@Felix:

If you have mintppc11 running then there is a good chance you can get Lu 14.04 running with the 1 GB RAM.  Just in case you don't know "alternate" is basically referring to the size of the iso . . . in comparison to the "live-desktop" size which is now often over 1 GB, alternate is **supposed*** to fit onto a CD but doesn't provide "live" function . . . and "mini" is even smaller and is essentially just an installer.  The alternate splits the difference on size of iso and having some files to install . . . so download time during the install is less than with the mini, etc.

To ***best*** answer your question you should download a Lu 14.o4 "Live-desktop" or whatever looks closest to "desktop" and boot it up using C key . . . and test it out . . . otherwise it is just talk.  Try various boot parameters, specific to your eMac's video card and see how it goes.  If you have some "issues" with getting 14 running, then I would suggest trying Lu/Xu 12.04 . . . that usually runs very well and doesn't need boot params . . . and then later you could use the Software services to upgrade to 14 . . . a window will open and ask you if you'd like to install 14 LTS.

What system do you now have WLAN installed on?  MintPPC?

e...

---

### Post by Felix_B. on 2016-01-13
Hi,

currently I am in deep trouble: I installed the "Alternate PowerPC" version and the installation procedure went through smoothly. But now the windows-system isn't starting (I only see a black screen with the mouse pointer). Is there any chance to kill this process and get into a terminal session? I would like to switch back to MintPPC. But unfortunately I have got a Microsoft keyboard plugged in and there is no eject key available for the cd-drive (alternate F8 doesn't seem to work?).

-- 

Thanks a lot,
Felix

---

### Post by este.el.paz on 2016-01-13
> **Felix_B. said:**
> Hi,

currently I am in deep trouble: I installed the "Alternate PowerPC" version and the installation procedure went through smoothly. But now the windows-system isn't starting (I only see a black screen with the mouse pointer). Is there any chance to kill this process and get into a terminal session? I would like to switch back to MintPPC. But unfortunately I have got a Microsoft keyboard plugged in and there is no eject key available for the cd-drive (alternate F8 doesn't seem to work?).

-- 

Thanks a lot,
Felix

This isn't really "deep" trouble, it's rather shallow trouble . . . but, if you can see the mouse pointer that is a good sign . . . you probably just need some boot parameters to get X properly sorted.  If you don't feel like spending any more time and you are still booted in the black screen, you can get to a TTY shell . . . hold "ctrl-alt-F2" keys and it should give you a command line . . . but, then what do you want to do?

---

### Post by Felix_B. on 2016-01-14
What kind of boot parameters would you suggest? I did not get any idea from reading through the documentation? But I still think it could be a good idea to still play around a little bit with command line options or boot parameters for the x-windows session. That's why I haven't deleted the Lubuntu installation yet. I am still waiting for an original eMac pro keyboard to arrive (I just ordered yesterday)...

That's what I have tried already: **vga=normal, acpi=off, noacpi**

BTW: What I did in order to insert my CD again: "Kernel text" at boot time led to the console (terminal session) where I could type "*eject -r"* in order to open the cd-tray by command.

---

### Post by kyle69 on 2016-01-14
What video card do you have?

---

### Post by Felix_B. on 2016-01-19
No idea: it's an eMac G4 800 MHz!?

---


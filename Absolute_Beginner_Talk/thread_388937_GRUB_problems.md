---
title: "GRUB problems"
date: 2007-03-20
forum: Absolute Beginner Talk
---

### Post by lwalper on 2007-03-20
For those of you who have been following my Ubuntu installation saga I have formatted my primary 80Gb drive and created two NTFS partitions, the first of which (30Gb) contains the Win2K OS. Then repartitioned the second 200Gb HDD (30Gb, 2Gb swap, 150+Gb data). The first partition has is formatted in the Linus native etc3, the other two (swap ??) and 150+Gb NTFS so I can share that partition data with the Win2K install. So far so good.

The Ubuntu install was *flawless*, with two icons automatically installed to the desktop for the NTFS partitions on drive zero. Now my question . . .

After rebooting the system a couple of times the GRUB seems to have changed the video frequency (or something?? like that). The POST comes up normally, but when the boot options load there is a mirror (well, not really mirror for that would be upside down) image of the boot options (actually just a second instance) about halfway down the screen -- and the text looks like it's got ants marching through it. When the OS video drivers load, everything goes back to normal. This occurs in the Win$$ OS as well -- up to the point when the drivers are loaded. For those familiar with the Win$$ OS there is a "progress bar" that comes up prior to the video driver load -- this too has the marching ants in it. Is there something in the GRUB that is resetting the video frequency (or something??) to cause this video image reflection.

---

### Post by dreadlord_chris on 2007-03-20
This might help:
[http://ubuntuforums.org/showthread.php?t=383492](http://ubuntuforums.org/showthread.php?t=383492)

---

### Post by lwalper on 2007-03-21
Hey, thanks a lot for the tip. it's an interesting exercise --- unfortunately it didn't change anything. I tried each of the screen resolutions with no change in the video output. It looks more like a frequency problem than that of a screen resolution. It's no big problem, just sort of an aggravation.

---

### Post by maniacmusician on 2007-03-21
try  manually setting your HorizSync and VertRefresh in our /etc/X11/xorg.conf file. You should put it under the Device section. 

You'll have to find the specific ranges for your monitor. you can look them up on the internet or they might be written on the back of your monitor.

---

### Post by lwalper on 2007-03-21
For some reason I'm not locating that file? Hmmm?

I've using a ViewSonic VG175. The manual tells me that at the current resolution (1280x1024) I should not be running any faster refresh rates than 60Hz (may damage the monitor). The only setting in the Screen Resolution dialog for that resolution is 76Hz. When I select different resolutions, ie. 1024x768, the image of course gets larger, but after a few seconds the system resets to the login screen and reverts to the higher resolution.

---

### Post by rusty4r on 2007-03-21
Open a terminal and type: gedit /etc/X11/xorg.conf 
then paste that file here so we can help you

---

### Post by dstew on 2007-03-21
My guess is that grub is not setting anything in the video card. When grub or the windows splash screen come up, they are using (or trying to use) the normal plain text terminal or VGA setting of your card. I think that your card settings were changed somehow by the operating system, maybe with respect to refresh rates, and those settings are retained by the card. When you turn the card on, it loads those settings, so any program that uses it in these simple modes would show the problem. One way to test this theory would be to boot up an old DOS disk if you have one. My guess is that you would see the same problem.

The answer would probably be re-setting the video card somehow from a running OS, using the card driver interface. What is your video card?

---

### Post by lwalper on 2007-03-22
That's more along the lines of what I was thinking. It seemed strange that the first couple of reboots came up "normal" and then there was this weird change -- like something had been reset on the video card.

The Ubuntu device manager tells me that it is reading an unknown platform legacy device. In Win2K (of course I have the native device drivers loaded from the PC manufacturer) tells me it's a VIA/S3G Unichrome ProIGP video card -- it's built on the motherboard.

---

### Post by dstew on 2007-03-22
The device manager message probably means the driver is not optimal for your video card. However, to put in the correct driver would probably be difficult. Here is a how-to for VIA video driver installation:

[https://help.ubuntu.com/community/OpenChrome](https://help.ubuntu.com/community/OpenChrome)

and a thread where people struggled with this:

[http://ubuntuforums.org/showthread.php?t=270667](http://ubuntuforums.org/showthread.php?t=270667)

Have you tried editing your /etc/X11/xorg.conf file yet?

---

### Post by lwalper on 2007-03-22
Yes, I did try to edit the /etc/X11/xorg.conf file using nano and came up with the following

-----------------------------------------------------------------------


Section "Device"
        Identifier      "Generic Video Card"
        Driver          "vesa"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "VG175"
        Option          "DPMS"
EndSection
--------------------------------------------------------------------------

I'll look at those OpenChrome discussion forums.

---

### Post by lwalper on 2007-03-22
Now that's better!! I went through the process as described -- now have Unichrome drivers installed and can change screen resolution and frequency. Excellent!!

Still no change in the boot loader. Oh well, maybe that few seconds of annoyance won't be too intolerable -- just kind of curious -- especially since the change did not occur immediately on the first load of Ubuntu, but only after two or three restarts. Everything seems to work OK (videowise) except for that.

---


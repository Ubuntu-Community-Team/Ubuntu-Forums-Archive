---
title: "Display Errors/Freeze on Shutdown"
date: 2006-06-06
forum: Absolute Beginner Talk
---

### Post by lark on 2006-06-06
Okay, weird problem here.

When I shut down or restart Ubuntu, it looks as if it's going into the normal shutdown screen, and then the computer freezes and all I see are a bunch of flashing technicolor boxes in a grid pattern.  (It looks a lot like when a DOS program would fault out under Win95 or Win98, actually, very retro.)

The problem started after I used Automatix to install the latest nVidia drivers, so I'm pretty sure this is a driver problem; I've got a newer nVidia card (I will try to find out which one).  I tried to install the newest driver from the nVidia site on my last install, but it was really confusing, so if there's an easier/simpler way?

Other than that -- I'm totally, madly in love with Ubuntu!!!

Edit, it's "NV36.1 [GeForce FX 5700 Ultra]" according to the Devices panel.

---

### Post by catlett on 2006-06-06
Did you try the Dapper Guide section on nvidia drivers? [http://krazypenguin.net/Ubuntu_Dapper_Drake_6.06_Guide#How_to_install_Graphics_Driver_.28NVIDIA.29](http://krazypenguin.net/Ubuntu_Dapper_Drake_6.06_Guide#How_to_install_Graphics_Driver_.28NVIDIA.29)

---

### Post by NoUse on 2006-06-06
I know I had problems with usplash causing hangs when using the nvidia binary drivers.

When you boot up the machine you'll see a prompt with something like "press esc for boot menu".  Press esc and when you get to the boot menu, hit 'e' to edit the line that is highlighted.  Then go down to the line starting with "kernel" and hit 'e' again.  Take off the word "splash" from the list of options then hit enter to comit and 'b' to boot with those options.  

See if disabling the splash screen fixes your problems.  If so you'll need to edit your /boot/grub/menu.lst to make that the default setting.

You can post back here if you aren't sure how to do that.

---

### Post by lark on 2006-06-06
Thank you, catlett and NoUse. :)

I read over the section on KrazyPenguin, and I think I've worked through it -- I checked my xorg.conf against theirs and ran through the steps as listed.  My Automatix install seems to have done most of what was suggested already, though.

Their xorg.conf:
```

Section "Device"
	Identifier	"NVIDIA Corporation xxxx [xxxxx xx xxxx xxx xx]"
	Driver		"nv"
	BusID		"PCI:1:0:0"
EndSection

```

Mine looks the same, except I don't have the "BusID" line and since the instructions don't say it's okay to mess with it, I'm afraid to just stick that line in to see what'll happen.

Disabling the splash did fix the problem (yay!) but it's sort of ugly now.  Nothing I can't live with, though!

---

### Post by aouie on 2006-06-07
Disabling splash appears to have bypassed the crash for me too (NVidia drivers, GeForce FX 5950, Athlon 64, upgraded to Dapper(32 bit)). Too many people are likely to encounter this issue. Hope they fix the underlying issue (whatever that may be) in a security update.
Sincerely,
Aouie

---

### Post by NoUse on 2006-06-07
Please post your experiences in a comment on this bug:
[https://launchpad.net/distros/ubuntu/+source/linux-restricted-modules-2.6.15/+bug/46874](https://launchpad.net/distros/ubuntu/+source/linux-restricted-modules-2.6.15/+bug/46874)

This looks like the problem you are having.  The debate seems to be whether its a bug in usplash or in nvidia-glx.  If its nvidia-glx we have to wait for Nvidia to fix it.  

Oh the joys of closed-source software.

---

### Post by lillian27 on 2006-06-07
Disabling the splash worked for me, too (GeForce FX 5700 Ultra).

I've had this problem since I installed Breezy when it came out.  I hadn't used ubuntu before then so I don't know if it was around before then (meaning is it an Ubuntu/uspash bug or an nvidia bug) but I don't remember this ever happening when I used Fedora.  Of course, YMMV.

When this was still broken for me (10 minutes ago ;) ) after powercycling the box the xserver would frequently not be able to run in any resolution other than 800x600.  Trying to switch resolutions from the keyboard did nothing, and the Screen Resolution tool only showed 800x600 in the combobox.  The xorg.conf seemed to still have all the right entries, but was apparently being ignored.  I would also seem to get the wrong or vanilla/default session (no saved apps running).  Sometimes several reboots were needed before I could get the other resolutions back; the proper session also seemed to return then as well.  

Regardless I'm glad there is finally a workaround.

lillian27

---

### Post by drtpw on 2006-07-28
NoUse,
Thanks for the fix.  I think it worked for my freeze on reboot problem.  Using an Nvidia GeForce 5700 Ultra.  Asking about the editing part.  I'm a noob so it didn't work - naturally.  Went to Terminal and typed: sudo gedit /boot/grub/menu.list  but I got a blank document.  If you have a minute, where did I go wrong?  Thanks.

---

### Post by NoUse on 2006-07-29
Sorry, there was a type in my original message.  It should be /boot/grub/menu.lst

Edit the line that starts with #kopt.  That is the default kernel options.

Once you've saved the file back, run:
sudo dpkg-reconfigure linux-image-`uname -r`

That will propagate those options.

---


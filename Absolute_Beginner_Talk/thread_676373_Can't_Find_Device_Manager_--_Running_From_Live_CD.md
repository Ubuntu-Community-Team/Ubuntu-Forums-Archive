---
title: "Can't Find Device Manager -- Running From Live CD"
date: 2008-01-23
forum: Absolute Beginner Talk
---

### Post by neysahead on 2008-01-23
I am trying the Ubuntu live CD to check for compatibility issues before installing it for good on my computer.  I was walking through the Troubleshooting for establishing a wireless connection, and the help file pointed me to "System > Administration > Device Manager".  Should be easy enough, but I don't have a "Device Manager" listed in the Administration menu.  The first item alphabetically is "Install".

Do I have to install in order to check compatibility?  Or am I missing something much more basic?

Thanks for any help you can provide.

(I knew that this wouldn't be plug-and-play, but I guess I didn't expect to run into a dead end this soon!)

---

### Post by nick_h on 2008-01-23
Try:

System->Preferences->Hardware Information

---

### Post by neysahead on 2008-01-23
Perfect.  Thanks, nick_h.

---

### Post by Demorgon on 2008-04-26
I'm having trouble finding a device manager or Hardware information with the latest uBUntu 8.04 64 - I've looked under System -> Preferences, but there is nothing there that I can see under live or installed.

Any help much appreciated!

---

### Post by catalina on 2008-04-26
Hi Demorgan,

Linux names things differently than windows.  The "Device Manager" in Linux is under "System - Preferences - Hardware Information."  The Hardware Information basically just does that.  The procedures for configuring hardware is different in linux than windows. 

Dean.

---

### Post by Demorgon on 2008-04-26
Right the only problem is there is no "Hardware Information" under System - Preferences as I stated in my post above, I don't see one anywhere?? Is there terminal cmd to open the equivalent?



> 
"I'm having trouble finding a device manager or [color=red]_Hardware information_[/color] with the latest uBuntu 8.04 64"

Been using another distro for 5+ years with kde installed am aware of the differences lol I sometimes use as some call windows terminology, but either way I call it device manager regardless of the OS, my bad I just want to MANAGE MY DEVICES 8)

EDIT:
Anyhow I found this and worked for what I need "Gnome-device-manager 0.2"

---

### Post by Severian. on 2008-04-27
I had the same problem. I loaded 'kde-hal-device-manager'. It seems to display information more similarly to the built-in I'm used to from 7.10.

---

### Post by elope on 2008-05-22
I had exactly the same problem as well 8.04 Ubuntustudio. 

I choosed the gnome version of the device manager. 

Install it via > Add/Remove or Synaptic by searching for device manager and selecting it for install. 

I would recommend the gnome version before the hal kde version, since it is to be more efficient and is written for the gnome desktop which ubuntu is using.

rock on in the free world.

---


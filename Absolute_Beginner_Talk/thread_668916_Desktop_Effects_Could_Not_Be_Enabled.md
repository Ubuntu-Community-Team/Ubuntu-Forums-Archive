---
title: "Desktop Effects Could Not Be Enabled"
date: 2008-01-15
forum: Absolute Beginner Talk
---

### Post by statelypenguin on 2008-01-15
What do I do to fix this?  I can't even change the effects to Normal.  Thanks.

---

### Post by steveneddy on 2008-01-15
What kind of video card do you have?

Do you have the restricted drivers enabled?

:popcorn:

There is no spoon.

---

### Post by statelypenguin on 2008-01-15
Okay I should have said in the first part that I'm a total newb here.  I've checked at one point to see my graphics card/drivers all that but I dont remember how to do it.

---

### Post by statelypenguin on 2008-01-15
description: 	VGA compatible controller
product: 	VT8375 [ProSavage8 KM266/KL266]
vendor: 	S3 Inc.
physical id: 	
0
bus info: 	
pci@0000:01:00.0
version: 	00
width: 	32 bits
clock: 	66MHz
capabilities: 	pm agp agp-2.0 vga bus_master cap_list
configuration:	
driver	=	prosavage_smbus
latency	=	32
maxlatency	=	255
mingnt	=	4
module	=	i2c_prosavage

is that good?

---

### Post by fernandoch on 2008-01-22
I have the same video card, and the same problem.

I found this link:

[http://hardware4linux.info/component/22493/](http://hardware4linux.info/component/22493/)

But got nothing clear. It seems this is just a reporting site.

Any clues?

---

### Post by smurphy_it on 2008-01-22
From the looks of that website you have to disable framebufferring within your xorg.conf file.

This is a text file, which you have to modify as a superuser.

Click Applications, accessories terminal then type sudo gedit /etc/X11/xorg.conf

Under the video section you will find you card.  You have to add an option to disableframebufferring.

This is usually a line like below.

**Option        DisableFrameBufferring yes  (or a 1 I can't remember)**


Make a backup of this file... If upon reboot you can't get into windows, don't worry it is a simple fix.

login the in the shell type:

sudo vi /etc/X11/xorg.conf

and remove the Option line you entered, save and close the file, and reboot.. that should get you back into windows.

---


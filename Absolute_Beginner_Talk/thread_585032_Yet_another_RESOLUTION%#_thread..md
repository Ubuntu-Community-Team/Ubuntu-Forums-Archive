---
title: "Yet another RESOLUTION%# thread."
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by soeten on 2007-10-21
In 7.04 I got 1024x768 working by adding 1024*768 to modes in the xorg.conf file, but when I do so in 7.10 the resolution wont show up in the Preferences -> Screen Resolution drop down menu. And if I remove all other modes other then 1024*768 and reboot it seems as if the login screen is shown in 1024*768, but when I log in my screen goes all matrix. ;p

Also when I tried to install with the 7.10 Cd, the screen went all matrix again when it was loading the gui. So I had to install 7.04 and upgrade to 7.10. This is on a Amentio Pro V3515 with a VIA VN896 chipset. (Im using the VESA driver.)

Any suggestions ? ; /

---

### Post by Pumalite on 2007-10-21
You have to find a driver for this:

Integrated in VIA VN896, Chrome9 HC with DirectX 9.0 3D/2D technology shared memory

---

### Post by soeten on 2007-10-21
Yeah, but the problem is I don't really know what driver to pick. (Or how to install it.)
Ive been looking at openchrome and if I understand right then I need the Chrome 9 HC driver, but It has bad support for video and no 3d support. Which doesnt really matter since I didn't have that with the VESA driver either. But, Im having a hard time finding documentation or a guide how to install the driver.

Ive been reading some @ [http://forums.viaarena.com/messageview.aspx?catid=28&threadid=76991](http://forums.viaarena.com/messageview.aspx?catid=28&threadid=76991) but basically everyone is doing and saying different things, and I cant really understand what to do?

---

### Post by Pumalite on 2007-10-21
Well, I read your link. They say your driver should be here now, since it was written in May. BTW, what about this:

I found the line "(II) VIA(0): VESA VBE Total Mem: 262144 kB" in your xorg.0.log file.
Please chenge the Video (Frame Buffer) size of BIOS from 256MB to 128MB or 64MB then try the VGA driver again.
VIA Linux VGA 72 driver only can use Frame Buffer size with 128 MB or 64 MB now.
Is this something possible in your laptop? Does it make sense to you?

---

### Post by soeten on 2007-10-21
Unfortunately you cant change the video memory in bios on the v3514. : /

---

### Post by twbdan on 2007-10-21
Go into BIOS and increase your video buffer from 1 to 8

---


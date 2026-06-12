---
title: "NVIDIA Confusion"
date: 2006-05-03
forum: Absolute Beginner Talk
---

### Post by StrikerWorldWide on 2006-05-03
Hi,

I'm an incredibly new Linux user - don't know anything. I have a PCIe NVIDIA 6600GT and have been trying to install the drivers for it, but it doesn't want to work. Here's the steps I took:

1. Downloaded the NVIDIA drivers and tried to run it from Terminal like the NVIDIA website said - it told me I needed root priveleges.

1 1/2. Searched the forums for how to install the drivers and found some guys Method 1, Method 2 and Method 3 link - used method 1 - didn't work.

2. Searched the Ubuntu forums and found how to do root priveleges (sudo -s - that's what I've been using)

3. Used the sudo -s then the sh <filename>.run command - it tells me I need binutils

4. Found out how to enable binutils - using the synaptic package manager and installed them as well as the dev versions for safety.

5. Tried to run Step 3 again, only to find that it has an error message telling me that NVIDIA already has a kernel loaded.

Could anyone please help me figure out what the go is here? I'm not only trying to enable 1280x1024 native res but I've got two 1280x1024 monitors and I'm trying to get Dual Screen.

Thanks so much,
Striker.

---

### Post by testube_babies on 2006-05-03
[http://easylinux.info/wiki/Ubuntu#How_to_install_Graphics_Driver_.28NVIDIA.29](http://easylinux.info/wiki/Ubuntu#How_to_install_Graphics_Driver_.28NVIDIA.29)

---

### Post by wylfing on 2006-05-03
Yeah, don't bother with the drivers from the nVidia site. I know this is standard practice on Windows (i.e., getting drivers from manufacturer sites) but we're in a different, better world. Just install the Ubuntu-supplied nVidia drivers and you'll be fine.

There is nothing wrong with the advice given, but another informative link is here:

[https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia](https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia)

HTH

---

### Post by StrikerWorldWide on 2006-05-04
So how do I actually know when the drivers installed - I've followed the procedures in testube's link but my screen res hasn't bounced back to 1280x1024 and I can't see anywhere to change it - my screen resolution setting only has 1024x768 and down... and definitely NO dual monitors yet. :(

Striker

---

### Post by testube_babies on 2006-05-04
Hopefully this tutorial will help you with the dual-monitor situation:

[http://www.ublug.org/ubuntu/twinview/twinview-howto-breezy.html](http://www.ublug.org/ubuntu/twinview/twinview-howto-breezy.html)

After doing this, you're guaranteed that the nvidia proprietary drivers are in action.

---

### Post by wylfing on 2006-05-04
Yep. If you're still having issues, show us the contents of /etc/X11/xorg.conf and we'll analyse. (I'll give instructions on how to get the contents of this file if you have trouble.)

---

### Post by StrikerWorldWide on 2006-05-06
Thanks guys, I've now got the dual monitors and everything working - looks shmicko! Noice one! :D

---


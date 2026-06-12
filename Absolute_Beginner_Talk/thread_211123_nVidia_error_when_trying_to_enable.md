---
title: "nVidia error when trying to enable"
date: 2006-07-07
forum: Absolute Beginner Talk
---

### Post by Nexusx6 on 2006-07-07
I'm running into a problem when trying to enable the drivers for nVidia.

I installed the nvidia-glx drivers for my 6800 GT, and following the wiki instructions I opened the terminal and typed:

> sudo nvidia-glx-config enable

The terminal's response:

> Error: your X configuration has been altered.
This script cannot proceed automatically. If you believe that this
not correct, you can update the md5sum entry executing the following
command:
md5sum /etc/X11/xorg.conf | sudo tee /var/lib/x11/xorg.conf.md5sum
otherwise edit manually /etc/X11/xorg.conf to change the Driver section
from nv to nvidia.
fox@fox-desktop:~$


huh??

Well, while I'm here I guess I drop this question too. I'm trying to extract a skin for aMSN into the /usr/share/amsn/skin folder, but I get an error that I don't have permission to do this. How can I go around this?

Thanks in advance for any replys :o

---

### Post by Dr. Nick on 2006-07-07
the nvidia-glx enable command expects the driver to be "nv", many times it is not though, so to avoid possible problems when it doesnt recgonize the driver it wont change it. You will have to change it manually.

Open a Terminal and type

gksudo gedit /etc/X11/xorg.conf

Look under the device section at the "driver" line, I bet it says "vesa" if it does and your card is nvidia then change vesa to "nvidia" Save the file and log off/on

---

### Post by Nexusx6 on 2006-07-07
> Look under the device section at the "driver" line, I bet it says "vesa" if it does and your card is nvidia then change vesa to "nvidia" Save the file and log off/on

I did exactly as you said, but instead this is what the device line looks like

> Section "Device"
	Identifier	"NVIDIA Corporation NV40 [GeForce 6800 GT]"
	Driver		"nv"
	BusID		"PCI:1:0:0"
EndSection

Should I still change "nv" to "nvidia", then log off and back on? Is it a sign of some other problem?

---

### Post by Dr. Nick on 2006-07-07
yes, you can still change nv to nvidia and relogin. It shouldnt be a concern. If however you get a nasty blue screen on login that says xorg errors then you will need to run 

sudo nano /etc/X11/xorg.conf from the command line and change back to nv

That assumes nano is installed already, I think that is installed by default, If not while at a command line simply do 

sudo apt-get install nano

---

### Post by Nexusx6 on 2006-07-07
Thanks for the help. GNOME started up without any problems.

Typing in sudo nvidia-glx-config enable at the terminal still gives me an error though I'm guessing that's normal now.

Thanks again :)

---

### Post by Dr. Nick on 2006-07-07
yeah, I wouldnt worry about the error, actually it should happen now that its enabled. If you saw a nvidia screen for a second then you are good to go.

---


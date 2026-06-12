---
title: "Vista dual boot issue"
date: 2008-02-28
forum: Absolute Beginner Talk
---

### Post by serialfish on 2008-02-28
Last night, I attempted to install Gutsy on a Windows Vista Dell laptop. I used the Ubuntu Live CD and went through the install process, allowing Ubuntu to create the partition information.

I have a 120 GB hard drive, so I moved Windows to about 75 GB and have Ubuntu for the rest. The partition and following install seemed to work fine. Ubuntu asked me to remove my CD and reboot, which I did.

After doing this, I was greeted with the GRUB screen which had the typical three Ubuntu choices and the Vista. I selected the top Ubuntu choice (seemingly the default). Then, a few words of text (boot-up type information) flashed, and then the screen went completely black. I left it for a few minutes, thinking it was loading, and it never got anywhere.

I rebooted and tried again, with the same results. For the third reboot, I selected the second choice (recovery, I believe). It then flashed a bunch of text and brought me to root. 

I tried Vista and it works fine. What have I done wrong or how do I fix this issue?

---

### Post by rbc on 2008-02-28
I had what sounds like the same thing happen. The Dell I have has a ATI 1300 video. The problem is probably that, Ubuntu is having trouble with your video card. Find out what it is, then post back or search the forums for that card

---

### Post by sayakb on 2008-02-28
> **serialfish said:**
> Last night, I attempted to install Gutsy on a Windows Vista Dell laptop. I used the Ubuntu Live CD and went through the install process, allowing Ubuntu to create the partition information.

I have a 120 GB hard drive, so I moved Windows to about 75 GB and have Ubuntu for the rest. The partition and following install seemed to work fine. Ubuntu asked me to remove my CD and reboot, which I did.

After doing this, I was greeted with the GRUB screen which had the typical three Ubuntu choices and the Vista. I selected the top Ubuntu choice (seemingly the default). Then, a few words of text (boot-up type information) flashed, and then the screen went completely black. I left it for a few minutes, thinking it was loading, and it never got anywhere.

I rebooted and tried again, with the same results. For the third reboot, I selected the second choice (recovery, I believe). It then flashed a bunch of text and brought me to root. 

I tried Vista and it works fine. What have I done wrong or how do I fix this issue?

Boot in to the recovery mode. 
Open xorg.conf file by typing:

```
nano /etc/X11/xorg.conf
```

Then scroll down to a section called "Screen"
You may find fields like identifier, device, monitor, default depth etc.
Below these fields, but just before the "EndSection" statement, add this:

```
	SubSection "Display"
		Modes		"800x600"
	EndSubSection
```

Save it using Ctrl+O and exit using Ctrl+X
Reboot by typing reboot at the # prompt.

PS: Try lower resolutions (like 640x480) if this doesn't work.

---

### Post by sayakb on 2008-02-28
Alternatively, if this above case doesn't work. Boot in through the LiveCD, then install the ATI/nVidia driver through the Restricted Drivers Manager (under System -> Administration)
Then goto the folder /var/cache/apt/archives and copy the driver and add to the newly installed filesystem at any convenient place, say /home/username
Now reboot and boot in to the recovery console, goto that directory and install that package.

---

### Post by serialfish on 2008-02-28
Much thanks.

---

### Post by serialfish on 2008-02-29
I don't seem to have the xorg.conf.

Why would this be? When I type in that command it gives me a blank screen minus the small user guide at the bottom which says 'new file' above it.

Please help!
Thanks again.

---

### Post by dstew on 2008-02-29
Better to do ```
sudo dpkg-reconfigure xserver-xorg
``` from the command line than to edit xorg.conf directly. To get a command line, boot into recovery mode, or press ctrl-alt-F1 at the blank screen of the regular boot.

---

### Post by serialfish on 2008-03-01
I followed the steps described by LinuxIsInnovation and now the standard is still showing a blank black screen. 

Even worse, now the recovery mode won't even go to a GUI by typing 'Exit'. It asks for a login. I give it the login and now it gives a message about 'The programs included with the Ubuntu system are free software...". I can't seem to get out of terminal.

Please help!

---

### Post by dstew on 2008-03-02
At the command line, enter```
sudo dpkg-reconfigure xserver-xorg
```Answer the questions the best you can. Use the vesa driver for the display. After you are done reconfiguring the xserver (the display software) enter startx. That should get your GUI back. Then you can work on getting the correct driver to make the display work better.

---


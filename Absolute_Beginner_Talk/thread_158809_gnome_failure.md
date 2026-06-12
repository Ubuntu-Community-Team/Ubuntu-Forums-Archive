---
title: "gnome failure?"
date: 2006-04-11
forum: Absolute Beginner Talk
---

### Post by SVwanders on 2006-04-11
I have installed Ubuntu on this computer. It has two hard drives and I have it set up to dual boot. My screen resolution or refresh rate is terrible so I was following the instructions to update the gforce video card. I got to the part about rebooting and the system fails to go into X server or at least that is what the screen says. I thought the problem might be with the xorg.conf so in the terminal (which is where I was dropped after failing to boot into Gnome) I mv the xorg.conf and mv (renamed right) the back up file xorg.conf. Well still no go. I get the X server fail message and am dropped into the terminal. I tried to print the screen of the error message but no luck. So my question is how do I get X server (whatever the hell X serve is) back online so I can use the graphical interface in Ubuntu?

one GREEN HORN!
Tim

---

### Post by cleverselfreferentialname on 2006-04-11
When you log in, go to "Sessions" beneath where you give your username and password, and select "Failsafe terminal". Then run ```
sudo apt-get install nano
``` then ```
sudo nano /etc/X11/xorg.conf
```

Look for the section similar to this:

```
Section "Device"
	Identifier	"ATI Technologies, Inc. Radeon X300 SE (RV370)"
	Driver		"fglrx"
	BusID		"PCI:1:0:0"
    	Option 		"RenderAccel" 		"true"
```

Of course yours will be different because you have an nVidia. Anyway, change "fglrx" or whatever your driver is called to "vesa".

Hope this helps.

Regards.
Paul

---

### Post by nalmeth on 2006-04-11
OR to reconfigure the xserver step by step type
sudo dpkg-reconfigure xserver-xorg

---

### Post by cleverselfreferentialname on 2006-04-11
[QUOTE=nalmeth]OR to reconfigure the xserver step by step type
sudo dpkg-reconfigure xserver-xorg[/QUOTE]
Yeah. Thats a more balanced approach. Go with that. Only change the driver to vesa if this doesn't work.

---

### Post by SVwanders on 2006-04-11
[COLOR="Red"][SIZE="3"][CENTER]!!!!BRAVO!!!! [/CENTER][/SIZE][/COLOR]


It worked and the eye straining screen refresh rate is set at a more comfortable 75 . . . Thanks for the help! I went in and configured all the settings using the vesa drivers . . . many thanks.

---


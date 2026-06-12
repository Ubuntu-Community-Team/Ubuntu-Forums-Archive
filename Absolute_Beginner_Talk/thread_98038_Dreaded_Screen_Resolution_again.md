---
title: "Dreaded Screen Resolution again"
date: 2005-12-02
forum: Absolute Beginner Talk
---

### Post by thavard on 2005-12-02
**I have submitted more information on the problem below**


Hello 
I saw on the forums yesterday an expalaination on how to set screen resolution so I am sorry for this post as I was unable to find the thread.. But I have a typical problem

Satellite 2655. I am only allowed to set as high as 800 X 600 but the computer supports 1024 x 768

went to sudo gedit /etc/X11/xorg.conf

And it told me that the driver supported 1024 x 768

What do I do 

I am sorry because I know the answer is already on the forum but I cant find it

---

### Post by aysiu on 2005-12-02
[Try this](http://ubuntuforums.org/showpost.php?p=129379&postcount=21)

---

### Post by teaker1s on 2005-12-02
or just sudo dpkg-reconfigure xserver-xorg to get it as near right as possible then add any extra lines in xorg.conf if required

---

### Post by BobSongs on 2005-12-02
Here's how I resolved the screen problem on my PC.

Since the default setup gave me a resolution and refresh rate I didn't like, I figured nothing from the repositories would help.

In frustration a friend walked me through it. So, I'm passing it on.

**Find your user's manual.** If you've misplaced, lost or thrown it away, then surf the net to your screen manufacturer's site. In my case a Hewlett Packard Ultra VGA 1280. Search the site for something along the lines of **Support and/or Troubleshooting**. Enter the name of your monitor and download any documents (probably in PDF format) that resembles the user manual.

**Search the manual for horizontal and vertical syncs.** The HP lists it as the "Scanning Frequency". Mine says: Horizontal 30 to 69 kHz, Vertical 50 to 160 Hz.

**Back up your xorg.conf.** Open a Terminal (Applications -> Accessories -> Terminal). You'll need to modify your 'xorg.conf' file. Before that back it up. Either use the following code or modify the '_original' part with the date or some other indicator.

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_original
```

**Modify your xorg.conf file.** Use this code:

```
sudo gedit /etc/X11/xorg.conf
```

**Replace the default numbers with the values given by default.** Scroll down to the bottom of the file. They should resemble '39-90'. Wish I could give you the default numbers. But my file has been modified since first set up. Replace the default numbers with the ones in your manual. Keep the same format.

**Save the file and restart Ubuntu.** Perhaps restarting GNOME is sufficient... but I come from a long line of Windows versions. It's a habit now. ;)

Hope it helps. If anyone wants to add some helpful suggestions or corrections, please feel free!

Bob

---

### Post by thavard on 2005-12-05
I really appreciate your help I will start work on the screen tonight

---

### Post by thavard on 2005-12-06
i WENT INTO XORG.CONF
Here are the details.. It appears that the screen is 1024 x 768 but the video driver supports 800 x 600 yet allows a virtual resolution of 1024 x768.
So I think the Ubuntu istaller worked but failed to send the driver informatiohn to Gnome because it says my maximun resoulution is only 800 x 600 Can any one help me solve this problem
Section "Device"
	Identifier	"Trident Microsystems Cyber 9525"
	Driver		"trident"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		De
pth		15
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768"
	EndSubSection

---

### Post by pocketchimp on 2005-12-07
Hi

I was having the exact same problem after installing Ubuntu for the very first time on my 2nd pc.

I followed Bobsongs instructions and got the details for my Iiyama s700jt1 monitor, backed up then edited xorg.conf.

I had no HorizSync or VertRefresh lines, but added them with my details, restarted and crossed my fingers.....

When my pc booted up, instead of being in 800x600 it was in glorious 1280x1024! Woohoo! Thankyou Bobsongs :KS 

For Thavard: - you need to edit the following section on yours:-

Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"
HorizSync 28-51
VertRefresh 43-60
EndSection

And amend the HorizSync and VertRefresh lines with the details from your monitor.

Hopefully it should work like a charm as it did for me and you can get on with exploring the wonderful world of Linux as I shall be :)

---


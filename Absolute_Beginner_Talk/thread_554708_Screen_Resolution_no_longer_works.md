---
title: "Screen Resolution no longer works"
date: 2007-09-19
forum: Absolute Beginner Talk
---

### Post by Gembryna on 2007-09-19
I have gone through multiple threads similar to the following:
[http://ubuntuforums.org/showthread.php?t=83973&highlight=modelines](http://ubuntuforums.org/showthread.php?t=83973&highlight=modelines)
and STILL can't get the resolution set properly.

I need 1600x1200@70hz and nothing else. Any other resolution is just not possible with this CRT (Samsung 997MB). I am using AIGLX or the open source ATI driver. I can't use the Restricted ATI driver with XGL as that kills Compiz Fusion.

Before the last update, I could go to Preferences>Screen Resolution> and set it to 70Hz in the drop-down box. Now only 75hz and 60hz are available after the update. 

Why did Ubuntu do this? Don't they know that MORE choices are better than fewer choices?

This has totally ruined my experience with Ubuntu becuase my screen looks totally screwed up.

Even after editing my xorg.conf (thank god I backed up the original and got back in thru Recovery Mode) and added the Modeline necessary. All I received in turn was a garbled screen.

BRING BACK 1600X1200@70HZ under Preferences>Screen Resolution!!!

How do I remedy this so I can get 70hz again? Apparently "modelines" no longer works in xorg.conf as I followed the instructions to the letter. I added the following modeline under Section Monitor
Modeline "1600x1200" 216.08  1600 1712 1976 2464  1200 1200 1203 1252
which didn't work for me.  

My xorg.conf file follows:
Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ImPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"stylus"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"eraser"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"		"cursor"
	Option		"ForceDevice"	"ISDV4"		# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc R430 [Radeon X800 XL] (PCIe)"
	Driver		"ati"
	BusID		"PCI:5:0:0"
	Option		"UseFBDev"		"true"
EndSection

Section "Monitor"
	Identifier	"SyncMaster"
	Option		"DPMS"
	HorizSync	30-96
	VertRefresh	50-160
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc R430 [Radeon X800 XL] (PCIe)"
	Monitor		"SyncMaster"
	DefaultDepth	24
	SubSection "Display"
		Modes		"1600x1200" "1280x1024" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"

# Uncomment if you have a wacom tablet
#	InputDevice     "stylus"	"SendCoreEvents"
#	InputDevice     "cursor"	"SendCoreEvents"
#	InputDevice     "eraser"	"SendCoreEvents"
EndSection

How do I fix this so I can get 1600x1200@70hz or is this just not possible any longer?

---

### Post by Gembryna on 2007-09-19
<Bump>

---

### Post by alienexplorers on 2007-09-19
try this modeline in your monitor section of your xorg.conf file,
> # 1600x1200 @ 70.00 Hz (GTF) hsync: 87.43 kHz; pclk: 190.25 MHz
  Modeline "1600x1200_70.00"  190.25  1600 1712 1888 2176  1200 1201 1204 1249  -HSync +Vsync

---

### Post by Gembryna on 2007-09-19
Thank you for your reply.

Unfortunately, it did not work. I had tried that modeline you posted, as well as others, earlier today. I copied and pasted yours again just a few mins ago, just to make sure that I had it correct.

**Unfortunately, not even "sudo dpkg -reconfigure xserver-xorg" works**. I can set it to 70hz and it just reboots into 75hz no matter how many times I try.

Apparently, **Ubuntu no longer supports modelines in xorg.conf** either... as it just reboots into the default settings again at 75hz.

Thank you again for your reply. I welcome any further suggestions.

---

### Post by Pumalite on 2007-09-19
It's booting to 75Hz because of your monitor. Consult your Manual or Google your monitor, go to Advanced and set your findings.

---

### Post by Gembryna on 2007-09-19
Yeah, I did that. In fact, I still have the User Manual for my monitor so I know what the safe refresh rates are for this monitor.

Unfortunately, the problem is NOT with my monitor **as it used to work at 1600x1200@70hz**. I could choose b/w 75, 70, 65, and 60hz. 70hz is no longer an option in Ubuntu. even though the monitor remains unchanged. It's Ubuntu that has changed, not the monitor.

I don't have this problem with any other 'nix distro or Windows XP. This isn't my first time in xorg.conf either as I have MANY copies of older xorg.conf files archived and none of those work now. The latest is timestamped for the 13th... of this month and it is a no-go.

Ubuntu changed something with how X-server works as sudo dpkg no longer works to configure X-server at 70hz in Advanced mode. Also, modelines no longer works in Ubuntu. You can make all the changes you want with modelines and they are ignored and then it reboots to the default settings of 1600x1200@75hz.

Any other helpful suggestions are welcome.

---

### Post by Gembryna on 2007-09-19
Update:
The problem with xorg.conf has now been confirmed: [http://ubuntuforums.org/showthread.php?t=486112&highlight=sudo+dpkg&page=39](http://ubuntuforums.org/showthread.php?t=486112&highlight=sudo+dpkg&page=39)

After reading Dave_Man's post this gave me an idea. MD5 the current xorg.conf with working older xorg.conf files and look for changes to the file.

What I found was interesting. Several of the working xorgs = the MD5 of the recent broken xorg released this morning. Seeing that the working ones are **exactly the same** as the "broken" one then there should be no reason that what "used to work" shouldn't continue working. However, this is no longer the case.  

This further explains why even when I substitute older copies of xorg.conf, screen resolution remains broken.

Finally, manual changes to the xorg.conf in gedit **and** sudo dpkg-reconfigure xserver-xorg can be inputted and saved, but screen behavior remains unchanged from default.

So the real problem is not xorg.conf itself, but how Ubuntu is interpreting the file and not acting on the changes made to xorg.conf. The problem is elsewhere in Ubuntu.

---

### Post by Gembryna on 2007-09-20
So has there been any word when xorg/X-server is going to be fixed and released thru Synaptic or the Update Mgr?

Once it is fixed, it may be a good idea to stop releasing new xorg packages for awhile. Don't fix what isn't broken. It would be a real treat to see Ubuntu make it for than a couple weeks without breaking.

---

### Post by Gembryna on 2007-10-04
Problem Solved...

Installed LinuxMint (the latest, Celena, is based on Feisty) which uses an older version of xorg.conf and doesn't cause any conflicts. In addition, the older version of xorg.conf still accepts modelines and changes to xorg.conf, whereas Gibbon still does not.

Thanks to those who tried to help.

---


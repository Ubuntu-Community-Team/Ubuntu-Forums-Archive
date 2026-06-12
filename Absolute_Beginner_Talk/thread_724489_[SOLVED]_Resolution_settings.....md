---
title: "[SOLVED] Resolution settings...."
date: 2008-03-14
forum: Absolute Beginner Talk
---

### Post by HighlyCalculated on 2008-03-14
I've just installed Unbuntu 6.06, and it's my first time using a non-windows OS.  I go to try and set my screen resolution but it will only go as high as 800x600.

My graphics card is a S3 Vision 968.

I've checked around and seen some similar questions, but feel I don't have a good enough grasp of what I'm doing yet to adapt those answers to my needs.

---

### Post by r5gtt2k3 on 2008-03-14
I'm no expert, Infact, I'm pretty much useless, but in windows, I used to get a real bad resolution when my graphics card was not installed, So err Is your graphics card installed in Ubuntu ? if it isnt i think you need to find the restricted drivers System>Prefrences .. Somewhere in there i think, Sorry about the **** advice, but like i said, I'm useless on this OS :D learning myself

---

### Post by sailor2001 on 2008-03-14
in terminal:   sudo dpkg-config -phigh xserver/xorg

---

### Post by Rocket2DMn on 2008-03-14
Since your install is brand new, I would suggest reinstalling right now using the latest version of Ubuntu, 7.10 - Gutsy Gibbon.  The next release, Hardy Heron is due out next month, so you can upgrade when it comes out and stay there for 3 years if you want.  Hardy will be an LTS release like 6.06 is, which is probably why you chose to install 6.06 (Dapper) rather than Gutsy.
You can get 7.10 at [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

After you install, if you still get screen resolution problems, see this guide: [http://ubuntuforums.org/showthread.php?t=690760](http://ubuntuforums.org/showthread.php?t=690760)
-it will work in 6.06 Dapper Drake, I just suggest 7.10 because it has better support and more up to date drivers.

---

### Post by kyphi on 2008-03-14
In a terminal type ```
sudo dpkg-reconfigure -phigh xserver-xorg
```Use your up/down keys to scroll up or down the list and when you come to the resolution that you want press the spacebar to select.  Save and exit.  To reset the windows manager press Ctrl+Alt+Backspace.

---

### Post by HighlyCalculated on 2008-03-14
> **Rocket2DMn said:**
> Since your install is brand new, I would suggest reinstalling right now using the latest version of Ubuntu, 7.10 - Gutsy Gibbon.  The next release, Hardy Heron is due out next month, so you can upgrade when it comes out and stay there for 3 years if you want.  Hardy will be an LTS release like 6.06 is, which is probably why you chose to install 6.06 (Dapper) rather than Gutsy.
You can get 7.10 at [http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

After you install, if you still get screen resolution problems, see this guide: [http://ubuntuforums.org/showthread.php?t=690760](http://ubuntuforums.org/showthread.php?t=690760)
-it will work in 6.06 Dapper Drake, I just suggest 7.10 because it has better support and more up to date drivers.

I actually choose 6.06 because it's system requirements are closer to the hardware I have....I'm running rather old hardware,

I've attempted to do what the thread said a couple times, and just ended up making the GUI not be able to show up....

I know I can run higher resolutions for a fact.

Are there any other ideas?

---

### Post by Rocket2DMn on 2008-03-14
Can you post your xorg.conf and the other following command:
```
cat /etc/X11/xorg.conf
lspci | grep VGA
```

---

### Post by HighlyCalculated on 2008-03-15
I'm assuming you only need this part of xorg.conf.

Section "Device"
	Identifier	"S3 Inc. 86c968 [Vision 968 VRAM] rev 0"
	Driver		"vesa"
	BusID		"PCI:0:13:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"S3 Inc. 86c968 [Vision 968 VRAM] rev 0"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

0000:00:0d.0 VGA compatible controller: S3 Inc. 86c968 [Vision 968 VRAM] rev 0

---

### Post by Rocket2DMn on 2008-03-15
You have a video card I've never heard of.  Video driver support in linux is bad enough, but you're using something that's just strange, you may not be able to get very good support for it.  You're definitely stuck with the vesa driver (generally used as a fallback safe mode driver), so you won't be able to get any desktop effects.  
You xorg.conf looks OK, and since your card isn't like anything I've seen before, I don't know what else you can do other than invest is a new video card - nvidia has good support in linux.  You may want to consider a cheaper end nvidia or ati card.  Sorry man, I think you're pretty much out of luck.  

If anybody else sees this and has any ideas, please do post them.

---

### Post by Mogurijin on 2008-03-15
If you're worried about system requirements, you could try Xubuntu 7.10. This would give you a newer OS (one that might have better driver support) and a desktop-manager for older machines.

[http://www.xubuntu.org/]("http://www.xubuntu.org/")

---

### Post by kyphi on 2008-03-15
Have you checked something as basic as your default resolution setting?

Go to System, Preferences, Resolution.  According to your configuration file you should be able to access 1024 x 768.

---

### Post by HighlyCalculated on 2008-03-16
> **kyphi said:**
> Have you checked something as basic as your default resolution setting?

Go to System, Preferences, Resolution.  According to your configuration file you should be able to access 1024 x 768.

Yeah, despite what the config file says, I can't change my resolution to 1024 x 768.  Baffling.

When I try to edit the config file through the terminal, it list S3 under the graphics card section, but everytime I set it, my screen just goes black when I restart.

I did end up trying xubuntu 7.10, but so far it's the same story.  I am keeping Xubuntu as it does seem to run a bit better for me then Ubuntu 6.06 did.  I guess it's down to getting a new graphics card.

But thanks to everyone who tried to help.

---

### Post by HighlyCalculated on 2008-03-16
Ok, a potentially encouraging development.  Again, I'm now using Xubuntu 7.10.

I went into screens and graphics from the settings menu, and clicked on the monitor model box, scrolled down and found my monitor listed.  In the "graphics card" section, I clicked driver, and also found my graphics card.  I selected both of them, however when I click "test", my screen just goes black, and when it comes back, the Screen and Graphics Preferences window is closed, and my resolution is still 800x600.  When I go back into the Screen and Graphics Preferences window, my monitor model is set back to custom 1 and my driver goes back to Vesa.

Do I need to run the config command in the terminal again?  What am I not knowing here?

---

### Post by Rocket2DMn on 2008-03-16
The Screen and Graphics thing rarely seems to work.  What's worse is they are trying to use it more in Hardy, and when I test out my hardware on it, I can't even get my currently working conifuration to work correctly.  While I understand the desire to get a nice GUI for all this, xorg.conf is so powerful!

If after restarting X you are stuck at a bad resolution, reconfigure X again to get back to where you were before.

---

### Post by HighlyCalculated on 2008-03-16
Found another graphics card laying around, slapped it in, and it worked.

If only I would have tried that two days ago....

Again, thanks to everyone that tried to help.

---


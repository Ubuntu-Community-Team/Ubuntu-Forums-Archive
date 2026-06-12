---
title: "Native Resolution Looks Like Lower Resolution"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by innactpro on 2007-04-30
I got the native resolution, 1440x900, to be available through reconfiguring xorg though my display still looks like it is set to a lower resolution. Auto detect during the reconfigure process recognized my monitor and video card fine. I went through the process of smoothing the look of fonts in the Ubuntu guide though this didn't help. I have done several searches of the forum and didn't find anything that has helped. As just yesterday was the first that I have installed Ubuntu I am sure I am not looking for exactly what i need. Ubuntu is a duel boot (yes duel) as I slowly move from XP learning these little things while doing so.

Thanks

---

### Post by kejar31 on 2007-04-30
I would help but I'm not sure what your asking?

---

### Post by innactpro on 2007-04-30
Well, my resolution is set to 1440x900 which is the native resolution for my monitor but fonts and images still look as though the monitor is set to a lower resolution. Fonts do not look as they should. For instance, an m in one location on the screen will be thick on the left side of itself and thin on the right while an m in a different location on the screen will be thick on the right side of itself thin on the left. Also images appear as though they are not anti-aliased.

---

### Post by lepz on 2007-05-01
> **innactpro said:**
> Well, my resolution is set to 1440x900 which is the native resolution for my monitor but fonts and images still look as though the monitor is set to a lower resolution. Fonts do not look as they should. For instance, an m in one location on the screen will be thick on the left side of itself and thin on the right while an m in a different location on the screen will be thick on the right side of itself thin on the left. Also images appear as though they are un-anti-aliased.

Can you post your xorg.conf file

---

### Post by innactpro on 2007-05-01
Sure
------------------------------------------------------------------------------------
Section "Device"
	Identifier	"ATI Technologies Inc RV280 [Radeon 9200]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"AL1916W"
	Option		"DPMS"
	HorizSync	31-84
	VertRefresh	56-76
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RV280 [Radeon 9200]"
	Monitor		"AL1916W"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1440x900" "1400x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1440x900" "1400x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1440x900" "1400x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1440x900" "1400x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1440x900" "1400x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1440x900" "1400x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus"	"SendCoreEvents"
	InputDevice     "cursor"	"SendCoreEvents"
	InputDevice     "eraser"	"SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection
------------------------------------------------------------------------------------
I only included the portion that pertained to the video card to the end. If I need to include the rest just let me know.

---

### Post by toddward on 2007-05-01
I'm unsure if the ATI drivers is like the NVIDIA drivers.  What version of the ATI drivers are you using?

---

### Post by innactpro on 2007-05-01
Drivers are a real weakness of mine. I do not know which drivers I am using nor do I know where to look to find out.

I found this in the Ubuntu guide.

------------------------------------------

3D ATI Video Card Driver

Many ATI video cards work well with Ubuntu automatically. To check that 3D acceleration works with your card, see the section called &#8220;Introduction to 3D Video Acceleration&#8221;.

If it doesn&#8217;t work:

   1.

      Install the xorg-driver-fglrx package from the &#8220;Restricted&#8221; repository (see Chapter 3, Adding, Removing and Updating Applications).
   2.

      To set up the new driver, enter in a terminal:

      sudo dpkg-reconfigure xserver-xorg

      Agree to automatic detection of your video, and choose the driver fglrx when asked.

Restart the computer for the changes to take effect.

------------------------------------------------------------------

I am going to try this and see if it helps. I had done the reconfigure thing a few times but I have no idea if I chose the fglrx driver.

------------------------------------------------------------------

OK that didn't work. I tried a few different driver selections and unless I choose the ati driver, X fails to start up. At least now I know which driver I'm using, I think. Oh well, the solution will present itself.

---

### Post by toddward on 2007-05-01
One application that will really help is an app called **envy**.  It basically gives you the option to install automatically (the ATI driver) or select from a series of previous drivers to install.  Hopefully this should solve your problem of things not appearing right.

You can find the application here: [https://launchpad.net/envy]("https://launchpad.net/envy")

---

### Post by innactpro on 2007-05-01
I went to the Envy page and I am unsure how to get it. I clicked around the site a little and didn't see anything that looked like a download. I went to Synaptic to search for it and a couple of things were found and installed but those look like they are for sound cards. I tried Add/Remove and searched for Envy and HDSPConf and HDSPMixer were the only things listed.

---

### Post by bobplano on 2007-05-01
you can try fglrx. installing them fixed the resolution for me. ```
sudo apt-get install xorg-driver-fglrx
```
also you need to add 1440x900 to the 24-bit one and once you installed the drivers you need to change the "drivers" part to fglrx. you can also use the reconfigure command, just choose fglrx. note that these drivers are propritary so you might have to add repos
here is a guide [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by innactpro on 2007-05-01
Most of that I had already done. I did go to the link and gave that a shot but no joy (does it matter that I have an Intel cpu instead of AMD). In the restricted Drivers Manager ATI has never had anything listed. Also with the Envy thing I'm still a little lost.

---

### Post by toddward on 2007-05-01
> **innactpro said:**
> I went to the Envy page and I am unsure how to get it. I clicked around the site a little and didn't see anything that looked like a download. I went to Synaptic to search for it and a couple of things were found and installed but those look like they are for sound cards. I tried Add/Remove and searched for Envy and HDSPConf and HDSPMixer were the only things listed.

If you'd like to still install the **envy** application, head back to the link I provided and click on the link titled ["Visit the Envy: Unofficial ATI and NVIDIA driver installer for Ubuntu home page"]("http://www.albertomilone.com/nvidia_scripts1.html").  This link is a detailed guide on how to get it installed (which takes very little time and effort).  

*Note: the downloadable file **envy_0.9.2-0ubuntu5_all.deb** is located about half-way down the page.*

Good luck figuring this stuff out!:)

---

### Post by innactpro on 2007-05-01
I made it to that page but did not know what to look for. I am trying it now, thanks.

----------------------------------------------------------------

I ran Envy and X server failed to start upon restating the computer after running Envy. Shouldn't ATI be showing in the Restricted Drivers Manager? The only thing listed there is the modem and I don't even use that.

----------------------------------------------------------------

I reinstalled 6.06, and I may stay with it because of the LTS, and my screen looks much better. Not quite as good as in XP but much better. I didn't spend any time in 6.06 or 6.10 and went straight into 7.04 from my 6.06 live CD so I never saw how my monitor would look in those. I am looking forward to Ubuntu Studio. Thanks for all the help. I just hope I can do as much for someone one day.

----------------------------------------------------------------

Going back 6.06 not only improved monitor performance but also fixed my DVD watching problem as well as my CD listening problems which I hadn't gotten around to asking about in the forums. Perhaps 7.04 needs a little more time or more experienced users?

----------------------------------------------------------------

I still have no 3D acceleration. I went through the Ubuntu documentation on fixing this and still no 3D acceleration.

---


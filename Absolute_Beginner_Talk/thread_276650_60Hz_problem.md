---
title: "60Hz problem"
date: 2006-10-13
forum: Absolute Beginner Talk
---

### Post by caravel on 2006-10-13
Hi I'm new to Ubuntu, and relatively new to Linux.  I have tried Mandrake in the past but found it frustrating and buggy.  Among the common problem I've always had is, graphics cards and monitors.

Now I seem to be in the same situation. 60Hz.  I have tried "sudo dpkg-reconfigure xserver-xorg" which ended up giving me the option to set either 1024*768@87Hz as well as 60Hz.  87Hz is not supported and, after blacking out, brings me back to the login screen.  My monitor, not terribly impressive, is a Belinea 102020 15".  My graphics card is a Radeon 9000 Pro 64MB which was detected ok.  Any ideas?  I seem to remember editing the X server config file in the past, but I'm not sure where to find it now.

Thanks in Advance for any help (my eyeballs can't take much more 60Hz!). 8)

---

### Post by petri on 2006-10-13
Welcome to Ubuntu!

"sudo dpkg-reconfigure xserver-xorg" does edit the xorg.conf

Try with **fglrxinfo** in terminal and if it does not answer with ATI then you need to install the drivers. [Here]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide") is a guide how to do it. If the first method don't work you do have to download the older drivers (8.28.8) from [www.ati.com](www.ati.com) and chance the version numbers in commands. That should do it.

---

### Post by Zimmer on 2006-10-13
> **caravel said:**
> Hi I'm new to Ubuntu, and relatively new to Linux.  I have tried Mandrake in the past but found it frustrating and buggy.  Among the common problem I've always had is, graphics cards and monitors.

Now I seem to be in the same situation. 60Hz.  I have tried "sudo dpkg-reconfigure xserver-xorg" which ended up giving me the option to set either 1024*768@87Hz as well as 60Hz.  87Hz is not supported and, after blacking out, brings me back to the login screen.  My monitor, not terribly impressive, is a Belinea 102020 15".  My graphics card is a Radeon 9000 Pro 64MB which was detected ok.  Any ideas?  I seem to remember editing the X server config file in the past, but I'm not sure where to find it now.

Thanks in Advance for any help (my eyeballs can't take much more 60Hz!). 8)

If you need to just alter the Monitor section of the xorg.conf then here is how I sorted mine.

Go to /var/log  and look for the xorg.0.log file and open it with gedit.
scroll through the log (big file, search if you like, for lines that refer to the Monitor.
there you should find info relating to the Vertical and Horizontal ranges...something like this...

(II) fglrx(0): Supported additional Video Mode:
(II) fglrx(0): clock: 25.2 MHz   Image Size:  304 x 228 mm
(II) fglrx(0): h_active: 640  h_sync: 688  h_sync_end 784 h_blank_end 800 h_border: 0
(II) fglrx(0): v_active: 350  v_sync: 410  v_sync_end 412 v_blanking: 449 v_border: 0
(II) fglrx(0): Ranges: V min: 50  V max: 75 Hz, H min: 31  H max: 61 kHz, PixClock max 80 MHz
(II) fglrx(0): Monitor name: AL1511
(II) fglrx(0):  ACER
(II) fglrx(0): End of Display1 EDID data --------------------

My monitor has a vertical range of 50-75       and horizontal  31-61.

You may find all sorts of other warning [WW] and eror messages [EE] which may also give clues as to how to put things right.

Use the Vertical and Horizontal values you find in YOUR log to insert as HorizSync 
and VertRefresh  statements in your xorg.conf file.
(use sudo gedit /etc/X11/xorg.conf) copy it to a backup file first, in case you make a mistake and need a working config again..

This is what the section should look like (with YOUR monitor values from your log file, of course, not mine)
Section "Monitor"
HorizSync      31-61
Identifier "Generic Monitor"
Option "DPMS"
VertRefresh    50-75
Modeline "1280x800@60" 83.91 1280 1312 1624 1656 800 816 824 841
EndSection

You could also check your Modeline statement is correct by referring to the values for the clock,
h_active,h_sync, h_sync_end, h_blank_end, v_active, v_sync, v_sync_end, v_blanking

If you are going to use the Modeline statement you must declare the mode in the Screen section...

Something like this:

Section "Screen"
Identifier "Default Screen"
Device "Intel Corporation 82852/855GM Integrated Graphics Device"
Monitor "Generic Monitor"
SubSection "Display"
        Depth     24
        Modes     "1280x800@60"
 EndSubsection
EndSection


This eliminates all the other mode statements for individual depths that you have in your current config so delete them from the Display subsection.
I have tested this method on my monitor. 
(My current entry, based on those 'actual'log entries at the beginning )

Section "Monitor"
	Identifier	"AL1511"
	Option		"DPMS"
        Modeline        "1024x768" 25.20 640 688 784 800 350 410 412 449
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon 9600 (R300 AP)"
	Monitor		"AL1511"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1024x768"
	EndSubSection
	
EndSection

 It works(even without the Vert and Horiz sync values) and my available resolutions and refresh rates are now to be found in the Screen>Preferences dialog. So find your log file and get looking for those values.

---

### Post by caravel on 2006-10-13
Thanks for the replies, I'll try this out tonight. ;)

---

### Post by caravel on 2006-10-13
Hi again

I could not find "fglrxinfo".  I tried "sudo gedit /etc/X11/xorg.conf" and edited the horizontal and vertical scan frequency ranges.  Now it does work, and I've got 1024*768@85Hz.  Thanks!

In the xorg.conf file i couldn't any reference to "Modeline", though there are a "Modes" lines.  My monitor and screen sections are now as follows:

```
Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	30-70
	VertRefresh	50-120
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. Radeon RV250 If [Radeon 9000 Pro]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "720x400" "640x480" "640x400"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "720x400" "640x480" "640x400"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "720x400" "640x480" "640x400"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "720x400" "640x480" "640x400"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1024x768" "800x600" "720x400" "640x480" "640x400"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1024x768" "800x600" "720x400" "640x480" "640x400"
	EndSubSection
EndSection
```

I still see "87Hz" as an option also in the screen resolution menu.

---

### Post by caravel on 2006-10-14
Well, now I've another problem.  The screensavers kept crashing so I decided to install the proprietary ATI driver.  After installing the proprietary ATI driver and rebooting, X now fails to initialise.  "no screens found" or some such error.  I followed the instructions on ATI's website exactly and now, yet again I'm left with a non functional OS (posting from XP).

First I did: "sudo sh ./ati-driver-installer-8.29.6.run"

Which opened a graphical install program.  I went for the automatic install, which is likely why it now doesn't work.  After this I ran:  "/usr/X11R6/bin/aticonfig --initial", and then rebooted as instructed.

Any ideas how I can get out of this one? ](*,)

Thanks in advance

Caravel

---

### Post by PriceChild on 2006-10-14
Follow this to install the ATI driver: [http://doc.gwos.org/index.php/Install_ATI_driver](http://doc.gwos.org/index.php/Install_ATI_driver)

---

### Post by caravel on 2006-10-14
Thanks for the reply but I've given up.  This is exactly the situation that made me abandon Linux in the past.  Possibly in the future when I can get an Nvidia graphics card I'll give it a go again.  This is not the way to try and learn about a new OS, spending half a day trying to install a stupid driver. ](*,)   I just don't have time nor the energy for this. :neutral:

Thanks anyway

Caravel

---

### Post by petri on 2006-10-15
I can see you followed the ATIs instructions, it seems like you followed the ATIs instructions and [http://doc.gwos.org/index.php/Install_ATI_driver](http://doc.gwos.org/index.php/Install_ATI_driver) but not [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)  that should have done it :rolleyes:

---

### Post by caravel on 2006-10-16
I didn't follow this: [http://doc.gwos.org/index.php/Install_ATI_driver](http://doc.gwos.org/index.php/Install_ATI_driver)

I basically don't understand it.  It doesn't seem to relate to the file I downloaded.  Do I have to install the driver first as per ATI's guide, and then follow the instructions above? O do I need to download a different package? Sorry for my apparrent stupidity. :-?

---

### Post by Demon012 on 2006-10-16
> sudo apt-get install xorg-driver-fglrx
sudo apt-get install linux-restricted-modules-$(uname -r) #Okay if it is already installed 
sudo dpkg-reconfigure xserver-xorg #Select the fglrx driver

apt-get downloads and installs the driver for you (sudo apt-get install) you then configure your computer to use it using dpkg-reconfigure xserver-xorg.

---

### Post by caravel on 2006-10-16
You've inspired me to try it again.  Thanks! :D

---

### Post by Demon012 on 2006-10-16
No problem glad I could be of help =)

---

### Post by petri on 2006-10-16
With Ubuntu you don't have to download files, the apt-get does it as does the aptitude command.

The first line in [http://doc.gwos.org/index.php/Install_ATI_driver](http://doc.gwos.org/index.php/Install_ATI_driver) downloads and installs the driver. The strange thin is they don't use the update command which is ```
sudo apt-get update
``` Paste it in your terminal and press Enter. Then paste this ```
sudo apt-get install xorg-driver-fglrx
``` which downloads and installs the driver. After that paste this 
```
sudo apt-get install linux-restricted-modules-$(uname -r)
``` which downloads the needed kernelmodules to your kernel (uname -r) means your kernel and you don't have to find out what is your kernel, nice isn't it? :D  Paste the third line ```
sudo dpkg-reconfigure xserver-xorg
``` and then a neat program starts where you have to choose you new driver "fglrx" and answer the other questions as you can, otherwise choose the default (just press Enter). This program rewrites your xorg.conf  which means your kernel will use the fglrx-driver as it reads the xorg.conf. I think :rolleyes: 

Then you have to reboot. In Linux you have to reboot when you do something with your kernel and now you added a module to your kernel. After reboot paste ```
fglrxinfo
``` in terminal and it should answer with **ATI** and not **Mesa**.

Didn't work? Just yell here so we try some othe methods.

---

### Post by caravel on 2006-10-16
```
fglrxinfo
[fglrx] API ERROR: could not register entrypoint for SelectTextureSGIS
[fglrx] API ERROR: could not register entrypoint for SelectTextureTransformSGIS
[fglrx] API ERROR: could not register entrypoint for ClientActiveVertexStreamATI[fglrx] API ERROR: could not register entrypoint for VertexBlendEnviATI
[fglrx] API ERROR: could not register entrypoint for VertexBlendEnvfATI
[fglrx] API ERROR: could not register entrypoint for VertexStream2sATI
[fglrx] API ERROR: could not register entrypoint for VertexStream2svATI
[fglrx] API ERROR: could not register entrypoint for VertexStream2iATI
[fglrx] API ERROR: could not register entrypoint for VertexStream2ivATI
[fglrx] API ERROR: could not register entrypoint for VertexStream2fATI
[fglrx] API ERROR: could not register entrypoint for VertexStream2fvATI
[fglrx] API ERROR: could not register entrypoint for VertexStream2dATI
[fglrx] API ERROR: could not register entrypoint for VertexStream2dvATI
[fglrx] API ERROR: could not register entrypoint for VertexStream3sATI
[fglrx] API ERROR: could not register entrypoint for VertexStream3svATI
[fglrx] API ERROR: could not register entrypoint for VertexStream3iATI
[fglrx] API ERROR: could not register entrypoint for VertexStream3ivATI
[fglrx] API ERROR: could not register entrypoint for VertexStream3fATI
[fglrx] API ERROR: could not register entrypoint for VertexStream3fvATI
[fglrx] API ERROR: could not register entrypoint for VertexStream3dATI
[fglrx] API ERROR: could not register entrypoint for VertexStream3dvATI
[fglrx] API ERROR: could not register entrypoint for VertexStream4sATI
[fglrx] API ERROR: could not register entrypoint for VertexStream4svATI
[fglrx] API ERROR: could not register entrypoint for VertexStream4iATI
[fglrx] API ERROR: could not register entrypoint for VertexStream4ivATI
[fglrx] API ERROR: could not register entrypoint for VertexStream4fATI
[fglrx] API ERROR: could not register entrypoint for VertexStream4fvATI
[fglrx] API ERROR: could not register entrypoint for VertexStream4dATI
[fglrx] API ERROR: could not register entrypoint for VertexStream4dvATI
[fglrx] API ERROR: could not register entrypoint for NormalStream3bATI
[fglrx] API ERROR: could not register entrypoint for NormalStream3bvATI
[fglrx] API ERROR: could not register entrypoint for NormalStream3sATI
[fglrx] API ERROR: could not register entrypoint for NormalStream3svATI
[fglrx] API ERROR: could not register entrypoint for NormalStream3iATI
[fglrx] API ERROR: could not register entrypoint for NormalStream3ivATI
[fglrx] API ERROR: could not register entrypoint for NormalStream3fATI
[fglrx] API ERROR: could not register entrypoint for NormalStream3fvATI
[fglrx] API ERROR: could not register entrypoint for NormalStream3dATI
[fglrx] API ERROR: could not register entrypoint for NormalStream3dvATI
[fglrx] API ERROR: could not register entrypoint for DrawRangeElementsEXT
[fglrx] API ERROR: could not register entrypoint for WeightbvARB
[fglrx] API ERROR: could not register entrypoint for WeightsvARB
[fglrx] API ERROR: could not register entrypoint for WeightivARB
[fglrx] API ERROR: could not register entrypoint for WeightfvARB
[fglrx] API ERROR: could not register entrypoint for WeightdvARB
[fglrx] API ERROR: could not register entrypoint for WeightubvARB
[fglrx] API ERROR: could not register entrypoint for WeightusvARB
[fglrx] API ERROR: could not register entrypoint for WeightuivARB
[fglrx] API ERROR: could not register entrypoint for WeightPointerARB
[fglrx] API ERROR: could not register entrypoint for VertexBlendARB
[fglrx] API ERROR: could not register entrypoint for MultiDrawArraysEXT
[fglrx] API ERROR: could not register entrypoint for MultiDrawElementsEXT
[fglrx] API ERROR: could not register entrypoint for DrawBuffersATI
[fglrx] API ERROR: could not register entrypoint for DrawElementsFGL
[fglrx] API ERROR: could not register entrypoint for DrawWireTrianglesFGL
[fglrx] API ERROR: could not register entrypoint for PNTrianglesiATI
[fglrx] API ERROR: could not register entrypoint for PNTrianglesfATI
[fglrx] API ERROR: could not register entrypoint for TexBumpParameterivATI
[fglrx] API ERROR: could not register entrypoint for TexBumpParameterfvATI
[fglrx] API ERROR: could not register entrypoint for GetTexBumpParameterivATI
[fglrx] API ERROR: could not register entrypoint for GetTexBumpParameterfvATI
[fglrx] API ERROR: could not register entrypoint for BeginVertexShaderEXT
[fglrx] API ERROR: could not register entrypoint for EndVertexShaderEXT
[fglrx] API ERROR: could not register entrypoint for BindVertexShaderEXT
[fglrx] API ERROR: could not register entrypoint for GenVertexShadersEXT
[fglrx] API ERROR: could not register entrypoint for DeleteVertexShaderEXT
[fglrx] API ERROR: could not register entrypoint for ShaderOp1EXT
[fglrx] API ERROR: could not register entrypoint for ShaderOp2EXT
[fglrx] API ERROR: could not register entrypoint for ShaderOp3EXT
[fglrx] API ERROR: could not register entrypoint for SwizzleEXT
[fglrx] API ERROR: could not register entrypoint for WriteMaskEXT
[fglrx] API ERROR: could not register entrypoint for InsertComponentEXT
[fglrx] API ERROR: could not register entrypoint for ExtractComponentEXT
[fglrx] API ERROR: could not register entrypoint for GenSymbolsEXT
[fglrx] API ERROR: could not register entrypoint for SetInvariantEXT
[fglrx] API ERROR: could not register entrypoint for SetLocalConstantEXT
[fglrx] API ERROR: could not register entrypoint for VariantbvEXT
[fglrx] API ERROR: could not register entrypoint for VariantsvEXT
[fglrx] API ERROR: could not register entrypoint for VariantivEXT
[fglrx] API ERROR: could not register entrypoint for VariantfvEXT
[fglrx] API ERROR: could not register entrypoint for VariantdvEXT
[fglrx] API ERROR: could not register entrypoint for VariantubvEXT
[fglrx] API ERROR: could not register entrypoint for VariantusvEXT
[fglrx] API ERROR: could not register entrypoint for VariantuivEXT
[fglrx] API ERROR: could not register entrypoint for VariantPointerEXT
[fglrx] API ERROR: could not register entrypoint for EnableVariantClientStateEXT[fglrx] API ERROR: could not register entrypoint for DisableVariantClientStateEXT
[fglrx] API ERROR: could not register entrypoint for BindLightParameterEXT
[fglrx] API ERROR: could not register entrypoint for BindMaterialParameterEXT
[fglrx] API ERROR: could not register entrypoint for BindTexGenParameterEXT
[fglrx] API ERROR: could not register entrypoint for BindTextureUnitParameterEXT[fglrx] API ERROR: could not register entrypoint for BindParameterEXT
[fglrx] API ERROR: could not register entrypoint for IsVariantEnabledEXT
[fglrx] API ERROR: could not register entrypoint for GetVariantBooleanvEXT
[fglrx] API ERROR: could not register entrypoint for GetVariantIntegervEXT
[fglrx] API ERROR: could not register entrypoint for GetVariantFloatvEXT
[fglrx] API ERROR: could not register entrypoint for GetVariantPointervEXT
[fglrx] API ERROR: could not register entrypoint for GetInvariantBooleanvEXT
[fglrx] API ERROR: could not register entrypoint for GetInvariantIntegervEXT
[fglrx] API ERROR: could not register entrypoint for GetInvariantFloatvEXT
[fglrx] API ERROR: could not register entrypoint for GetLocalConstantBooleanvEXT[fglrx] API ERROR: could not register entrypoint for GetLocalConstantIntegervEXT[fglrx] API ERROR: could not register entrypoint for GetLocalConstantFloatvEXT
[fglrx] API ERROR: could not register entrypoint for WindowPos2dARB
[fglrx] API ERROR: could not register entrypoint for WindowPos2fARB
[fglrx] API ERROR: could not register entrypoint for WindowPos2iARB
[fglrx] API ERROR: could not register entrypoint for WindowPos2sARB
[fglrx] API ERROR: could not register entrypoint for WindowPos2ivARB
[fglrx] API ERROR: could not register entrypoint for WindowPos2svARB
[fglrx] API ERROR: could not register entrypoint for WindowPos2fvARB
[fglrx] API ERROR: could not register entrypoint for WindowPos2dvARB
[fglrx] API ERROR: could not register entrypoint for WindowPos3iARB
[fglrx] API ERROR: could not register entrypoint for WindowPos3sARB
[fglrx] API ERROR: could not register entrypoint for WindowPos3fARB
[fglrx] API ERROR: could not register entrypoint for WindowPos3dARB
[fglrx] API ERROR: could not register entrypoint for WindowPos3ivARB
[fglrx] API ERROR: could not register entrypoint for WindowPos3svARB
[fglrx] API ERROR: could not register entrypoint for WindowPos3fvARB
[fglrx] API ERROR: could not register entrypoint for WindowPos3dvARB
[fglrx] API ERROR: could not register entrypoint for BindBufferARB
[fglrx] API ERROR: could not register entrypoint for DeleteBuffersARB
[fglrx] API ERROR: could not register entrypoint for GenBuffersARB
[fglrx] API ERROR: could not register entrypoint for IsBufferARB
[fglrx] API ERROR: could not register entrypoint for BufferDataARB
[fglrx] API ERROR: could not register entrypoint for BufferSubDataARB
[fglrx] API ERROR: could not register entrypoint for GetBufferSubDataARB
[fglrx] API ERROR: could not register entrypoint for MapBufferARB
[fglrx] API ERROR: could not register entrypoint for UnmapBufferARB
[fglrx] API ERROR: could not register entrypoint for GetBufferParameterivARB
[fglrx] API ERROR: could not register entrypoint for GetBufferPointervARB
[fglrx] API ERROR: could not register entrypoint for NewObjectBufferATI
[fglrx] API ERROR: could not register entrypoint for IsObjectBufferATI
[fglrx] API ERROR: could not register entrypoint for UpdateObjectBufferATI
[fglrx] API ERROR: could not register entrypoint for GetObjectBufferfvATI
[fglrx] API ERROR: could not register entrypoint for GetObjectBufferivATI
[fglrx] API ERROR: could not register entrypoint for FreeObjectBufferATI
[fglrx] API ERROR: could not register entrypoint for DeleteObjectBufferATI
[fglrx] API ERROR: could not register entrypoint for ArrayObjectATI
[fglrx] API ERROR: could not register entrypoint for GetArrayObjectfvATI
[fglrx] API ERROR: could not register entrypoint for GetArrayObjectivATI
[fglrx] API ERROR: could not register entrypoint for VariantArrayObjectATI
[fglrx] API ERROR: could not register entrypoint for GetVariantArrayObjectfvATI
[fglrx] API ERROR: could not register entrypoint for GetVariantArrayObjectivATI
[fglrx] API ERROR: could not register entrypoint for ElementPointerATI
[fglrx] API ERROR: could not register entrypoint for DrawElementArrayATI
[fglrx] API ERROR: could not register entrypoint for DrawRangeElementArrayATI
[fglrx] API ERROR: could not register entrypoint for MapObjectBufferATI
[fglrx] API ERROR: could not register entrypoint for UnmapObjectBufferATI
[fglrx] API ERROR: could not register entrypoint for VertexAttribArrayObjectATI
[fglrx] API ERROR: could not register entrypoint for GetVertexAttribArrayObjectfvATI
[fglrx] API ERROR: could not register entrypoint for GetVertexAttribArrayObjectivATI
[fglrx] API ERROR: could not register entrypoint for VertexAttrib1sARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib1fARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib1dARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib2sARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib2fARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib2dARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib3sARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib3fARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib3dARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4sARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4fARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4dARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4NubARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib1svARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib1fvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib1dvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib2svARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib2fvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib2dvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib3svARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib3fvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib3dvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4bvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4svARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4ivARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4ubvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4usvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4uivARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4fvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4dvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4NbvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4NsvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4NivARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4NubvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4NusvARB
[fglrx] API ERROR: could not register entrypoint for VertexAttrib4NuivARB
[fglrx] API ERROR: could not register entrypoint for VertexAttribPointerARB
[fglrx] API ERROR: could not register entrypoint for EnableVertexAttribArrayARB
[fglrx] API ERROR: could not register entrypoint for DisableVertexAttribArrayARB[fglrx] API ERROR: could not register entrypoint for ProgramStringARB
[fglrx] API ERROR: could not register entrypoint for BindProgramARB
[fglrx] API ERROR: could not register entrypoint for DeleteProgramsARB
[fglrx] API ERROR: could not register entrypoint for GenProgramsARB
[fglrx] API ERROR: could not register entrypoint for ProgramEnvParameter4fARB
[fglrx] API ERROR: could not register entrypoint for ProgramEnvParameter4dARB
[fglrx] API ERROR: could not register entrypoint for ProgramEnvParameter4fvARB
[fglrx] API ERROR: could not register entrypoint for ProgramEnvParameter4dvARB
[fglrx] API ERROR: could not register entrypoint for ProgramLocalParameter4fARB
[fglrx] API ERROR: could not register entrypoint for ProgramLocalParameter4dARB
[fglrx] API ERROR: could not register entrypoint for ProgramLocalParameter4fvARB[fglrx] API ERROR: could not register entrypoint for ProgramLocalParameter4dvARB[fglrx] API ERROR: could not register entrypoint for GetProgramEnvParameterfvARB[fglrx] API ERROR: could not register entrypoint for GetProgramEnvParameterdvARB[fglrx] API ERROR: could not register entrypoint for GetProgramLocalParameterfvARB
[fglrx] API ERROR: could not register entrypoint for GetProgramLocalParameterdvARB
[fglrx] API ERROR: could not register entrypoint for GetProgramivARB
[fglrx] API ERROR: could not register entrypoint for GetProgramStringARB
[fglrx] API ERROR: could not register entrypoint for GetVertexAttribdvARB
[fglrx] API ERROR: could not register entrypoint for GetVertexAttribfvARB
[fglrx] API ERROR: could not register entrypoint for GetVertexAttribivARB
[fglrx] API ERROR: could not register entrypoint for GetVertexAttribPointervARB
[fglrx] API ERROR: could not register entrypoint for IsProgramARB
[fglrx] API ERROR: could not register entrypoint for GenFragmentShadersATI
[fglrx] API ERROR: could not register entrypoint for BindFragmentShaderATI
[fglrx] API ERROR: could not register entrypoint for DeleteFragmentShaderATI
[fglrx] API ERROR: could not register entrypoint for BeginFragmentShaderATI
[fglrx] API ERROR: could not register entrypoint for EndFragmentShaderATI
[fglrx] API ERROR: could not register entrypoint for PassTexCoordATI
[fglrx] API ERROR: could not register entrypoint for SampleMapATI
[fglrx] API ERROR: could not register entrypoint for ColorFragmentOp1ATI
[fglrx] API ERROR: could not register entrypoint for ColorFragmentOp2ATI
[fglrx] API ERROR: could not register entrypoint for ColorFragmentOp3ATI
[fglrx] API ERROR: could not register entrypoint for AlphaFragmentOp1ATI
[fglrx] API ERROR: could not register entrypoint for AlphaFragmentOp2ATI
[fglrx] API ERROR: could not register entrypoint for AlphaFragmentOp3ATI
[fglrx] API ERROR: could not register entrypoint for SetFragmentShaderConstantATI
[fglrx] API ERROR: could not register entrypoint for CurrentPaletteMatrixARB
[fglrx] API ERROR: could not register entrypoint for MatrixIndexubvARB
[fglrx] API ERROR: could not register entrypoint for MatrixIndexusvARB
[fglrx] API ERROR: could not register entrypoint for MatrixIndexuivARB
[fglrx] API ERROR: could not register entrypoint for MatrixIndexPointerARB
[fglrx] API ERROR: could not register entrypoint for StencilOpSeparateATI
[fglrx] API ERROR: could not register entrypoint for StencilFuncSeparateATI
[fglrx] API ERROR: could not register entrypoint for PointParameteriEXT
[fglrx] API ERROR: could not register entrypoint for PointParameterivEXT
[fglrx] API ERROR: could not register entrypoint for GenOcclusionQueriesNV
[fglrx] API ERROR: could not register entrypoint for DeleteOcclusionQueriesNV
[fglrx] API ERROR: could not register entrypoint for IsOcclusionQueryNV
[fglrx] API ERROR: could not register entrypoint for BeginOcclusionQueryNV
[fglrx] API ERROR: could not register entrypoint for EndOcclusionQueryNV
[fglrx] API ERROR: could not register entrypoint for GetOcclusionQueryivNV
[fglrx] API ERROR: could not register entrypoint for GetOcclusionQueryuivNV
[fglrx] API ERROR: could not register entrypoint for MapTexture3DATI
[fglrx] API ERROR: could not register entrypoint for UnmapTexture3DATI
[fglrx] API ERROR: could not register entrypoint for PointParameterfARB
[fglrx] API ERROR: could not register entrypoint for PointParameterfvARB
[fglrx] API ERROR: could not register entrypoint for GenVisibilityQueriesATI
[fglrx] API ERROR: could not register entrypoint for DeleteVisibilityQueriesATI
[fglrx] API ERROR: could not register entrypoint for BeginDefineVisibilityQueryATI
[fglrx] API ERROR: could not register entrypoint for EndDefineVisibilityQueryATI[fglrx] API ERROR: could not register entrypoint for BeginUseVisibilityQueryATI
[fglrx] API ERROR: could not register entrypoint for EndUseVisibilityQueryATI
[fglrx] API ERROR: could not register entrypoint for GenQueriesARB
[fglrx] API ERROR: could not register entrypoint for DeleteQueriesARB
[fglrx] API ERROR: could not register entrypoint for IsQueryARB
[fglrx] API ERROR: could not register entrypoint for BeginQueryARB
[fglrx] API ERROR: could not register entrypoint for EndQueryARB
[fglrx] API ERROR: could not register entrypoint for GetQueryivARB
[fglrx] API ERROR: could not register entrypoint for GetQueryObjectivARB
[fglrx] API ERROR: could not register entrypoint for GetQueryObjectuivARB
[fglrx] API ERROR: could not register entrypoint for DeleteObjectARB
[fglrx] API ERROR: could not register entrypoint for GetHandleARB
[fglrx] API ERROR: could not register entrypoint for DetachObjectARB
[fglrx] API ERROR: could not register entrypoint for CreateShaderObjectARB
[fglrx] API ERROR: could not register entrypoint for ShaderSourceARB
[fglrx] API ERROR: could not register entrypoint for CompileShaderARB
[fglrx] API ERROR: could not register entrypoint for CreateProgramObjectARB
[fglrx] API ERROR: could not register entrypoint for AttachObjectARB
[fglrx] API ERROR: could not register entrypoint for LinkProgramARB
[fglrx] API ERROR: could not register entrypoint for UseProgramObjectARB
[fglrx] API ERROR: could not register entrypoint for ValidateProgramARB
[fglrx] API ERROR: could not register entrypoint for Uniform1fARB
[fglrx] API ERROR: could not register entrypoint for Uniform2fARB
[fglrx] API ERROR: could not register entrypoint for Uniform3fARB
[fglrx] API ERROR: could not register entrypoint for Uniform4fARB
[fglrx] API ERROR: could not register entrypoint for Uniform1iARB
[fglrx] API ERROR: could not register entrypoint for Uniform2iARB
[fglrx] API ERROR: could not register entrypoint for Uniform3iARB
[fglrx] API ERROR: could not register entrypoint for Uniform4iARB
[fglrx] API ERROR: could not register entrypoint for Uniform1fvARB
[fglrx] API ERROR: could not register entrypoint for Uniform2fvARB
[fglrx] API ERROR: could not register entrypoint for Uniform3fvARB
[fglrx] API ERROR: could not register entrypoint for Uniform4fvARB
[fglrx] API ERROR: could not register entrypoint for Uniform1ivARB
[fglrx] API ERROR: could not register entrypoint for Uniform2ivARB
[fglrx] API ERROR: could not register entrypoint for Uniform3ivARB
[fglrx] API ERROR: could not register entrypoint for Uniform4ivARB
[fglrx] API ERROR: could not register entrypoint for UniformMatrix2fvARB
[fglrx] API ERROR: could not register entrypoint for UniformMatrix3fvARB
[fglrx] API ERROR: could not register entrypoint for UniformMatrix4fvARB
[fglrx] API ERROR: could not register entrypoint for GetObjectParameterfvARB
[fglrx] API ERROR: could not register entrypoint for GetObjectParameterivARB
[fglrx] API ERROR: could not register entrypoint for GetInfoLogARB
[fglrx] API ERROR: could not register entrypoint for GetAttachedObjectsARB
[fglrx] API ERROR: could not register entrypoint for GetUniformLocationARB
[fglrx] API ERROR: could not register entrypoint for GetActiveUniformARB
[fglrx] API ERROR: could not register entrypoint for GetUniformfvARB
[fglrx] API ERROR: could not register entrypoint for GetUniformivARB
[fglrx] API ERROR: could not register entrypoint for GetShaderSourceARB
[fglrx] API ERROR: could not register entrypoint for BindAttribLocationARB
[fglrx] API ERROR: could not register entrypoint for GetActiveAttribARB
[fglrx] API ERROR: could not register entrypoint for GetAttribLocationARB
[fglrx] API ERROR: could not register entrypoint for IsRenderbufferEXT
[fglrx] API ERROR: could not register entrypoint for BindRenderbufferEXT
[fglrx] API ERROR: could not register entrypoint for DeleteRenderbuffersEXT
[fglrx] API ERROR: could not register entrypoint for GenRenderbuffersEXT
[fglrx] API ERROR: could not register entrypoint for RenderbufferStorageEXT
[fglrx] API ERROR: could not register entrypoint for GetRenderbufferParameterivEXT
[fglrx] API ERROR: could not register entrypoint for IsFramebufferEXT
[fglrx] API ERROR: could not register entrypoint for BindFramebufferEXT
[fglrx] API ERROR: could not register entrypoint for DeleteFramebuffersEXT
[fglrx] API ERROR: could not register entrypoint for GenFramebuffersEXT
[fglrx] API ERROR: could not register entrypoint for CheckFramebufferStatusEXT
[fglrx] API ERROR: could not register entrypoint for FramebufferTexture1DEXT
[fglrx] API ERROR: could not register entrypoint for FramebufferTexture2DEXT
[fglrx] API ERROR: could not register entrypoint for FramebufferTexture3DEXT
[fglrx] API ERROR: could not register entrypoint for FramebufferRenderbufferEXT
[fglrx] API ERROR: could not register entrypoint for GetFramebufferAttachmentParameterivEXT
[fglrx] API ERROR: could not register entrypoint for GenerateMipmapEXT
```

Ok the driver seemed to work!  Thanks alot! :mrgreen:

I have those errors above from fglrxinfo.

I haven't seen if the OpenGL screensavers are working yet.  Here goes.

As I suspected the screensavers don't function, but there are no crashes so I've changed the screensaver to a non OpenGL one.  I know enough about OpenGL (little) to know that the errors from fglrx look like they are related to that API.  So it seems that OGL is broken.  Not a big deal though would've been nice to have OGL functionality.

---

### Post by petri on 2006-10-16
That's broken OpenGL, get back to my first post. There is a link which takes you here: [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

There you can read about istructions which would have given you the drivers. Did you read that link för three days ago? There can you also read about **the instructions how to fix broken OpenGL**  (Troubleshooting for Method 1)

---

### Post by caravel on 2006-10-16
Ok I did sudo cp libGL.so.1.2 /usr/lib

Then I tested the screensavers and they were all working!

Then I did fglrxinfo again and got this:

```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9000 PRO DDR Generic
OpenGL version string: 1.3.1072 (X4.3.0-8.25.18)
```

Isn't it great when it works? :mrgreen:

**petri** I owe you a drink or several my friend! =D>

---

### Post by petri on 2006-10-17
Sounds great! 

Both the drink and you got your ATI working but just help 30 :rolleyes:  other persons coming after us in Ubuntu and you'll be good. :mrgreen:

---

### Post by caravel on 2006-10-17
I'll try but I haven't much of a clue myself, as yet.  But as I discover things from the pros here I will endeavour to make others aware of this. ;)

---


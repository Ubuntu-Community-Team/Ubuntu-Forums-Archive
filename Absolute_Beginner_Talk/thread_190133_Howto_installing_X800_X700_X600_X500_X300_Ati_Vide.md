---
title: "Howto: installing X800 X700 X600 X500 X300 Ati Video Cards"
date: 2006-06-05
forum: Absolute Beginner Talk
---

### Post by edurm on 2006-06-05
I'm just creating this topic because my old own was closed: [link](http://www.ubuntuforums.org/showthread.php?t=183643)

If you're trying to install Ubuntu 6.06 or 5.XX using an ATI video card X200 X300 X500 X550 X600 X700 X800 X850 series or even the new ones X1300 X1600 X1800 X1900 series or any other video card and comes to this screen:

[img]http://i4.tinypic.com/10yl3tl.jpg[/img]

It happened because the xserver (the graphic interface) could not be correctly loaded.


To fix this problem is quite easy:


1) type: *sudo nano /etc/X11/xorg.conf* (Remember, Linux is case sensitive)

2) Find the line **driver "ati"** change it to **"vesa"** and then press Ctrl+x, then "Enter" to overwrite.

Now You will be able to start the "X", to do it type: *startx* then "Enter"

3) Now The ubuntu was loaded and you will see a install shortcut in your desktop screen. Well, now just follow the install instruction and setup the system. After you complete the process you will be in a black terminal screen again. Don't worry it just happened because GDM wasn't full loaded and after restart it will not happen again. To restart type *sudo shutdown -r "now"*



Now you are running Linux using the "vesa" drives that is as older as a 386 computer

To fix it just head to the next fase: 



_Installing Ati "fglrx" drives:_

1. Open the "synaptic" (System > Administration > Synaptic)
2. Search for fglrx
3. Mark xorg-driver-fglrx and fglrx-control
4. Apply changes (it will download and install the drive)
5. Open a terminal window
6. *sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup* (Creating a backup)
7. *sudo gedit /etc/X11/xorg.conf*
8. Find "device" change **driver = "vesa"** or **"ATI"** to **driver = "fglrx"**
9. Save
10. ctrl+alt+backspace (restart X) 


After this step you may run *sudo dpkg-reconfigure xserver-xorg* to add your desired out of standart resolution or refresh rate value

*Backuping xorg.conf is essential, specially if you are running a non english language, because if you use the comand *sudo dpkg-reconfigure xserver-xorg* your keyboard setting will get missconfigured. Use your backup xorg.conf to restore your regional keybord setting

**After all this you will be able to get a **real** 85Hz or 100Hz refresh rate under 1024X768

*** Now that you have your Ubuntu Linux running fine you can install [Automatix](http://www.ubuntuforums.org/showthread.php?t=80295) - It'll install everything you need easier than count one, two, three

---

### Post by u.b.u.n.t.u on 2006-06-05
Good post edurm,

That will help someone when they search!

:grin:

---

### Post by NeoGreen on 2006-06-06
Awesome post, this really helped me out.  Thanks.:D

---

### Post by Phasmagon on 2006-06-06
it is really rather easier than that.

In a terminal type

sudo apt-get install xorg-driver-fglrx
sudo aticonfig --initial
sudo aticonfig --overlay-type-Xv

and then either startx if you are in console
or Ctl+Alt+Backspace if in virtual terminal.

---

### Post by Arthur Millar on 2006-06-06
ive tried this ond my monitor signal dies when i change the xorg.conf from ati to vesa could it be my monitor settings

---

### Post by Phasmagon on 2006-06-06
Maybe the resolution in xorg.conf is set too high?

---

### Post by aq3e on 2006-06-06
Thanks so much only issue i have now on my X800GTO 512 is no OpenGL

---

### Post by Eoin on 2006-06-06
[QUOTE=Phasmagon]it is really rather easier than that.

In a terminal type

sudo apt-get install xorg-driver-fglrx
sudo aticonfig --initial
sudo aticonfig --overlay-type[COLOR="Red"]=[/COLOR]Xv[/QUOTE]

Just want to confirm that the above steps worked for me with an AMD x62 Dual Core and a Radeon X800 (With a small little correction shown in [COLOR="Red"]red[/COLOR]).

I had to install xorg-driver-fglrx twice though, once to get the live cd up and running and once again for the harddisc install. Note the vesa drivers method would not work me for me.

---

### Post by edurm on 2006-06-06
[QUOTE=Arthur Millar]ive tried this ond my monitor signal dies when i change the xorg.conf from ati to vesa could it be my monitor settings[/QUOTE]

Linux is case sentitive and xorg.conf is a very delicate config file. Check for a missing " or a extra point or a blank space you may acidentally inserted. I don't belive your monitor could not work with vesa driver or 60HZ resfresh rate

---

### Post by aq3e on 2006-06-06
Yea you must have missed something the vesa driver always should work its basically a last resort. But has anyone had sucess with OpenGL?

---

### Post by Eoin on 2006-06-06
[QUOTE=Arthur Millar]ive tried this ond my monitor signal dies when i change the xorg.conf from ati to vesa could it be my monitor settings[/QUOTE]

I was having this problem and am pretty sure it wasn't typo, the monitor would switch off as if to change resolution but never come back on.

---

### Post by edurm on 2006-06-06
[QUOTE=Eoin]I was having this problem and am pretty sure it wasn't typo, the monitor would switch off as if to change resolution but never come back on.[/QUOTE]
How old is your monitor? I think I know why it is happening, Linux sets the default vesa resolution to 1280X1024 quite high for an old monitor. I think first you must go to xorg.conf and delete all 1280X1024 resolution. After this it must start at 1024X768, I think your monitor can handle this resolution


[QUOTE=aq3e]Yea you must have missed something the vesa driver always should work its basically a last resort. But has anyone had sucess with OpenGL?[/QUOTE]
Wich program are you using to test OpenGL ? :-k

---

### Post by ales on 2006-06-06
Great many tahnks,


I trie and it worsk. I have Athlon 3200 64andX800 GTO 512Sapphire.
How can I check if 3D abilities are on_
?

---

### Post by Eoin on 2006-06-06
[QUOTE=edurm]How old is your monitor? I think I know why it is happening, Linux sets the default vesa resolution to 1280X1024 quite high for an old monitor. I think first you must go to xorg.conf and delete all 1280X1024 resolution. After this it must start at 1024X768, I think your monitor can handle this resolution[/QUOTE]

Goog idea but my monitor is a TFT with native 1280x1024 resolution. This is the first time I've had a problem with the visa driver, but its also my first time using X.org 7.

---

### Post by edurm on 2006-06-06
[QUOTE=Eoin]Goog idea but my monitor is a TFT with native 1280x1024 resolution. This is the first time I've had a problem with the visa driver, but its also my first time using X.org 7.[/QUOTE]

It's vesa not visa, watchout, would not be this the case ?


[QUOTE=ales]Great many tahnks,

I trie and it worsk. I have Athlon 3200 64andX800 GTO 512Sapphire.
How can I check if 3D abilities are on_
?[/QUOTE]

It's on. If you go Synaptic and search for fglrx you'll find the xorg-driver-fglrx installed (green box) if you read the botom line it says: 

*This package provides 2D display drivers and hardware accelerated OpenGL.*

Mine is 8.25 wich means it's the newest driver

---

### Post by aq3e on 2006-06-06
I dont know why it wont work then thats odd, i now get my native resolution of 1680x1050, but no opengl


EDIT: works now had to do it a second time, after i dpkg-reconfigured  i selected no to write on the first wite option but did hit yes to the monitor configuration, works now!

---

### Post by edurm on 2006-06-18
To test opengl just open a terminal and type: glxgears -printfps

---

### Post by Lord Landis on 2006-06-21
Edurm, Phasmagon, thanks a ton!  I've been arguing with my system for hours now, and it looks like I won't have to resort to drastic measures after all.  

Does anyone know if this has been fixed in 6.06 or not?

---

### Post by edurm on 2006-06-22
Not yet, that is why I sugested that xorg.conf should start in "VESA" for all ati cards

---

### Post by macarrao37 on 2006-06-25
[QUOTE=Arthur Millar]ive tried this ond my monitor signal dies when i change the xorg.conf from ati to vesa could it be my monitor settings[/QUOTE]


I have the same problem.. I´ve tried to change screen resolution. and nothing works..
I can really hear the loading sounds of ubuntu.. but no images..

---

### Post by edurm on 2006-06-27
[QUOTE=macarrao37]I have the same problem.. I´ve tried to change screen resolution. and nothing works..
I can really hear the loading sounds of ubuntu.. but no images..[/QUOTE]


Try to boot in 800X600 video mode. Maybe your monitor can not handle the default ubuntu gnome resolution

---

### Post by neshumah on 2006-06-30
Does anyone knows if an ati x300 is able to support XGL and Compiz ??

---

### Post by vincent85 on 2006-07-02
Hi there,

I've tried many possible ways(change the resolution to the minimum,check " or a extra point or a blank space that may acidentally inserted....) but nothing work.
my monitor signal still dies after change conf...
Plz help, i am really want to try this OS.
Thank

---

### Post by /thomas on 2006-07-03
[QUOTE=vincent85]Hi there,

I've tried many possible ways(change the resolution to the minimum,check " or a extra point or a blank space that may acidentally inserted....) but nothing work.
my monitor signal still dies after change conf...
Plz help, i am really want to try this OS.
Thank[/QUOTE]

i have the same problem. i have x800gt with two syncmaster 940b. the monitor dies every time (tried 3 times) after i have made the [sudo nano /etc/X11/xorg.conf ...etc] change and type *startx*.

i also tried *sudo dpkg-reconfigure xserver-xorg* and changed to VESA, i tried twice -  the monitor dies after i type *startx*

the intresting thing is, that i can run ubuntu 5.10 live dvd (like now) by doing the *sudo dpkg-reconfigure xserver-xorg*! but as stated, the same procedure in 6.06 makes my display die.

---

### Post by vincent85 on 2006-07-04
Yes, Another person like me, can anyone help us out? (The monitor signal dies after change "ati"-> "vesa" in conf) ...
Plz, anyone.....

---

### Post by Snorri Kristjánsson on 2006-07-04
[QUOTE=Phasmagon]it is really rather easier than that.

In a terminal type

sudo apt-get install xorg-driver-fglrx
sudo aticonfig --initial
sudo aticonfig --overlay-type-Xv

and then either startx if you are in console
or Ctl+Alt+Backspace if in virtual terminal.[/QUOTE]

Thank you, this realy did the trick :D  and did I say THANK YOU

---

### Post by /thomas on 2006-07-04
update: i did get the x800gt to work with ubuntu: i'm not 100% sure what it was any more, since i stayed up all night until i fixed it. 

after x server crashes, *sudo nano /etc/X11/xorg.conf* and then change the *driver ati* to *driver radeon* as well as delete all resolutions (for 24 bit) except 640x480. that way you can continue with ubuntu. 

the screen is unbearably small, but it is possible to go through with the installer from the desktop. at some point i went to synaptic and installed the *fglrx* drivers. after having installed ubuntu, i changed the driver from *radeon* to *fglrx* and added my display's native resolution to the list.

sorry about the confusing explanation, but i was extremely tired when i did this.

now my dilemma is: how do i get my dual displays to work as an extended desktop? at the moment they are in clone mode/mirroring mode. i read about some xinerama but it seems **so** complicated...

---

### Post by edurm on 2006-07-11
> **vincent85 said:**
> Yes, Another person like me, can anyone help us out? (The monitor signal dies after change "ati"-> "vesa" in conf) ...
Plz, anyone.....

Try this in xorg.conf: "as well as delete all resolutions (for 24 bit) except 640x480. that way you can continue with ubuntu."

---

### Post by sYs^ on 2006-07-11
> **/thomas said:**
> update: i did get the x800gt to work with ubuntu: i'm not 100% sure what it was any more, since i stayed up all night until i fixed it. 

after x server crashes, *sudo nano /etc/X11/xorg.conf* and then change the *driver ati* to *driver radeon* as well as delete all resolutions (for 24 bit) except 640x480. that way you can continue with ubuntu. 

the screen is unbearably small, but it is possible to go through with the installer from the desktop. at some point i went to synaptic and installed the *fglrx* drivers. after having installed ubuntu, i changed the driver from *radeon* to *fglrx* and added my display's native resolution to the list.

sorry about the confusing explanation, but i was extremely tired when i did this.

now my dilemma is: how do i get my dual displays to work as an extended desktop? at the moment they are in clone mode/mirroring mode. i read about some xinerama but it seems **so** complicated...

Thanks man, I have exactly the same problem (x800GT/SyncMaster 730BF), I'll try it tonight, I hope it'll work. :>

---

### Post by IronWolve on 2006-07-11
Dont forget to edit /etc/default/linux-restricted-modules-common

Add this line

DISABLED_MODULES="fglrx"

Then reboot. That fixed it for me.

BTW, new releases of restricted modules will bork Ubuntu again.  ](*,)

---

### Post by sYs^ on 2006-07-13
Now my system is installed, but when I shut it down the monitor turns off and I can't see any response from the PC. So I can't see the shutdown process but the black screen.

Any ideas?

---

### Post by Hedzu on 2006-07-19
radeon driver instead of vesa and 640 for 24 bits did the trick for me on my radeon x800xl pcie/syncmaster 915N with ubuntu 6.06 64 bit.

Thanks for the help ppl, ubuntu rocks ;)

---

### Post by Frawg on 2006-08-02
eoin's suggestion really helped 
>  Originally Posted by Phasmagon
it is really rather easier than that.

In a terminal type

sudo apt-get install xorg-driver-fglrx
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv

running x2 3800 with visiontek radeon x800

---

### Post by onefournine on 2006-08-26
> **Phasmagon said:**
> it is really rather easier than that.

In a terminal type

sudo apt-get install xorg-driver-fglrx
sudo aticonfig --initial
sudo aticonfig --overlay-type-Xv

and then either startx if you are in console
or Ctl+Alt+Backspace if in virtual terminal.

Thank you very much. This was a bullseye for me. I'm running a Pentium D 820 with a Radeon X600. I'm using the AMD64 version of 6.06. Thanks again.

---

### Post by ajare on 2006-09-04
Changing the xorg.conf driver to "radeon" and removing resolutions down to 800x600 worked for me.

Thanks Hedzu :D

---

### Post by zeeR on 2006-09-04
One weird thing happened to me...When i install ubuntu from scratch (i have a radeon x600), and do glrxinfo, it says "Direct Rendering: Yes"...Then  i install the fglrx driver in synaptic, and change the xorg.conf to the "fglrx" driver, after the restart, it says "Mesa" and all that, and Tux Racer, for example, gets extra slow!...And before i could play it normally, without any framerate problems... =S

EDIT: When i remove the drivers and get xorg.conf back to the original, it all becomes ok again.

---

### Post by Ranime on 2006-10-22
Here is my xorg.conf, maybe somebody can make some good use of it. it works on my side.

I do have an AGP board btw ;)

```
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc104"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "Device"
	Identifier	"ATI Technologies, Inc. R420 JT [Radeon X800VE]"
	Driver		"fglrx"
	BusID		"PCI:2:0:0"
	Screen		0
##	Option		"FastVram"
##	Option		"Accel"
##	Option 		"UseInternalAGPGART" 	"no"
##	Option 		"OpenGLOverlay" 	"off"
##	Option 		"VideoOverlay" 		"on"
##	Option		"NoDDC"
EndSection

Section "Device"
   	Driver        	"fglrx"
   	Identifier    	"ATI Technologies, Inc. R420 JT [Radeon X800VE - TV-OUT]"
   	Screen		1
   	Option        	"TVOutFormat" 		"Composite" #or SVIDEO etc
   	Option        	"TVStandard" 		"PAL-B" #or NTSC, PAL-I for uk etc
   	Option        	"ConnectedMonitor" 	"TV"
   	BusID         	"PCI:2:0:0" #adjust using 'lspci' or cat /proc/pci
EndSection


Section "Monitor"
	Identifier	"Generic Monitor" #CRT
	Option		"DPMS"
	HorizSync	28-83
	VertRefresh	60-120
EndSection

Section "Monitor"
   	Identifier 	"Extended Monitor" #TV
   	HorizSync 	30-95
   	VertRefresh 	60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies, Inc. R420 JT [Radeon X800VE]"
	Monitor		"Generic Monitor"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		Modes		"1152x864"
	EndSubSection
EndSection

Section "Screen"
   	Device 		"ATI Technologies, Inc. R420 JT [Radeon X800VE - TV-OUT]"
   	Identifier 	"TV"
   	Monitor 	"Extended Monitor"
   	DefaultDepth 	24
       		SubSection "Display"
               	Depth 		24
               	Modes 		"1024x768"
       EndSubSection
EndSection


Section "ServerLayout"
   Identifier "Simple Layout"
       Screen 0 "Default Screen"
       Screen 1 "TV" RightOf "Default Monitor"
   InputDevice "Generic Keyboard"
   InputDevice "Configured Mouse"
EndSection


Section "DRI"
	Mode	0666
EndSection

```

goodluck

---

### Post by ojasvi rajpal on 2006-10-22
Thanks helped me

---

### Post by LTBP5WD2 on 2006-10-28
O.K. Here goes.I am a newbie.  I was able to install 6.06 on an old Pentium III machine but I cannot get it to run on my good machine.  I am running XP Media Center Edition with an Xbox Media extender to stream video.  My good system is an Asus P5WD2 Premium motherboard with 2 Sata II 300gig hard Drives( IDE configured in AHCI mode but I am not running a raid setup since I don't know how or if I need it)(XP on one and media on the other), Powercolor X800GT, and a Haupauge MCE 500 dual TV tuner card.  I can get 6.06 to run in safe graphics mode from the live CD but when I try to run in normal mode I get a scrambled screen. I think it may be because of the video card, but I read the 6.06 does not work with Sata II hard drives. Can anyone o[ponit me in the right direction?  
How would I stream video using the Xbox Media Extender or would I need other hardware?  

I am trying to get away from Windows and the cost of software.

---

### Post by Roobert on 2006-10-31
edurm, has any of your procedures changed for Edgy? I tried installing xorg-driver-fglrx and fglrx-control, and then changing the driver in /etc/X11/xorg.conf to every type of driver you listed to no avail.

---

### Post by rosvit on 2006-11-06
> **edurm said:**
> 
1) type: *sudo nano /etc/X11/xorg.conf* (Remember, Linux is case sensitive)


where should i type that command? 
thanx

---

### Post by James^H on 2006-11-13
At a command prompt.

On a side note, I am sad that there is still this issue with ATI cards in uBuntu, I appreciate its not ubuntus fault per se, but its a real deal breaker for me to try and re-install it. I got it working (barely) before, but the screen res etc was not correct, and yes I did edit the config file correctly (as stated by my manual).

I always want to move to Linux, ubuntu espescially, but its just so frustrating with ATI cards.

I'll probs end up upgrading to nVidia soon anyway.

---

### Post by davebed on 2006-11-13
I am hoping someone will be able to tell me if my xorg.conf file is OK.

My dispaly is working, but I'm confused about double entries in the **Monitor** and **Device** entries:
```
**Section "Monitor"**
	Identifier   "Generic Monitor"
	Option	    "DPMS"
EndSection

**Section "Monitor"**
	Identifier   "aticonfig-Monitor[0]"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

**Section "Device"**
	Identifier  "ATI Technologies, Inc. ATI Default Card"
	Driver      "vesa"
	BusID       "PCI:1:0:0"
EndSection

**Section "Device"**
	Identifier  "aticonfig-Device[0]"
	Driver      "fglrx"
	Option	    "VideoOverlay" "on"
	Option	    "OpenGLOverlay" "off"
EndSectio
```

Does this look right or do I have a problem? I am using Beryl right now, but I want to make sure that my graphics card (x1400 on Inspiron e1505) are optimized and really don't know how to proceed in checking.

Thanks for your input.

---

### Post by James^H on 2006-11-13
I havent researched editing that config file in a few months since I had to do it, but I would say it looks OK.

What I would suggest is that if it "feels" to be working correctly then I would **not** start messing around with it. At the least it could mean grief to you.

---

### Post by paulajohnw on 2006-11-14
After i get Blue "Xserver Failed" Screen and click OK on the error reports i am dropped on a Black Screen with a single blinking cursor.  I tried typing, "sudo nano /etc/xll/xorg.conf" <enter> Nothing happens cursor just drops down a line.  I also tried some of the other suggestions.  "sudo apt-get install xorg driver-fglrx" etc.  Nothing can be done from black screen.  Any Help?

---

### Post by paulajohnw on 2006-11-14
ANSWER HERE!!!!!

This is a very common problem and guess what I HAVE THE ANSWER!!!!!!!

I pieced this together over the last couple of hours.

1.  At the 1st screen where it gives you all the options for installing, press "F6" (Options)

2.  delete "  splash --" from the boot options

3.  Choose option #1 "Start or Install"

4.  Looks like nothing is happening for a couple of mins.  Probably depends on ur PC

5.  XServer Fails, Skip all the reports and such

6.  You should now get a terminal window.  Type the following...  
  "sudo apt-get install xorg-driver-fglrx" <enter>
  "sudo aticonfig --initial" <enter>
  "sudo aticonfig --overlay-type=Xv" <enter> (notice that is Xv not xv x is caps)

7.  startx
8.  viola

---

### Post by lilnerd on 2006-11-17
Is that for 6.10? The problem im getting is that when load the live cd it freezes. ALREADY TRIED IT ON OTHER COMPS AND BURNED ANOTHER CD.
Thanks,
lilnerd

---

### Post by lucagfc on 2006-11-22
I have the same problem with an x700 card on a laptop. I modify the config files with "sudo nano /etc/X11/xorg.conf" i write vesa instead of ati and when i write startx there is a problem with the monitor "monitor found but no configuration in correct" i tried to reconfig with "sudo dpkg-reconfigure xserver-sorg" and i saved only the monitor configuration but the system don't run. if i use the "radeon" driver instead of vesa the serverx don't have problem with monitor but the screen in black! help me

P.S. Sorry for my bad english

---

### Post by James^H on 2006-11-22
Boot up into recovery mode (selection at BOOT) and from there you can log in as root.

Hopefully it will have different settings than your own account, and X should start. From there you can copy your files to a new account or something.

At the minute I tried installing the bloody ATI drivers and now when I log in I get a corrupted screen. Will have a play around again tomorrow or something.

Ironically Linux people always bash Windows for BSODs etc, but here we are all getting Blue screens in Linux........

---

### Post by lucagfc on 2006-11-23
Nobody can help me?!? :(

---

### Post by iceburgh on 2006-11-30
> **paulajohnw said:**
> ANSWER HERE!!!!!

This is a very common problem and guess what I HAVE THE ANSWER!!!!!!!

I pieced this together over the last couple of hours.

1.  At the 1st screen where it gives you all the options for installing, press "F6" (Options)

2.  delete "  splash --" from the boot options

3.  Choose option #1 "Start or Install"

4.  Looks like nothing is happening for a couple of mins.  Probably depends on ur PC

5.  XServer Fails, Skip all the reports and such

6.  You should now get a terminal window.  Type the following...  
  "sudo apt-get install xorg-driver-fglrx" <enter>
  "sudo aticonfig --initial" <enter>
  "sudo aticonfig --overlay-type=Xv" <enter> (notice that is Xv not xv x is caps)

7.  startx
8.  viola

Thanks. Worked perfectly for me. Great help.

---

### Post by Ultimadark on 2006-12-02
I have a X850XT, and when I try to install Ubuntu 6.10 (this is the first time Im trying to install Linux), the first loading screen loads, but when the loading bar is almost full, my screen gets a little bit grainy and the loading bar freezes. There is also a green horizontal line below the loading bar. I logged onto IRC and a guy there with a X700 said that he had exactly the same problem.

Im gonna try to install Ubuntu 6.06 tomorrow, if someone knows whats wrong when I try to install 6.10 Ill be very happy :D

---

### Post by 56phil on 2006-12-02
I had the same problem with a X700. Things went better when I tried the safe graphics install in Dapper (6.06.1). If you really want Edgy, try the alternate install CD.

---

### Post by spliffy on 2006-12-16
i have a x800gto an the vesa driver didnot work i get a blank screen on reboot,
i have tryed all res settings??

---

### Post by jamaxus on 2006-12-16
i have the x9000 so im trying this now as i seem to get that message

---

### Post by Poirot on 2007-01-11
Hello, I have just installed a Club3Dx800RX graphics card. I get the same blue screen as the original post but I can't get from there to a console, I get...

> 'xserver is now disabled restart gdm when it is configured properly'

Then the screen just goes blank and I can type stuff but it is ignored. A useful amendment to the howto would be instructions to get to a terminal/console when faced with the blue screen.

I have managed to reboot in 'recovery' mode and have access to a console. Hooray!

However, my xorg.conf file doesn't list driver "ati" which can be changed to "vesa"

It does have this:

> Section "Device"
Identifier "NVIDIA Corporation NV11 [GeForce2 MX/MX 400]
Driver "nvidia"
BusID "PCI:1:0:0"
EndSection

I believe this nvidia reference is my old graphics card.

[LIST=1]
[*]Can I just replace "nvidia" with "vesa" as above?
[*]I cannot easily remove my new card since the catch on the AGP slot is blocked by the massive fan on the card. I need to fix this ideally without reverting back to my old card.
[/LIST]

---

### Post by Ranime on 2007-01-13
[B][SIZE="4"]@ Poirot
Oh yeah... don't forget to unload and uninstall your nVidia drivers first!!![/SIZE][/B]

> [LIST=1]
[*]Can I just replace "nvidia" with "vesa" as above?
[*]I cannot easily remove my new card since the catch on the AGP slot is blocked by the massive fan on the card. I need to fix this ideally without reverting back to my old card
[/LIST]

@1:  first of all you should replace 
> Section "Device"
Identifier "NVIDIA Corporation NV11 [GeForce2 MX/MX 400]
Driver "nvidia"
BusID "PCI:1:0:0"
EndSection

with:
```
Section "Device"
	Identifier  "ATI Technologies, Inc. ATI Default Card"
	Driver      "vesa"
	BusID       "PCI:1:0:0"
EndSection
```

as mentioned here: [http://ubuntuforums.org/showthread.php?t=190133&page=5]("http://ubuntuforums.org/showthread.php?t=190133&page=5")

2nd: When you've done that, it's gonne be a bit tricky... the settings above will give you vesa support up to 1024x768x24, but it won't give you accelerated 3D support for games like DOOM3 orso...

To get that, you either compile the driver from ATI wich 9 out of 10 times will work, if you follow the in structions from this howto: [ATTACH]22898[/ATTACH]. Go to **Using drivers from ATI.com** and follow it step by step.

OR...

Use the fglrx-driver from the repository, by reading this: [http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide")

when done that, find YOUR card from this mess:
```
ATI Radeon/FireGL: The following chipsets are supported:
	RADEON 9000/9000 PRO (RV250 4966), RADEON 9000 LE (RV250 4967),
	MOBILITY FireGL 9000 (M9 4C64), MOBILITY RADEON 9000 (M9 4C66),
	RADEON 9000 PRO (D9 4C67), RADEON 9250 (RV280 5960),
	RADEON 9200 (RV280 5961), RADEON 9000 (RV280 5962),
	RADEON 9200 SE (RV280 5964), FireMV 2200 PCI (RV280 5965),
	MOBILITY RADEON 9200 (M9+ 5C61), MOBILITY RADEON 9200 (M9+ 5C63),
	FireGL 8800 (R200 5148), RADEON 8500 (R200 514C),
	RADEON 9100 (R200 514D), RADEON 8500 AIW (R200 4242),
	RADEON 9600 (RV350 4150), RADEON 9600 SE (RV350 4151),
	RADEON 9600 PRO (RV360 4152), RADEON 9600 (RV350 4E51),
	MOBILITY RADEON 9600/9700 (M10/M11 4E50),
	MOBILITY RADEON 9500 (M11 4E52), MOBILITY RADEON 9550 (M12 4E56),
	RADEON 9500 (R300 4144), RADEON 9600 TX (R300 4146),
	FireGL Z1 (R300 4147), RADEON 9700 PRO (R300 4E44),
	RADEON 9500 PRO/9700 (R300 4E45), RADEON 9600 TX (R300 4E46),
	FireGL X1 (R300 4E47), RADEON 9800 SE (R350 4148),
	RADEON 9500 (R350 4149), RADEON 9550 (RV350 4153),
	FireGL T2 (RV350 4154), RADEON 9600 (RV351 4155),
	RADEON 9800 PRO (R350 4E48), RADEON 9800 (R350 4E49),
	RADEON 9800 XT (R360 4E4A), FireGL X2-256/X2-256t (R350 4E4B),
	MOBILITY FireGL T2/T2e (M10/M11 4E54), RADEON X300 (RV370 5B60),
	RADEON X600 (RV380 5B62), RADEON X550 (RV370 5B63),
	FireGL V3100 (RV370 5B64), FireMV 2200 (RV370 5B65),
	MOBILITY RADEON X300 (M22 5460), MOBILITY RADEON X300 (M22 5461),
	MOBILITY RADEON X600 (M24 5462), MOBILITY FireGL V3100 (M22 5464),
	RADEON X600 (RV380 3E50), FireGL V3200 (RV380 3E54),
	MOBILITY RADEON X600 (M24 3150), MOBILITY RADEON X300 (M22 3152),
	MOBILITY FireGL V3200 (M24 3154), RADEON X800 (R420 4A48),
	RADEON X800 PRO (R420 4A49), RADEON X800 SE (R420 4A4A),
	RADEON X800 XT (R420 4A4B), RADEON X800 (R420 4A4C),
	FireGL X3-256 (R420 4A4D), MOBILITY RADEON 9800 (M18 4A4E),
	RADEON X800 SE (R420 4A4F),
	RADEON X800 XT Platinum Edition (R420 4A50),
	RADEON X800 VE (R420 4A54), RADEON X800 (R423 5548),
	RADEON X800 PRO (R423 5549),
	RADEON X800 XT Platinum Edition (R423 554A),
	RADEON X800 GT (R423 554B), RADEON X800 XT (R423 5D57),
	FireGL V7100 (R423 5550), FireGL V5100 (R423 5551),
	MOBILITY RADEON X800 XT (M28 5D48), MOBILITY FireGL V5100 (M28 5D49),
	MOBILITY RADEON X800 (M28 5D4A), RADEON X800 XL (R430 554D),
	RADEON X800 GT (R430 554E), RADEON X800 GTO (R430 554F),
	RADEON X850 XT Platinum Edition (R480 5D4D),
	RADEON X800 GTO (R480 5D4F), RADEON X850 XT (R480 5D52),
	RADEON X850 (R481 4B48), RADEON X850 XT (R481 4B49),
	RADEON X850 SE (R481 4B4A), RADEON X850 PRO (R481 4B4B),
	RADEON X850 XT Platinum Edition (R481 4B4C),
	MOBILITY FireGL V5000 (M26 564A), MOBILITY FireGL V5000 (M26 564B),
	FireGL V5000 (RV410 5E48), FireGL V3300 (RV410 5E49),
	RADEON X700 XT (RV410 5E4A), RADEON X700 PRO (RV410 5E4B),
	RADEON X700 SE (RV410 5E4C), RADEON X700 (RV410 5E4D),
	RADEON X700 (RV410 5E4F), MOBILITY RADEON X700 (M26 5652),
	MOBILITY RADEON X700 (M26 5653), MOBILITY RADEON X700 XL,
	RADEON 9100 IGP (RS300 5834),
	RADEON 9000 PRO/9100 PRO IGP (RS350 7834),
	MOBILITY RADEON 9000/9100 IGP (RS300M 5835),
	RADEON XPRESS 200 (RS400 5A41), RADEON XPRESS 200M (RS400 5A42),
	RADEON XPRESS 200 (RS480 5954), RADEON XPRESS 200M (RS480 5955),
	RADEON XPRESS 200 (RS482 5974), RADEON XPRESS 200M (RS482 5975),
	RADEON XPRESS 200 (RC410 5A61), RADEON XPRESS 200M (RC410 5A62),
	RADEON X1800 (R520 7100), MOBILITY RADEON X1800 (M58 7101),
	MOBILITY RADEON X1800 (M58 7102), MOBILITY FireGL V7200 (M58 7103),
	FireGL V7200 (R520 7104), FireGL V5300 (R520 7105),
	MOBILITY FireGL V7100 (M58 7106), RADEON X1800 XT (R520 7108),
	RADEON X1800 PRO (R520 7109), RADEON X1800 SE (R520 710A),
	RADEON X1800 (R520 710B), RADEON X1800 (R520 710C),
	FireGL V7300 (R520 710E), FireGL V7350 (R520 710F),
	RADEON X1300 PRO (RV505 7143), RADEON X1300 (RV505 7147),
	MOBILITY RADEON X1300 (M52 714B), MOBILITY RADEON X1300 (M52 714C),
	RADEON X1300 (RV505 715F), RADEON X1300 XT (RV515 7140),
	RADEON X1300 PRO (RV515 7142), MOBILITY FireGL (M54 GL 7144),
	MOBILITY RADEON X1400 (M54 7145), RADEON X1300 LE (RV515 7146),
	MOBILITY RADEON X1300 (M52 7149), MOBILITY RADEON X1300 (M52 714A),
	RADEON X1300 SE (RV515 714E), FireGL V3300 (RV515 7152),
	RADEON X1300 VE (RV515 715E), RADEON X1300 (RV516 7180),
	RADEON X1300 (RV516 7183), RADEON X1300 (RV516 7187),
	RADEON X1900 (R580 7240), RADEON X1900 (R580 7243),
	RADEON X1900 (R580 7244), RADEON X1900 (R580 7245),
	RADEON X1900 (R580 7246), RADEON X1900 (R580 7247),
	RADEON X1900 (R580 7248), RADEON X1900 (R580 7249),
	RADEON X1900 (R580 724A), RADEON X1900 (R580 724B),
	RADEON X1900 (R580 724C), RADEON X1900 (R580 724D),
	RADEON X1900 (R580 724E), RADEON X1900 (R580 724F),
	RADEON X1600 XT (RV530 71C0), RADEON X1600 PRO (RV530 71C2),
	MOBILITY FireGL V5200 (M56 71C4), MOBILITY RADEON X1600 (M56 71C5),
	RADEON (RV530 LE 71C6), RADEON (RV530 VE 71CE),
	FireGL V3400 (RV530 71D2), FireGL V5200 (RV530 71DA),
	RADEON (RV530 SE 71DE)
```

And use the chipset code wher it said **ATI Technologies, Inc. ATI Default Card** @ the divice section mentioned earlier.

If you wish to view an example, check my post here: [http://ubuntuforums.org/showpost.php?p=1649168&postcount=37]("http://ubuntuforums.org/showpost.php?p=1649168&postcount=37")

Goodluck with it...

**[SIZE="4"]Oh yeah... don't forget to unload and uninstall your nVidia drivers first!!![/SIZE]**

---

### Post by ub_one on 2007-01-17
Hi,

I'm pretty new to the Linux world and I want to install Ubuntu (Desktop version) v 6.10.
My graphics card is an ATI X700 and I ran into the same blue screen. My question is, when do I have to type the [sudo nano /etc/X11....] ? How do I get to the terminal where I can type that? Because after the blue screen, just a black screen appears and that's it. 
Thx,:-k

---

### Post by ub_one on 2007-01-18
see next post..

---

### Post by ub_one on 2007-01-18
..I finally got into the vesa mode and I have managed to see the LIVE CD interface and the install icon on the desktop. Everything goes smoothly until I choose to do the operations of creating new partitions with the Ubuntu's Partition Tool during installation. After I have chosen the operations to be done, it asks me to confirm if I want to do them and I say yes and it freezes after a couple of seconds. Do you think that could be related to the vesa mode that Ubuntu has been loaded in or...is it something else ?
Thx again..:-k  

P.S. I guess I'll open a post or somthg in the Installation part of the forum to see what people have to say.

---

### Post by shamus390 on 2007-01-19
I'm running an x700 and having some problems. Once I set X to use the vesa driver, everything works fine, but when I try the fglrx driver, after the reboot the signal to the monitor dies. Ubuntu goes about it's normal start up sequence but when X starts the screen goes black. I then have to reboot into recovery and change back to vesa. Anyone have any insight?

---

### Post by eddgy on 2007-02-12
...or you could just select safe graphics mode at the beginning of the installation!

---

### Post by fjf314 on 2007-02-15
I just wanted to drop in and say thanks to edurm.  I have an ATI Radeon X600 and while I was able to install Ubuntu in Safe Graphics mode, but I couldn't figure out how to make my graphics not... suck.  I installed the ATI driver, but it didn't do much.  If I were to grab a window and drag it around, it would leave behind a lot of after-images.  Also, minimizing programs would cause there to be a lot of laggy black lines from the outline of the window going down to the bottom of the screen.  I was going to make a thread asking how to fix this, but following the directions in the first post really smoothed things out for me.  Thanks!

---

### Post by bill3763 on 2007-02-18
Thank you!  I've been trying to get my X300 sorted out for about 10 days worth of spare time reading ... these instructions sorted it for my Dell Dimension 5100, Edgy install.  I'm looking forward to the time my XP gets booted only at tax time ... well, that Intuit monopoly is getting kind of expensive ... maybe I'll just do em by hand!

---

### Post by Ozcu on 2007-02-27
osmo@osmo-laptop:~$ startx
xauth:  creating new authority file /home/osmo/.serverauth.5714

X: user not authorized to run the X server, aborting.
Couldnt get a file descriptor referring to the console


:lolflag: :( 

What to do?

---

### Post by pastrami on 2007-03-06
> **paulajohnw said:**
> ANSWER HERE!!!!!

This is a very common problem and guess what I HAVE THE ANSWER!!!!!!!

I pieced this together over the last couple of hours.

1.  At the 1st screen where it gives you all the options for installing, press "F6" (Options)

2.  delete "  splash --" from the boot options

3.  Choose option #1 "Start or Install"

4.  Looks like nothing is happening for a couple of mins.  Probably depends on ur PC

5.  XServer Fails, Skip all the reports and such

6.  You should now get a terminal window.  Type the following...  
  "sudo apt-get install xorg-driver-fglrx" <enter>
  "sudo aticonfig --initial" <enter>
  "sudo aticonfig --overlay-type=Xv" <enter> (notice that is Xv not xv x is caps)

7.  startx
8.  viola

Awesome!  That did the trick!  :)  Any suggestions on how I can include this if I want to re-burn the ISO disc?

---

### Post by Mischief on 2007-03-10
Hi,

I have the dreaded ATI Mobility Radeon X700 and was so happy when I found this guide. Been trying to get ubuntu running on my Acer Travelmate 8100 since July last year.

> **edurm said:**
> 

1) type: *sudo nano /etc/X11/xorg.conf* (Remember, Linux is case sensitive)


I did the changes from "ati"->"vesa" in xorg.conf

> **edurm said:**
> 
2) Find the line **driver "ati"** change it to **"vesa"** and then press Ctrl+x, then "Enter" to overwrite.

Now You will be able to start the "X", to do it type: *startx* then "Enter"

When I enter "startx", i get the following error:

[B]xauth:    creating new authority file /home/ubuntu/.xserverauth.6685

Fatal server error:
Server is already active for display 0
           if this server is no longer ruinning, remove /tmp/.X0-lock
           and start again.[/B]

What do I do next?

---

### Post by Hyter on 2007-03-10
I get this error message during the install.
Is there anyway I can get around it during the install?

---

### Post by igknighted on 2007-03-10
First, if you have an ATI card your best bet is to install via the alternate install CD and then fix the drivers.  Second, if "vesa" doesn't work for you, try "radeon".  My x800GTO works poorly with vesa (sometimes ok, sometimes nothing) but usually really well with "radeon".  Never with "ati".  Would be nice if Ubuntu would not just default to "ati" for ati cards as many have this issue... but thats another debate.  To get it all up and running requires jumping through a few hoops (and theoretically ATI is working on this... rumor has it AMD is turning them around and we can expect good things this year), but if you follow the procedures all these ATI cards work just fine.

---

### Post by lilnerd on 2007-03-11
I still am stuck in 6.06. please help...When load the live CD for 6.10 i get to the menu...and i select what i want to do...but it still freezes when loading up](*,) :evil: :icon_frown: ...i have a radeon x300. Also when I use the 6.06 live cd i have to do sudo nano /etc/X11/xorg.conf...then change ati to vesa....and when im done installing it i can change it to fglrx..so 6.06 is fine with the radeon, and also i can ubdate 6.06 to 6.10, but i want to do a clean install. So if anyone can help me it would be nice. BTW i have a pentium D 820 with 1 GB DDR ram, 80 GB samsung IDE hard drive...radeon x300 (128mb), ide dvd burner, and 500 watt power supply...just if you need to know.
Thanks again
lilnerd[-(

---

### Post by castoroil97 on 2007-03-16
After working 3 weeks on my video card, I downloaded envy and *FINALLY* got it working!!!

My ATI card was a 200m mobility express for a toshiba laptop

Hope this helps you!!!

Thanks Ubuntu community and especially the creator of envy!!!

Get Envy from here

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by The other One on 2007-03-23
> **paulajohnw said:**
> ANSWER HERE!!!!!

This is a very common problem and guess what I HAVE THE ANSWER!!!!!!!

I pieced this together over the last couple of hours.

1.  At the 1st screen where it gives you all the options for installing, press "F6" (Options)

2.  delete "  splash --" from the boot options

3.  Choose option #1 "Start or Install"

4.  Looks like nothing is happening for a couple of mins.  Probably depends on ur PC

5.  XServer Fails, Skip all the reports and such

6.  You should now get a terminal window.  Type the following...  
  "sudo apt-get install xorg-driver-fglrx" <enter>
  "sudo aticonfig --initial" <enter>
  "sudo aticonfig --overlay-type=Xv" <enter> (notice that is Xv not xv x is caps)

7.  startx
8.  viola

I was ready to give up on Ubuntu, but this worked PERFECTLY for me (radeon X850). Thanks to you all.:KS :KS :KS :KS :KS

---

### Post by efthin on 2007-03-24
Cheers mate good post. I had to use this solotion to get my X850 XT to work

> **Eoin said:**
> sudo apt-get install xorg-driver-fglrx
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv


---

### Post by Harkonnen on 2007-03-27
I'm getting an x server error when I try to load the Ubuntu live CD (6.06). My video card is a Radeon 9200se. I have an Intel on-board video as well, but it has been disabled in BIOS. I think it may be causing some sort of conflict. I was wondering if the solution here would work for me too. Here are some pictures of the error.

[[COLOR="Blue"]XserverError1[/COLOR]]("http://harkonnen19.googlepages.com/xservererror1.jpg")

[[COLOR="Blue"]XserverError2[/COLOR]]("http://harkonnen19.googlepages.com/xservererror2.jpg")

[[COLOR="Blue"]XserverError3[/COLOR]]("http://harkonnen19.googlepages.com/xservererror3.jpg")

[[COLOR="Blue"]XserverError4[/COLOR]]("http://harkonnen19.googlepages.com/xservererror4.jpg")

Also, on the fourth image. The text isn't always that neat. It is usually covered in blue and when hitting enter the command line moves around.

PS: I am not gonna use 6.10 because for some reason it shuts my CPU fan off when trying to boot. I don't even want to deal with that ATM. :P

---

### Post by Harkonnen on 2007-03-28
Or is this what I have to do? I am not looking to install this right now.

> 1) type: sudo nano /etc/X11/xorg.conf (Remember, Linux is case sensitive)

2) Find the line driver "ati" change it to "vesa" and then press Ctrl+x, then "Enter" to overwrite.

Now You will be able to start the "X", to do it type: startx then "Enter"

3) Now The ubuntu was loaded and you will see a install shortcut in your desktop screen. Well, now just follow the install instruction and setup the system. After you complete the process you will be in a black terminal screen again. Don't worry it just happened because GDM wasn't full loaded and after restart it will not happen again. To restart type sudo shutdown -r "now"

---

### Post by U2XS on 2007-09-04
> **Phasmagon said:**
> it is really rather easier than that.
In a terminal type

sudo apt-get install xorg-driver-fglrx
sudo aticonfig --initial
sudo aticonfig --overlay-type-Xv

and then either startx if you are in console
or Ctl+Alt+Backspace if in virtual terminal.

OMG!  I don't even know what it did but it worked quickly and perfectly!  Thanks for posting!

---

### Post by addrever on 2007-09-06
What do you do if this happens when loading the LiveCD?  I have the most current "desktop" live cd.

---

### Post by McGriff on 2007-09-06
ok i know im gonna get WRONG TREAD all over this but i have asked this question in 3-4 different treads without any response 

i have a x1800 and and ubuntu 7.04 and i am having the same driver type probs will the things suggested work on this card or is it just for older ati cards i would just like any infor on this as ive been trying for weeks already and i dont want to waste trying loads of things that wont work AGAIN 

thanks in advance
GRIFF

---

### Post by KingArthur10 on 2007-09-06
My recommendation is to use the Automatix installer to get the fglrx drivers installed.  One thing sometimes you have to check, though, is that in /etc/X11/xorg.conf at the bottom section, it says Option "Composite" "False" or Option "Composite" "0".  If you have a true or a 1, it will not work right.  You can check this by goiong to the terminal after installing the driver via automatix and typing "sudo gedit /etc/X11/xorg.conf"  Scroll to the bottom and check.  if you have a false or a 0, just reboot and you should have your graphics card configured correctly.  Hope this isn't too jumbled.

---

### Post by McGriff on 2007-09-06
ok man ill give it a shot heres hopeing thx again

---

### Post by airtonix on 2007-09-18
always, always, always, always, use this to start or restart X.

stop X : 
> sudo /etc/init.d/gdm stop 

start X:
> sudo /etc/init.d/gdm start 

restart X:
> sudo /etc/init.d/gdm restart 

---


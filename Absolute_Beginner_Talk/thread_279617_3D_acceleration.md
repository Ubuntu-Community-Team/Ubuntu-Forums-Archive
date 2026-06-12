---
title: "3D acceleration"
date: 2006-10-18
forum: Absolute Beginner Talk
---

### Post by lifemaximum on 2006-10-18
hi
how can i find out if i can have 3d acceleration available in a normal gnome session?

how do i find out my graphic card model using codes/ to see whethere i can install Beryl or not ??

---

### Post by xpod on 2006-10-18
Me thinks if you look in this you will find that out

```
gksudo gedit /etc/X11/xorg.conf
```

---

### Post by lifemaximum on 2006-10-18
Should i install the beryl or xgl? is it all that good... i tried installing the ATI driver for my laptop and xserver got screwed up so i had to reinstall it again....

```
    GLX_SGI_video_sync, GLX_SGIS_multisample, GLX_SGIX_fbconfig
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI R200 20060602 AGP 1x TCL
OpenGL version string: 1.3 Mesa 6.5.1
OpenGL extensions:

```

i am jus all confused here...alittle help will be apperciated.](*,)

---

### Post by CatKiller on 2006-10-18
```
glxinfo | grep render
```
If it says "direct rendering: Yes" then you have 3D acceleration.

```
lspci | grep VGA
```
will tell you what your graphics card thinks it is.

---

### Post by xpod on 2006-10-18
lol.....i looked for the specific commands for him but could`nt find them again..
The Xorg.conf was the next best thing i thought.

Ive only just installed a proper nvidia card and the beta\edgy stuff.Got it all working and we all love it in this house.

Who needs wonky windows when you can have wobbly windows:-D

EDIT:"lspci" on its own was the one i forgot...shows everything

---

### Post by lifemaximum on 2006-10-18
alrite dude thanks for the help ....it worked 

```

faz@max-laptop:~$ glxinfo | grep render
direct rendering: Yes
OpenGL renderer string: Mesa DRI R200 20060602 AGP 1x TCL
faz@max-laptop:~$ lspci | grep VGA
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R250 Lf [FireGL 9000] (rev 01)
faz@max-laptop:~$

```

now is my graphic card compatiable for beryl...can i install the ATI drivers for it ? where to install it ? and how ?

---

### Post by xpod on 2006-10-18
This what i followed...it has links for all kinds

[http://www.ubuntuforums.org/showthread.php?t=263851](http://www.ubuntuforums.org/showthread.php?t=263851)

---

### Post by lifemaximum on 2006-10-18
by the way i tried to install the ATI drivers , using the methods provided in ubuntu guide...but like i said after installing it when i restarted my laptop...i got a screen spilt in 2 and one side was white and the other side brown...and that is all i could see...??](*,)

---

### Post by xpod on 2006-10-18
I could be wrong but i think theres more than one way for installing all this stuff for any one particular card and you may just need to find the right method for your hardware...

I had to try a couple of different ways with it all in dapper, gnome & kde and never did get it sorted in gnome properly.
It all works great in edgy though so im ok......for now:???:

---

### Post by lifemaximum on 2006-10-18
i guess i should give the ATI website a visit and download the driver from there....why couldn't i think of that earlier...thanks for all your help.

---

### Post by Delkster on 2006-10-18
With their recent driver releases, ATI has just dropped support for old R200 (and R250) based cards. You can have 3D acceleration (although it's not very fast) with your R250-based card with just the drivers included in Ubuntu, and it's actually even enabled by default.

I have an R200 and use the open-source drivers that come with Ubuntu because the proprietary drivers from ATI aren't that great (in OpenGL they're faster than the open-source driver but that's about it) and they're a lot more hassle.

If you decide to stick with the open-source driver, you might want to enable 4x AGP mode, though, since it doesn't seem to be enabled by default (it wasn't for me either). If you want to know how to do that, please ask. It takes a while to explain it well (although it's not very hard to do with good instructions) and it wouldn't be useful if you decide to take the proprietary ATI driver instead. (The settings are probably different, and it enables 4x AGP mode by default anyway.)

---

### Post by lifemaximum on 2006-10-18
I installed the driver from the ATI website..restarted my laptop and u can guess what happen.... i got an error for my xserver it was not working and i was shifted to recovery mode...what should i do now to get the my xserver back...](*,) ](*,)  HELP


and yea i would like to learn to do that..i would apperciate if you provide me with the instructions on that...

---

### Post by Delkster on 2006-10-18
For now, just try logging in at the text console you got and enter the following command:
```
sudo dpkg-reconfigure xserver-xorg
```
It'll ask for your password and should ask you a number of questions. Choose the default option at each of them, except that for the video driver you should choose "ati" instead of "fglrx" (if it suggests that). You may also want to check if the available resolutions it suggests are what you want. After you finish answering the questions you should have a new working X server configuration.

You can now try restarting the X server with the following command:
```
sudo /etc/init.d/gdm restart
```
or you can reboot the system by hitting Ctrl+Alt+Delete.

Let us know if you got your X server working again, and if you did, we'll get on to enabling AGP 4x mode.

---

### Post by lifemaximum on 2006-10-19
i already tried reconfigureing xserver and restarting gdm
i think it mite have something to do with gdm file which i modified ....how can i get it back again i mean the defualt file ???

---

### Post by lifemaximum on 2006-10-19
i tried this how to which asked for a few files to be modified.. can u check and tell me if i did anything wrong.. or there is something wrong with the how to and which file i need to replace ? it would be much apperciated


```
1. Get Radeon Going
First, we need to remove xorg-driver-fglrx

Code:
sudo aptitude remove xorg-driver-fglrxOK now lets grab the newest radeon driver from the compiz/beryl repos.

Code:
gksudo gedit /etc/apt/sources.listAnd add this to the end:

Code:
deb http://www.beerorkid.com/compiz dapper main aiglx
deb http://media.blutkind.org/xgl/ dapper main aiglxnow add in the right stuff for the radeon driver:

Code:
sudo aptitude update
sudo aptitude dist-upgrade
sudo aptitude reinstall libgl1-mesa libgl1-mesa-driOK now we need our Xorg.conf to be ready

Code:
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo gedit /etc/X11/xorg.confHere are the areas of interest:

Code:
Section "Module"
	Load	"bitmap"
	Load	"dbe"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

#...

# Leave the identifier and BusID alone, but add the options
Section "Device"
	Identifier	"YOURS HERE"
	Driver		"radeon"
	BusID		"YOURS HERE"
	Option	  "backingstore" "true"
	Option	  "EnablePageFlip" "true"
	Option	  "SubPixelOrder" "none"
	Option	  "AccelMethod" "XAA"
	Option	  "RenderAccel" "true"
	Option	  "AGPMode" "4"
	Option	  "ColorTiling"   "on"
	Option	  "DynamicClocks" "on"
	Option	  "mtrr" "on"
	Option	  "VideoOverlay" "on"
	Option	  "OpenGLOverlay" "off"
EndSection

#...

Section "Screen"
	Identifier	"YOURS"
	Device		"YOURS"
	Monitor		"YOURS"
	DefaultDepth	24
	SubSection "Display"
		Depth		24
		# You can put your modes below, for your own resolutions, these are mine:
		Modes		"1400x1050" "1280x1024" "1280x800" "1024x768" "800x600" "640x480"
	EndSubSection
EndSection

#...

Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
	Option "Composite" "Enable"
EndSectionNow set up the modules to get the right ones at boot:

Code:
gksudo gedit /etc/modulesMake sure that you have these lines:

Code:
#agpgart # you dont need these two lines, just make sure they are NOT there
#fglrx
drm
radeonAdd a little something to your .drirc to get full resolution support:

Code:
gedit ~/.drirccontents:

Code:
<driconf>
    <device screen="1" driver="r200">
        <application name="Default">
            <option name="allow_large_textures" value="2" />
        </application>
    </device>
</driconf>Now reboot to get the modules to load.

If this didn't work and you got a text login, login and do "sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf" and then "sudo /etc/init.d/gdm restart". If you had to do this, you should stop now, you won't be able to get farther.

For the rest of you, log in to gnome and open a terminal and type:

Code:
glxinfo | grep renderingand make sure you get a Yes.

OK Part 1 is done.

2. XGL Time!
So Compiz-quinnstorm forked to Beryl, which is what this howto will now cover.

First, lets install xgl and Beryl:

Code:
sudo aptitude install xserver-xgl beryl emerald-themesNow I dont know about you guys, but I hate switching GDM to XGL, because if it messes up I have to use the text console, so we are going to make our own xgl session.

Code:
sudo gedit /usr/share/xsessions/xgl.desktopHere is the content:

Code:
[Desktop Entry]
Encoding=UTF-8
Name=XGL
Exec=/usr/bin/startxgl.sh
Icon=
Type=ApplicationOK now we need to make /usr/bin/startxgl.sh:

Code:
sudo gedit /usr/bin/startxgl.shcontents:

Code:
Xgl -fullscreen :1 -ac -accel xv -accel glx:pbuffer &
DISPLAY=:1
# Start GNOME
exec gnome-sessionnow make it executable:

Code:
sudo chmod +x /usr/bin/startxgl.shOK now log out and press CTRL+ALT+BACKSPACE. Click Options and then Select Session. Choose XGL. Log in and click "Just for this session" just in case it messes up.

To edit beryl related settings, run csm. To edit the window manager themes, run "beryl-settings".
```

---

### Post by lifemaximum on 2006-10-19
is there anything that can replace xserver?

---

### Post by lifemaximum on 2006-10-19
okie the latest error that i got is 

```

x:warning ; process set to priority -1 instead of requested priority 0
```

anybody knows what should i do now ? i am desperate

---

### Post by Delkster on 2006-10-20
If you think something may be wrong with your gdm configuration, you could try cleaning it and reinstalling gdm to get the defaults back:
```

sudo mv /etc/gdm /etc/gdm.backup
sudo apt-get install --reinstall gdm

```
Normally reinstalling the package with the --reinstall flag does not replace the existing configuration with the default one, but if configuration files are missing it does install the default configuration.

If that doesn't work, could you post your X.org log, probably located at **/var/log/Xorg.0.log**?

---


---
title: "setting screen resolution on my laptop"
date: 2006-08-23
forum: Absolute Beginner Talk
---

### Post by Phshy on 2006-08-23
*removed comment about title...* --matthew

I've been a windows user so many years now, and now decided to install ubuntu onto my laptop (A Gateway 400 VTX). Well so far the only nice experience I've had is not having to jump through hoops to format the HD (thankfully the install process took care of it easily).

So having used a 16x12 resolution on my windows pc for so many years, the first thing I wanted to do was to change it from the default 800x600 to 1204x768 (The laptop's max resolution). Well I was pretty surprised to see it wasn't available (only 8x6 and 640x480 are). 
So to find a fix to my resolution problem, naturally I googled, found a lot of forum posts, but no definitive answer ( [http://www.wplug.org/pipermail/wplug/2003-November/019998.html](http://www.wplug.org/pipermail/wplug/2003-November/019998.html) is the best I've seen).

I made a backup of the xorg.conf file and edited it according to the above link (default depth to 16 rather than 24, and left only  Depth  16 and Modes  "1024x768" under SubSection Display), restarted and nothing has changed (8x6 and 64x48 are still the only resolutions available).

Thought I'd go about finding a display driver for my chip and came across [http://intellinuxgraphics.org/download.html](http://intellinuxgraphics.org/download.html) , but "Compiling and/or upgrading video drivers in Linux is a complex and error-prone task. If you are not experienced doing this, we recommend that you get precompiled packages from one of the many Linux distributions. "

That ended up scaring me off to here. Any way I can get 1024x768 resolution? If it requires a video driver (for a 82852/855GM chip) any recommendations to which I should use?

I don't want to noose up the penguin just yet, especially over a resolution problem. Thanks for any help.

Full specs of the laptop are here: [http://support.gateway.com/s/Mobile/Gateway/400VTX/3501331sp47.shtml](http://support.gateway.com/s/Mobile/Gateway/400VTX/3501331sp47.shtml)

Here are the video specs

Video
# Graphics controller     Intel 852MG (chipset integrated)
# 2D hardware acceleration
# 3D rendering acceleration
________________________________________________________________

Video memory:     UMA (shared memory) architecture with Dynamic Video Memory Technology (DVMT)
________________________________________________________________

# LCD display panel:     15.0-inch active matrix (TFT) LCD color display
# Maximum panel resolution: 1024 × 768
# Maximum color depth: 18-bit (262,144 colors)
LCD supported video modes:     XGA
LCD maximum refresh rate:    60 Hz
________________________________________________________________

External video     Supports dual display and dual view
External CRT resolutions     Supports standard IBM VGA compatible modes
Maximum resolution: 1,920 × 1,200 × 16-bit colors
External CRT maximum refresh rate     85 Hz

---

### Post by Tomosaur on 2006-08-23
I'm not persnally familiar with your exact chip, but try the following command in the termina:
```

sudo apt-get install 915resolution

```
Once it's installed, type 'man 915resolution' and use the info in there to alter your resolutions. 

Sorry I couldn't be any more help.

---

### Post by Phshy on 2006-08-23
No luck using 915resolution
(Pretty sure I did it right, edited /etc/default/915resolution, entered the mode, x/yreso and bit correctly.)
Edited xorg so it now looks like

Section "Screen"
Indentifier "Default Screen"
Device "Intel Corporation 82852/855GM

Integrated Graphics Device
Monitor "Generic Monitor"
DefaultDepth 16
SubSection "Display" 16
Modes "1024x768" "800x600" "640x480" EndSubSection
EndSection

Still exactly the same though, only 8x6 and 64x48 are available and 8x6 is the default

---

### Post by xmastree on 2006-08-23
Could this be yet another screen refresh rate problem?
Some insallations require specific refres rates in xorg.conf.

Mine (not a laptop) is like this:
```
Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
[COLOR="Red"][B]	HorizSync	28-64
	VertRefresh	43-60[/B][/COLOR]
EndSection
```

Those bits in red, does yours have them?

---

### Post by Phshy on 2006-08-23
HorizSync 28-51
VertRefresh 43-60

is what I have in xorg

---

### Post by bensexson on 2006-08-23
A Google search came up with this: [http://www.linuxquestions.org/questions/showthread.php?t=321336](http://www.linuxquestions.org/questions/showthread.php?t=321336)

---

### Post by Phshy on 2006-08-23
Doesn't look like the guy got the fix he was hoping for, its probably just stuck at 8x6. 
Also either I don't have xorgcfg or I'm trying to run it wrongly, do I have to download this seperately?

---

### Post by TFX360 on 2006-08-23
xorg.conf is found in /etc/X11/

Backup first open a Terminal


```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bck
```


If anything fails cp the other way around to recover from a faulty conf.

and then type in the Terminal


```
gksu gedit /etc/X11/xorg.conf
```



Should get you in it good and editable...

---

### Post by frrobert on 2006-08-23
I had a same type of problem

I went to [https://help.ubuntu.com/community/FixVideoResolutionHowto?highlight=%28video%29](https://help.ubuntu.com/community/FixVideoResolutionHowto?highlight=%28video%29)


And followed the following instuructions.  I doesn't always work but it is easy to try and works a good portion of the time.

Hope this helps

Run the Autodetect Script Again

I'm not sure that this is the solution that works for the most people actually, but it most certainly is the quickest and easiest one. All we're doing is running the same script that tried to detect your video hardware when you initially installed. Sometimes this does help. Run the following command.

For Ubuntu 6.06 (Dapper Drake):

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.custom
sudo sh -c 'md5sum /etc/X11/xorg.conf > /var/lib/x11/xorg.conf.md5sum'
sudo dpkg-reconfigure xserver-xorg

---

### Post by Phshy on 2006-08-23
The autodetection didn't work out :(

I tried what TFX360 said, and after typing gksugedit /etc/X11/xorg.conf I got this message:

GnomeUI - WARNING **: While connecting to session manager: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

After that it opened up xorg.conf (But as far as I can tell in the same way as when I typed 'sudo gedit /etc/X11/xorg.conf'

So still no luck :confused:

---

### Post by frrobert on 2006-08-23
I believe TFX360
 meant gksudo gedit /etc/X11/xorg.conf

---


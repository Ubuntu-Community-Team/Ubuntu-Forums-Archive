---
title: "Big Problem!"
date: 2006-01-29
forum: Absolute Beginner Talk
---

### Post by linuxnovice on 2006-01-29
Hello People,
Two days into Ubuntu and I have already messed up the OS. Oh well, they say keep trying dont they? :) 
So here is my problem:

Everything was working fine except for my screan resolution which was set at 640x480. Now I have an IBM 6332 E74 17" moniter with the following rates:

Horz : 30-69KHz
Vert : 50-120Hz

My Video card:
82845G/GL/GV/GE/PE Integrated Graphics Device with total of 1MB of memory. My windows is right now running at 1074x768 at 24 bit. This is the max I believe for my Video card and montier combination.

So after searching the net and the forum, I found a way to correct my res in Ubuntu. 
This is what I did:
cat /etc/X11/xorg.conf
sudo dpkg-reconfigure xserver-xorg.
It opend up a panel which guided me thro the installation and I accepted everything default.
Today morning I boot up my machine and Ubuntu says Failed to Start the X server. I can to into console though.
I came into windows and did a search online and found this website :
[https://wiki.ubuntu.com/FixVideoResolutionHowto](https://wiki.ubuntu.com/FixVideoResolutionHowto)
I did as instructed for like 5 times! but no use. It refuses to enable my X server. Also I see that when Ubuntu is loading the modules I get this:
mounting local filesystems    Failed

I dont know what happened and would really appreciate it if anyone could help me out. Is there something I can do or do I need to re-insall ubuntu over again???
Thanks,
Linuxnovice.

---

### Post by bscbrit on 2006-01-29
OK, the main error is the failure to mount local drives - I suspect that your monitor problem might also be related to this, perhaps it cannot find the video specification at boot up.  On the commandline, type the following:

df

which will show you how much space you have on each of your drives.  The right-hand column is 'Mounted on' which specifies each of your mount points.  Change to each of your regular directories in turn (ignore /dev.... etc) and find out which one has not mounted - it will be empty when it shouldn't be.

Armed with this information, come back here with it and a copy of your /etc/fstab and we will see if we can get it remounted.

---

### Post by linuxnovice on 2006-01-29
Hello,
Thankyou bscbrit, for your suggestion. Here is the info I got after following your instructions:

df output:
Filesystem                   Mounted On                          Use%
/dev/hda6                        /                                      21
tmpfs                            /dev/shm                              0
tmpfs             /lib/modules/2.6.12-9-386/volatile            2
/dev/hda5                      /boot                                   1
/dev/hda1                     /media/hda1                          49

You said info about regular directories, but I dont know which ones are regular.

I got info for /etc/fstab:

Filesystem              MountPoint        Type       Options         Dump    Pass 
proc                         /proc             proc         defaults        0          0 
/dev/hda6                  /                  ext3   defauts,error=remount-ro 0  1
/dev/hda5                /boot              ext3         defaults         0          2
/dev/hda7                none               swap          sw              0           0
/dev/hdc            /media/cdrom0    udf,iso 9660 user,noauto     0          0
/dev/fd0            /media/floppy        auto          rw,use,noauto 0          0
/dev/hda1         /media/windows     ntfs        ns=utf8,umask=0222 0     0

I dont know whether this is the info that you require. If its not, please can you tell me which command I need to use to get the required info?
Thanks!
Linuxnovice.

P.S : I have ubuntu live CD. Will that help in anyway?

---

### Post by xmastree on 2006-01-29
[QUOTE=linuxnovice]
Horz : 30-69KHz
Vert : 50-120Hz

sudo dpkg-reconfigure xserver-xorg.
It opend up a panel which guided me thro the installation and I accepted everything default.[/quote]I suspect that was your mistake.
Reconfiguring xserver will just put it back to how it was after the initial install, which clearly wasn't correct.

All you needed to have done was put those refresh rates in the correct place in your /etc/X11/xong.conf and it would probably have been fine.

What's the error you get when trying to start x server? Run **startx** from the terminal and see what the error is...

Did you make any backup of the file first? restoring that one might get you back to your 640x480 desktop from where you can get further.

Rather than running reconfigure again, I suspect you're gonna have to edit xorg.conf from your terminal (not as scary as it seems) and fix it manually.

---

### Post by bscbrit on 2006-01-29
Your filesystems seem to have loaded OK - I cannot see any that haven't.  Next time you boot try to get a more accurate description of the error message e.g. exactly what it says, whereabouts in the boot it takes place.  I know that these sound difficult but just do the best that you can.

There is one anomaly:

Accorcding to your fstab /dev/hda1 should be mounted as /media/windows, yet it appears to have been mounted as /media/hda1.  I'm not sure why this should be, unless you have been mounting/unmounting drives manually.  That would explain it.  However, if 'df' can find it is is obviously readable and it will not have affected the boot up procedure.

> 
df output:
/dev/hda1 /media/hda1 49

I got info for /etc/fstab:

Filesystem MountPoint Type Options Dump Pass
/dev/hda1 /media/windows ntfs ns=utf8,umask=0222 0 0


Other than that, we need the answers to xmastree's questions, particularly what happens when you try to startx?

---

### Post by linuxnovice on 2006-01-29
Hello bscbrit,
I got into GNOME! I searched more in the forum and found this :
sudo nano /etc/X11/xorg.confg~
I saved the file after removing the ~ and ran sudo dpkg-reconfigure -phigh xserver.xorg. This didnt help, as it didnt detect my video settings automatically.

Then, I ran sudo dpkg-reconfigure xserver-sorg. I did some configuring again restarted GDM by using sudo /etc/init.d/gdm restart. I came into my desktop. However, my screen resolution is still small remaining at 640x480 and the module loading screen still shows Mounting Local file systems as failed. Is there any way I could correct this?
Thanks!
Linuxnovice.

---

### Post by bscbrit on 2006-01-29
Yes - but first of all make a backup copy of your working xorg.conf e.g.

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.working
sudo chmod -w /etc/X11/xorg.conf.working

The easiest way is simply to copy and paste the 2 lines above into a terminal window.  What it does is make a copy and then change its permissions to read-only - that way you cannot delete it without trying. :D 

Next, open your version of xorg.conf and highlight the parts relating to 'Monitor' and 'Screen', copy and paste them back here and I can suggest what to edit.

---

### Post by xmastree on 2006-01-29
Ok, first thing is, **stop running dpkg-reconfigure**. It obviously can't detect things correctly. The answer to you 640x480 question is simple, you need to enter your monitor's reftesh rates into xorg.conf and restart.

I assume you have a desktop at the moment? run this
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo gedit /etc/X11/xorg.conf
```The first line backs up your current file, just in case...

The next one will open an editor. Scroll down until you see a section which looks like this: ```

Section "Monitor"
	Identifier	"NEC CI CT700"
	Option		"DPMS"
EndSection
```
Yours will be slightly different, due to the diffrent monitor.

Add the two lines below, (marked in red) **before** the 'EndSection' line, like this:
```

Section "Monitor"
	Identifier	"NEC CI CT700"
	Option		"DPMS"
[COLOR="Red"]	HorizSync       30-69
        VertRefresh     50-120
[/COLOR]EndSection
```(I got those figures from your previous post)

Then restart x.

However, I notice that you only have 1MB of video RAM? Look further down for sections like this:
```
SubSection "Display"
		Depth		24
		Modes		[COLOR="Red"]"1280x1024" "1152x864" [/COLOR]"1024x768" "832x624" "800x600" "720x400" "640x480"
``` and I suggest you remove any references to modes higher than 1024x768. Also, at the top of that section it will probably say **default depth 24**, I suggest changing that to 16.

---

### Post by linuxnovice on 2006-01-29
Hello,
Thanks for all your help bcsbrit, I am very grateful. I did exactly what you told, cut and paste :D (easier you know....). I thought you might need all the info so here my xorg.conf. 
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
	FontPath	"/usr/share/X11/fonts/CID"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"GLcore"
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
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

[COLOR="Blue"]Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-51
	VertRefresh	43-60
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Monitor		"Generic Monitor"
	DefaultDepth	16
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

[/COLOR]Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection

---

### Post by xmastree on 2006-01-29
That looks good, but the refresh rates are different from the ones you quoted in your first post. Try altering them to what matches your monitor.

---

### Post by bscbrit on 2006-01-29
Xmastree beat me to it!

Make the changes and restart X.  However, before you do, just try System -> Preferences -> Screen Resolution and see if you can select a higher res from there.  However, your horizontal and vertical sync settings in xorg.conf do need changing to the correct values.

---

### Post by linuxnovice on 2006-01-29
Hello,
I changed the refersh rate as per my requirements xmastree. Now, system->preferences->screen resolutions, it shows my referesh rate as 85Hz (originally it was 60Hz) but MY SCREEN RESOLUTION IS STILL AT 640x480! Wont it ever change? Now my screen has a center square surrounded by black on all four sides. Please tell me what I need to do...
Thanks,
Linuxnovice.

---

### Post by xmastree on 2006-01-29
Try reducing the colour depth. It'll look ugly, but it might help diagnose the problem. back to the file, change depth from 16 to 8.
```
DefaultDepth 16
```

Is your video RAM really only 1MB?

> 82845G/GL/GV/GE/PE Integrated Graphics Device with total of 1MB of memory. My windows is right now running at **[COLOR="Red"]1074x768 at 24 bit[/COLOR]**. This is the max I believe for my Video card and montier combination.That needs at least 2.25MB of RAM...

Even at 16 bit you need 1.5MB of video RAM.

---

### Post by linuxnovice on 2006-01-29
Well,
No change, except as you said, it looks ugly. Let me go into windows check the amount of video RAM that I have again. In case it is the same, do I need a driver update or something? Is there anything that I can do for that mounting filesystem failure error.
Linuxnovice.

---

### Post by linuxnovice on 2006-01-29
Well,
Sorry to bother you guys so much. But I am really desperate to get linux working because I need it to use it for my project. The site below gives the details of my montier:
[http://www-307.ibm.com/pc/support/site.wss/document.do?sitestyle=lenovo&lndocid=MIGR-4W4KVX](http://www-307.ibm.com/pc/support/site.wss/document.do?sitestyle=lenovo&lndocid=MIGR-4W4KVX)
Apparently I saw another very very similar model which had the exact opposite refresh rates (sorry guys :oops:) 

This is my video card info as given by PC Wizard:

General Information :	 
Model :	82845G/GL/GV/GE/PE Integrated Graphics Device 
Manufacturer :	IBM 
Bus Type :	PCI 
Manufacturer :	Intel Corporation 
Total Memory :	1 MB 
Texture Memory :	51 MB 
Processor :	Intel(R) 82845G Graphics Controller 
Converter :	Internal 
Refresh Rate (min/max) :	60/120 Hz 

Well any suggestions on what to do now?

Thanks,
Linuxnovice.

---

### Post by xmastree on 2006-01-29
Try changing the driver from i810 to vesa, like this:
```
Section "Device"
Identifier "Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
[COLOR="Red"]**[SIZE="2"]#[/SIZE]**[/COLOR] Driver "i810"
[COLOR="Red"]**Driver "vesa"**[/COLOR]
BusID "PCI:0:2:0"
EndSection
```You could delete the Driver "i810" line, but commenting it like that makes it easier to revert if it has no effect.

Isn't the i810 a built-in one? How much memory have you allocated in the BIOS?

(running out of ideas here...)

---

### Post by linuxnovice on 2006-01-29
Seeeesh,
I must be windows novice too :P :D My video card has approx 64MB of RAM!
Now what?
Linux/Windowsnovice..

---

### Post by xmastree on 2006-01-29
64MB, that's more like it.

All I can see is it's an 82845, and you're using the 810 driver. I've used systems with the 810 chipset and they worked fine, but yours is 845... check my last post, try the vesa option. It may still look ugly, but it may give us more clues.

---

### Post by xmastree on 2006-01-29
Found this:
[http://ubuntuforums.org/showthread.php?t=27029](http://ubuntuforums.org/showthread.php?t=27029)
But it seems to have mixed results...

---

### Post by bscbrit on 2006-01-29
I've been doing a bit of googling.  The 82845 does use the i810 driver and it has a known problem with artifacts.

However, it should be capable of up to 1280x1024 depending upon the monitor in use and some have had great success using it under Mepis - so it can be coaxed into working with linux.

My feeling is that there is more than one problem here - don't forget this all started with the graphics problem, and then there were the reported disk mounting problems (which we haven't heard about recently - have they gone away?) and then back to the graphics.

Not that much of the above helps but I am also running out of useful suggestions to make.  All the usual problems regarding a computer display that will not open at the desired resolution have been looked at and appear to be absolutely normal.

Still thinking, and always searching for an answer....

---

### Post by xmastree on 2006-01-29
Yeah, I'm almost out of ideas too, and it's bedtime here anyway...
This one's all yours, bscbrit. Say hello to the Barbary Macaques for me. :D

---

### Post by bscbrit on 2006-01-29
linuxnovice - are you still seeing the same problems with the disks not mounting at boot time and, if so, what is the error message (well as much of it as you can remember)?

---

### Post by linuxnovice on 2006-01-29
Hello bcsbrit,
Well, sorry it took me so long to reply. I had to leave the pc because something had come up. Anyway, just before you are prompted for the username and password, you get a screen which says ubuntu and below it starts with loading module like this:

Loading modules                      ok
.....                                             ok
....                                              ok
.....                                             ok
Checking file systems              ok
Mounting local filesystem     [COLOR="Red"] failed[/COLOR]
....                                               ok
....                                               ok
Its still there. As for the res....take a look at my xorg.conf. My machine is too weird. Its detected my moniter but its wiped out the refresh rates :confused: :

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
	FontPath	"/usr/share/X11/fonts/CID"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
        # paths to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/CID"
EndSection

Section "Module"
	Load	"GLcore"
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
	Option		"Protocol"		"ImPS/2"
	Option		"Emulate3Buttons"	"true"
	Option		"ZAxisMapping"		"4 5"
EndSection

Section "Device"
	Identifier	"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
EndSection

[COLOR="Blue"]Section "Monitor"
	Identifier	"IBM 6332 E74"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device"
	Monitor		"IBM 6332 E74"
	DefaultDepth	16
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
[/COLOR]
Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
EndSection

Section "DRI"
	Mode	0666
EndSection
So, what do you make of it?
Thanks,
Linuxnovice.

P.S: I tried xmastree's vesa driver suggestion. I couldnt get to GNOME after that. I had to load the backup and get in. WHAT IS WRONG WITH MY MACHINE?

Xmasstree gave me this link : [http://ubuntuforums.org/showthread.php?t=27029](http://ubuntuforums.org/showthread.php?t=27029)
The author of the thread, has asked me to run [http://ubuntuforums.org/showthread.php?t=27029](http://ubuntuforums.org/showthread.php?t=27029). This link seems to be broken. Here's what I get :
linuxfreak@ubuntu:~$ wget [http://ftp.psn.ru/debian/pool/main/8/855resolution/855resolution_0.3-4_i386.deb](http://ftp.psn.ru/debian/pool/main/8/855resolution/855resolution_0.3-4_i386.deb)
--20:17:41--  [http://ftp.psn.ru/debian/pool/main/8/855resolution/855resolution_0.3-4_i386.deb](http://ftp.psn.ru/debian/pool/main/8/855resolution/855resolution_0.3-4_i386.deb)
           => `855resolution_0.3-4_i386.deb'
Resolving ftp.psn.ru... 194.149.67.136
Connecting to ftp.psn.ru|194.149.67.136|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
20:17:47 ERROR 404: Not Found.

If you could come on msn, it would be so much more easier........sudarshan_gem@hotmail.com.

---

### Post by bscbrit on 2006-01-29
I'd like you to boot your computer in 'recovery mode'.  When you restart your computer you may get the GRUB menu, if not, it will give you a few seconds during which you can press the escape key and it will display the GRUB menu.

Select your normal kernel but with the option that is marked as 'Recovery mode'.  Watch the screen during the boot - which will not go in to fancy graphics but remain as text.  You are looking for the part when it tries to mount the various drives.  Try to identify which drive is causing the problem.

(There are other ways of doing this but they will take as long for me to explain than it will for you to do it - this method is dirty but much quicker :D )

Once you have the necessary information, you can reboot as usual and let me know what it says please.

---

### Post by linuxnovice on 2006-01-29
Well,
The thing was too fast but I have an idea where the '[COLOR="Red"]fail[/COLOR]' occured. It was while mounting /dev/hda1 (windows). Other mounting had ok beside it.
Linuxnovice.

Here is something really weird:
This is my /etc/fstab contents:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda6       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       /boot           ext3    defaults        0       2
/dev/hda1       /media/hda1     ntfs    defaults        0       0
/dev/hda7       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1       /media/windows  ntfs    nls=utf8,umask=0222 0       0
 
Now when I give sudo mount -a, I get this:
mount: mount point /media/windows does not exist.

What is the deal here???

---

### Post by bscbrit on 2006-01-29
OK, well the windows drive will NOT affect the booting of your Ubuntu so we can disregard it as a possible cause.


But there are 2 problems with your fstab:

You are trying to mount /dev/hda1 twice! Delete the line

/dev/hda1 /media/hda1 ntfs defaults 0 0


I think the second possible problem is that you are trying to mount it as read/write - which you cannot do for NTFS!

If you try the following options you might find the fault disappears: 

/dev/hda1 /media/windows ntfs ro,nls=utf8,umask=0222 0 0

But for the moment, I am at a loss what to suggest for your display problem.  I'm still thinking.....

---

### Post by linuxnovice on 2006-01-29
Well,
I did what you told me to. It hasnt solved the 'fail' thing at startup...but it has solved another problem that I had. Now I can easliy access my Windows NTFS partition :D. So my screen is bugging you uh? Should I go in for a reinstall?
Linuxnovice.

---

### Post by bscbrit on 2006-01-29
It sounds a bit defeatist - but I will confess as to having no further bright ideas.  If you do a re-install, at least I will have some thinking time _and_ the problem may go away. ;)

---

### Post by bscbrit on 2006-01-29
What is failing now?

---

### Post by linuxnovice on 2006-01-29
Well, 
The screen is still as it is. Other than that, everything else seems ok. But the screen is bothering me because I look directly into it! Besides, I am going to be working in Linux alot, and with this screen, it will be difficult. I do have one request. While I reinstall, what are the things that I have to look out for? And do I need to delete this linux partition thro windows, or will the Ubuntu CD take care of it? Finally, right now I have around 1.5GB for swap, 100MB for /boot and 10GB for /. Any changes to be done here? I have 1.2GB of RAM, so I think I dont need that much swap. Other than these, if you have any suggestions about what I have to do right after I reinstall, please let me know.
Thanks for all your help and am sorry for bugging you so much!
Linuxnovice.

---

### Post by bscbrit on 2006-01-29
The ubuntu install will let you manage your partitions - you can either use the ones that you already have or you can delete them and start again -DO NOT delete your window(s) partition.  No, of course you won't - but loads of people do and then come here asking how to fix them....:-D 

You do not need more than 512Mb for swap no matter how much RAM you actually have. That should save you a Gb or so!

And when you re-install you surely cannot be in any worse position regarding your screen - well you can, but I prefer not to think of such things.  As you say, you really do need to have a good display because you will spend so much time looking at it.

Regarding my question regarding 'What is failing' - I thought that you said you were still getting failure messages during boot up.  If they have gone away then OK.  I had remembered that your display was causing you problems.  :p

---

